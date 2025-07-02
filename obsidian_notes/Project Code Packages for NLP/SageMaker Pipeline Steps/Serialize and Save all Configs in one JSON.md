---
tags:
  - code
  - code_snippet
  - python/json
  - aws/sagemaker_pipeline
keywords: 
topics: 
language: python
date of note: 2025-05-23
---

## Code Snippet Summary

>[!important]
>This file includes several functions
>- `serialize_config`: 
>	- `model_dump` all fields in all configs in the list
>	- create `meta_data` field
>	- recursively serialize any datetime, Path, Enum, nested dict, or list; and save to dictionary
>- `merge_and_save_configs`
>	- merge a list of Configs and save to json
>	- the json has following fields
>		- `"shared"`
>			- fields that appear (with identical values) in two or more configs
>		- `"processing"`
>			- fields that belong to any ProcessingStepConfigBase subclass,
>		- `"specific"`
>			- all other fields, grouped by each unique step_name
>- `load_configs`
>	- load a list of Configs from JSON saved
>- `verify_configs`

## Rule for Field Categorization

>[!important]
> - Identify fields that appear in both processing and non-processing configs (cross-type fields)
> 
> - For these **cross-type fields**:
> 	- If the field is **static** *AND* has **identical values across ALL configs** (both processing and non-processing):
> 	    - Place it in the root "**shared**" section
> 
> 	- If values **differ between configs**:
> 	    - For *non-processing configs*: keep in "**specific**" section
> 	    - For *processing configs*: keep in "**processing_specific**" section
> 
> - For fields that are **exclusive** to only **processing configs**:
> 	- If **static** *and* **identical** across all processing configs: place in "**processing_shared**"
> 	- Otherwise: place in "**processing_specific**"
> 
> - For fields **exclusive** to **non-processing configs**:
> 	- If **static** *and* **identical** across multiple configs: place in "**shared**"
> 	- Otherwise: place in "**specific**"
>- The following categories are mutual exclusive
>	- "**specific**" and "**shared**"
>	-  "**processing_specific**" and "**processing_shared**"
>-  "**processing_specific**" and "**specific**" are grouped by step names


## Code

```python
from typing import List, Dict, Any, Type, Union
import json
from datetime import datetime
from pathlib import Path
from enum import Enum
from pydantic import BaseModel
```

### Base Config Type

```python
from .config_base import BasePipelineConfig
```

- [[Base Config]]
### Serialize all Attributes

```python
def serialize_config(config: BaseModel) -> Dict[str, Any]:
    """
    Serialize a single Pydantic config to a JSON‐serializable dict,
    embedding a metadata block that includes a unique 'step_name'.

    If the config has a 'job_type' attribute, we append that to the
    standard step name so that multiple CradleDataLoadConfig instances
    won't conflict.
    """
    # 1) Dump the model to a plain dict (handles nested submodels)
    config_dict = config.model_dump() if hasattr(config, "model_dump") else config.dict()

    # 2) Compute the base step name
    base_step = BasePipelineConfig.get_step_name(config.__class__.__name__)

    # 3) If this config has 'job_type', append it to make the step name unique
    if hasattr(config, "job_type"):
        job_type_val = getattr(config, "job_type").capitalize()
        # CamelCase‐style: e.g. "CradleDataLoadingStep_training" → "CradleDataLoadingStep_training"
        step_name = f"{base_step}_{job_type_val}"
    else:
        step_name = base_step

    # 4) Inject metadata
    config_dict["_metadata"] = {
        "step_name": step_name,
        "config_type": config.__class__.__name__,
    }

    # 5) Recursively serialize any datetime, Path, Enum, nested dict, or list
    def serialize_value(value: Any) -> Any:
        if isinstance(value, datetime):
            return value.isoformat()
        elif isinstance(value, Enum):
            return value.value
        elif isinstance(value, Path):
            return str(value)
        elif isinstance(value, dict):
            return {k: serialize_value(v) for k, v in value.items()}
        elif isinstance(value, list):
            return [serialize_value(item) for item in value]
        return value

    return {key: serialize_value(val) for key, val in config_dict.items()}
```

