---
tags:
  - code
  - code_snippet
  - python/pydantic
keywords: 
topics: 
language: python
date of note: 2025-05-22
---

## Code Snippet Summary

>[!important]
>Base Config Class
>- Based on `Pydantic` version 2
>- Define common shared attributes
>	- `bucket`
>	- `current_date`
>	- `region`
>	- `aws_region`
>	- `author`
>	- `pipeline_name`
>	- `pipeline_description`
>	- `pipeline_version`
>	- `pipeline_s3_loc`
>	- `framework_version`
>	- `py_version`
>	- `source_dir`


## Code

```python
from pydantic import BaseModel, Field, model_validator, field_validator
from typing import List, Optional, Dict, Any
from pathlib import Path
import json
from datetime import datetime
```


### Base Config

```python
class BasePipelineConfig(BaseModel):
    """Base configuration with shared pipeline attributes."""
    # Shared basic info
    bucket: str = Field(description="S3 bucket name for pipeline artifacts and data.")
    current_date: str = Field(
        default_factory=lambda: datetime.now().strftime("%Y-%m-%d"),
        description="Current date, typically used for versioning or pathing."
    )
    region: str = Field(default='NA', description="Custom region code (NA, EU, FE) for internal logic.")
    aws_region: Optional[str] = Field(default=None, description="Derived AWS region (e.g., us-east-1).")
    author: str = Field(description="Author or owner of the pipeline.")

    # Overall pipeline identification
    pipeline_name: str = Field(description="Name of the SageMaker Pipeline.")
    pipeline_description: str = Field(description="Description for the SageMaker Pipeline.")
    pipeline_version: str = Field(description="Version string for the SageMaker Pipeline.")
    pipeline_s3_loc: str = Field(
        description="Root S3 location for storing pipeline definition and step artifacts.",
        pattern=r'^s3://[a-zA-Z0-9.-][a-zA-Z0-9.-]*(?:/[a-zA-Z0-9.-][a-zA-Z0-9._-]*)*$'
    )

    # Common framework/scripting info (if shared across steps like train/inference)
    framework_version: str = Field(default='2.1.0', description="Default framework version (e.g., PyTorch).")
    py_version: str = Field(default='py310', description="Default Python version.")
    # General source_dir, specific entry points will be in step configs
    source_dir: Optional[str] = Field(default=None, description="Common source directory for scripts if applicable. Can be overridden by step configs.")


    class Config:
        arbitrary_types_allowed = True
        validate_assignment = True
        # extra = 'forbid' # Or 'allow' / 'ignore' as per your preference
        protected_namespaces = ()

    @model_validator(mode='before')
    @classmethod
    def _construct_base_attributes(cls, values: Dict[str, Any]) -> Dict[str, Any]:
        """
        Sets up default values for core attributes if not provided,
        often using external context like a session object (mocked here).
        """
        # Resolve bucket and author using sais_session if not provided
        # In real usage, sais_session might be passed differently or be a global
        if 'bucket' not in values or values['bucket'] is None:
            values['bucket'] = sais_session.team_owned_s3_bucket_name()
        if 'author' not in values or values['author'] is None:
            values['author'] = sais_session.owner_alias()

        # Ensure current_date is set
        if 'current_date' not in values or values['current_date'] is None:
            values['current_date'] = datetime.now().strftime("%Y-%m-%d")
        
        # Derive aws_region from custom region code
        region_code = values.get('region', 'NA') # Default to 'NA' if not present
        values['region'] = region_code # Ensure region code is in values

        region_mapping = {"NA": "us-east-1", "EU": "eu-west-1", "FE": "us-west-2"}
        if 'aws_region' not in values or values['aws_region'] is None:
            values['aws_region'] = region_mapping.get(region_code, "us-east-1") # Default if mapping fails

        # Construct pipeline name if not provided
        pipeline_name = values.get('pipeline_name')
        if not pipeline_name:
            pipeline_name = f'{author}-BSM-RnR-{region}'
            values['pipeline_name'] = pipeline_name

        # Construct pipeline description if not provided
        if not values.get('pipeline_description'):
            values['pipeline_description'] = f'BSM RnR {region}'

        # Set default pipeline version if not provided
        pipeline_version = values.get('pipeline_version')
        if not pipeline_version:
            pipeline_version = '0.1.0'
            values['pipeline_version'] = pipeline_version

        # Construct pipeline S3 location if not provided
        if not values.get('pipeline_s3_loc'):
            pipeline_subdirectory = 'MODS'  # You might want to make this configurable
            pipeline_subsubdirectory = f"{pipeline_name}_{pipeline_version}"
            values['pipeline_s3_loc'] = f"s3://{Path(bucket) / pipeline_subdirectory / pipeline_subsubdirectory}"
        
        return values

    @field_validator('region')
    @classmethod
    def _validate_custom_region(cls, v: str) -> str:
        valid_regions = ['NA', 'EU', 'FE']
        if v not in valid_regions:
            raise ValueError(f"Invalid custom region code: {v}. Must be one of {valid_regions}")
        return v

    @field_validator('source_dir', check_fields=False) # check_fields=False if source_dir can be None
    @classmethod
    def _validate_source_dir_exists(cls, v: Optional[str]) -> Optional[str]:
        if v is not None and not v.startswith('s3://'): # Only validate local paths
            if not Path(v).exists():
                raise ValueError(f"Local source directory does not exist: {v}")
            if not Path(v).is_dir():
                raise ValueError(f"Local source_dir is not a directory: {v}")
        return v
    
```

- [[Data Class with Pydantic]]
- [[Simple Data Class from Pydantic]]


### Save Config to JSON

```python
def save_config_to_json(
    model_config: ModelConfig, 
    hyperparams: ModelHyperparameters, 
    config_path: str = "config/config.json"
) -> Path:
    """
    Save ModelConfig and ModelHyperparameters to JSON file
    
    Args:
        model_config: ModelConfig instance
        hyperparams: ModelHyperparameters instance
        config_path: Path to save the config file
    
    Returns:
        Path object of the saved config file
    """
    try:
        # Convert both models to dictionaries
        config_dict = model_config.model_dump()
        hyperparams_dict = hyperparams.model_dump()
        
        # Combine both dictionaries
        combined_config = {**config_dict, **hyperparams_dict}
        
        # Create config directory if it doesn't exist
        path = Path(config_path)
        path.parent.mkdir(parents=True, exist_ok=True)
        
        # Save to JSON file
        with open(path, 'w') as f:
            json.dump(combined_config, f, indent=2, sort_keys=True)
            
        print(f"Configuration saved to: {path}")
        return path
        
    except Exception as e:
        raise ValueError(f"Failed to save config: {str(e)}")
```


## Derived Classes

- [[Config for Training Step]]
- [[Config for Model Step]]
- [[Base Config for Processing Step]]


-----------
##  Recommended Notes

- [[Base Step Builder]]