### Merge All Attributes in a list of Config in one JSON

```python
def merge_and_save_configs(config_list: List[BaseModel], output_file: str) -> Dict[str, Any]:
    """
    Merge multiple configs of potentially the same class (e.g. CradleDataLoadConfig for different job_types),
    then save them to a single JSON. Returns the "merged" structure (so you can inspect it if desired).

    We build three sections:
      - "shared": fields that appear (with identical values) in two or more configs
      - "processing": fields that belong to any ProcessingStepConfigBase subclass,
          grouped by each unique step_name
      - "specific": all other fields, grouped by each unique step_name

    Finally, under "metadata" → "config_types" we map each unique step_name → config class name.
    """
    merged_config: Dict[str, Dict[str, Any]] = {
        "shared": {},
        "processing": defaultdict(dict),
        "specific": defaultdict(dict),
    }

    # Track all encountered JSON‐stringified values for each field
    field_values: Dict[str, Set[str]] = defaultdict(set)
    # Track which step_names contributed to which field
    field_sources: Dict[str, Dict[str, List[str]]] = defaultdict(lambda: defaultdict(list))

    # 1) First pass: collect field‐values and where they came from
    for config in config_list:
        config_dict = serialize_config(config)
        step_name = config_dict["_metadata"]["step_name"]

        # All valid top‐level fields for this Pydantic class
        valid_fields = set(config.__class__.model_fields.keys())

        for key, val in config_dict.items():
            if key == "_metadata" or key not in valid_fields:
                continue

            # JSON‐serialize the candidate value (stable sort_keys)
            json_text = json.dumps(val, sort_keys=True)
            field_values[key].add(json_text)
            field_sources["all"][key].append(step_name)

            # If this config is a ProcessingStepConfigBase, mark accordingly
            if isinstance(config, ProcessingStepConfigBase):
                if key in ProcessingStepConfigBase.model_fields:
                    field_sources["processing"][key].append(step_name)
                else:
                    field_sources["specific"][key].append(step_name)
            else:
                field_sources["specific"][key].append(step_name)

    # 2) Second pass: divide into shared vs. processing vs. specific
    for key, jsons in field_values.items():
        # If exactly one unique JSON value but used by multiple step_names → shared
        if len(jsons) == 1 and len(field_sources["all"][key]) > 1:
            merged_config["shared"][key] = json.loads(next(iter(jsons)))
        # Otherwise, if this key ever appeared under ProcessingStepConfigBase, put under "processing"
        elif key in field_sources["processing"]:
            for config in config_list:
                if isinstance(config, ProcessingStepConfigBase):
                    config_dict = serialize_config(config)
                    step_name = config_dict["_metadata"]["step_name"]
                    if key in config_dict and key in config.__class__.model_fields:
                        merged_config["processing"][step_name][key] = config_dict[key]
        # Finally, any leftover goes under "specific"
        else:
            for config in config_list:
                config_dict = serialize_config(config)
                step_name = config_dict["_metadata"]["step_name"]
                if key in config_dict and key in config.__class__.model_fields:
                    merged_config["specific"][step_name][key] = config_dict[key]

    # 3) metadata.section: record exact timestamp & field_sources & config_types
    metadata = {
        "created_at": datetime.now().isoformat(),
        "field_sources": field_sources,
        # Instead of class_name → step_name, we do step_name → class_name (allows duplicates of same class)
        "config_types": {
            serialize_config(cfg)["_metadata"]["step_name"]: cfg.__class__.__name__
            for cfg in config_list
        },
    }

    output_data = {"metadata": metadata, "configuration": merged_config}

    with open(output_file, "w") as f:
        json.dump(output_data, f, indent=2, sort_keys=True)

    return merged_config
```


### Load JSON and Reconstruct Configs

```python
def load_configs(input_file: str, config_classes: Dict[str, Type[BaseModel]]) -> Dict[str, BaseModel]:
    """Load configurations from JSON file"""
    with open(input_file, 'r') as f:
        data = json.load(f)

    metadata = data["metadata"]
    config_data = data["configuration"]
    config_types = metadata["config_types"]
    field_sources = metadata["field_sources"]

    configs = {}
    for config_name, step_name in config_types.items():
        if config_name not in config_classes:
            raise ValueError(f"Unknown config type: {config_name}")

        config_class = config_classes[config_name]
        
        # Get the fields that are valid for this config class
        valid_fields = set(config_class.model_fields.keys())
        
        # Combine fields for this config
        fields = {}
        
        # Add shared fields (only if they're valid for this config)
        for key, value in config_data["shared"].items():
            if key in valid_fields:
                fields[key] = value
        
        # Add processing-specific fields if applicable
        if issubclass(config_class, ProcessingStepConfigBase):
            if step_name in config_data["processing"]:
                processing_fields = config_data["processing"][step_name]
                fields.update({
                    k: v for k, v in processing_fields.items()
                    if k in valid_fields
                })
        
        # Add config-specific fields
        if step_name in config_data["specific"]:
            specific_fields = config_data["specific"][step_name]
            fields.update({
                k: v for k, v in specific_fields.items()
                if k in valid_fields
            })

        try:
            configs[step_name] = config_class(**fields)
        except Exception as e:
            print(f"Error creating {step_name} config: {str(e)}")
            print(f"Attempted to create with fields: {fields}")
            print(f"Valid fields for {config_name}: {valid_fields}")
            raise

    return configs

```


### Verify the List of Configs

```python
def verify_configs(
    original_configs: List[BaseModel],
    loaded_configs: Dict[str, BaseModel]
) -> bool:
    """Verify that loaded configs match the originals"""
    all_match = True
    
    for original in original_configs:
        step_name = BasePipelineConfig.get_step_name(original.__class__.__name__)
        print(f"\nVerifying {step_name}:")
        
        if step_name not in loaded_configs:
            print(f"⚠ No loaded config found for {step_name}")
            all_match = False
            continue

        loaded_config = loaded_configs[step_name]
        
        # Compare serialized versions
        original_dict = serialize_config(original)
        loaded_dict = serialize_config(loaded_config)
        
        # Remove metadata for comparison
        original_dict.pop('_metadata', None)
        loaded_dict.pop('_metadata', None)
        
        if original_dict == loaded_dict:
            print(f"✓ Configuration matches original for {step_name}")
        else:
            print(f"⚠ Configuration differs for {step_name}")
            diffs = {
                k: (original_dict.get(k), loaded_dict.get(k))
                for k in set(original_dict) | set(loaded_dict)
                if original_dict.get(k) != loaded_dict.get(k)
            }
            print("Differences:", diffs)
            all_match = False

    return all_match
```


## Save all Configs

```python
# Usage example:
if __name__ == "__main__":
    CONFIG_CLASSES = {
        'BasePipelineConfig': BasePipelineConfig,
        'TrainingConfig': TrainingConfig,
        'ModelCreationConfig': ModelCreationConfig,
        'ProcessingStepConfigBase': ProcessingStepConfigBase,
        'PackageStepConfig': PackageStepConfig,
        'ModelRegistrationConfig': ModelRegistrationConfig
    }

    # Save configs
    config_list = [base_config, train_config, model_config, 
                  processing_config, package_config, registration_config]
    merge_and_save_configs(config_list, 'configs.json')

    # Load configs
    loaded_configs = load_configs('configs.json', CONFIG_CLASSES)

    # Access configs by step name
    base_config = loaded_configs['Base']
    training_config = loaded_configs['Training']
    model_config = loaded_configs['Model']
    processing_config = loaded_configs['Processing']
    package_config = loaded_configs['Package']
    registration_config = loaded_configs['Registration']

    print("\nLoaded configurations:")
    for step_name, config in loaded_configs.items():
        print(f"{step_name}: {type(config).__name__}")

```


- [[Config for Pytorch Training Step]]
- [[Config for Pytorch Model Step]]
- [[Hyperparameter for Pytorch Training Step]]
- [[Config for Packaging Step]]
- [[Config for Payload Generation Step]]
- [[Config for Model Registration Step]]





-----------
##  Recommended Notes

