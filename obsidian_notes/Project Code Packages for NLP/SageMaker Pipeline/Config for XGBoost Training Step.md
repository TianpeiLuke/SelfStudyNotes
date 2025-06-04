---
tags:
  - code
  - code_snippet
  - aws/sagemaker_pipeline
  - python/pydantic
keywords: 
topics: 
language: python
date of note: 2025-06-03
---

## Code Snippet Summary

>[!important]


- [[Builder XGBoost Training Step]]
## Code

```python
from pydantic import BaseModel, Field, model_validator, field_validator
from typing import List, Optional, Dict, Any
from pathlib import Path
import json
from datetime import datetime
```

### Base Config and Hyperparameters

```python
from .hyperparameters_xgboost import XGBoostModelHyperparameters
from .config_base import BasePipelineConfig
```

- [[Base Config]]
- [[Hyperparameter for XGBoost Training Step]]

### XGBoost Training Config

```python
class XGBoostTrainingConfig(BasePipelineConfig):
    """
    Configuration specific to the SageMaker XGBoost Training Step.
    This assumes script mode for XGBoost to align with the builder's design.
    If using built-in XGBoost without a script, entry_point/source_dir would be optional.
    """
    # S3 paths with updated pattern
    input_path: str = Field(
        description="S3 path for input training data (e.g., train and validation channels).",
        pattern=r'^s3://[a-zA-Z0-9.-]+(?:/[a-zA-Z0-9._-]+)*$' # Simplified pattern a bit
    )
    output_path: str = Field(
        description="S3 path for output data (model artifacts, etc.).",
        pattern=r'^s3://[a-zA-Z0-9.-]+(?:/[a-zA-Z0-9._-]+)*$'
    )
    checkpoint_path: Optional[str] = Field(
        default=None,
        description="Optional S3 path for model checkpoints.",
        pattern=r'^s3://[a-zA-Z0-9.-]+(?:/[a-zA-Z0-9._-]+)*$'
    )

    # Instance configuration
    training_instance_type: str = Field(default='ml.m5.xlarge', description="Instance type for XGBoost training job.")
    training_instance_count: int = Field(default=1, ge=1, description="Number of instances for XGBoost training job.")
    training_volume_size: int = Field(default=30, ge=1, description="Volume size (GB) for training instances.")

    # Script mode configuration (if not using built-in algorithm directly)
    training_entry_point: str = Field(default='train_xgb.py', description="Entry point script for XGBoost training.")
    # source_dir is inherited from BasePipelineConfig, should contain training_entry_point

    # Framework versions for SageMaker XGBoost container
    framework_version: str = Field(default="1.7-1", description="SageMaker XGBoost framework version (e.g., '1.7-1', '1.5-1').")
    py_version: str = Field(default="py3", description="Python version for the SageMaker XGBoost container.")


    # XGBoost specific hyperparameters
    hyperparameters: XGBoostModelHyperparameters # Use the specific XGBoost hyperparameter class

    class Config(BasePipelineConfig.Config): # Inherit base config settings
        pass

    @model_validator(mode='before')
    @classmethod
    def _construct_training_paths(cls, values: Dict[str, Any]) -> Dict[str, Any]:
        """Constructs S3 paths specific to training if not provided."""
        # Call base validator to ensure bucket, current_date etc. are there
        values = super()._construct_base_attributes(values) # Explicitly call if not guaranteed by Pydantic order

        bucket = values.get('bucket')
        current_date = values.get('current_date')
        pipeline_name = values.get('pipeline_name', 'DefaultPipeline')


        if not values.get('input_path'):
            values['input_path'] = f"s3://{bucket}/{pipeline_name}/training_input/{current_date}"
        if not values.get('output_path'):
            values['output_path'] = f"s3://{bucket}/{pipeline_name}/training_output/{current_date}/model"
        if 'checkpoint_path' not in values: # Allow explicit None to disable default path construction
             values['checkpoint_path'] = f"s3://{bucket}/{pipeline_name}/training_checkpoints/{current_date}"
        return values

    @model_validator(mode='after')
    def _validate_training_paths_logic(self) -> 'XGBoostTrainingConfig':
        """Validates S3 path requirements for training."""
        paths_to_check: Dict[str, Optional[str]] = {
            'input_path': self.input_path,
            'output_path': self.output_path
        }
        if self.checkpoint_path: # Only add if it's not None
            paths_to_check['checkpoint_path'] = self.checkpoint_path

        # Filter out None paths before checking for uniqueness
        defined_paths = {k: v for k, v in paths_to_check.items() if v is not None}

        if len(set(defined_paths.values())) != len(defined_paths):
            # Identify which paths are duplicated for a clearer error message
            from collections import Counter
            path_counts = Counter(defined_paths.values())
            duplicates = {path: count for path, count in path_counts.items() if count > 1}
            raise ValueError(f"All defined paths (input, output, checkpoint) must be unique. Duplicates found: {duplicates}")
            
        min_depth = 2 # S3 bucket + at least one prefix level
        for path_name, path_value in defined_paths.items():
            if path_value: # Should always be true due to filter, but defensive
                # s3://bucket/prefix1/prefix2 -> ['bucket', 'prefix1', 'prefix2'] -> length 3
                depth = len(path_value.replace("s3://", "").split('/'))
                if depth < min_depth:
                    raise ValueError(
                        f"{path_name} ('{path_value}') must have at least {min_depth} levels of hierarchy (bucket + prefix)."
                    )
        return self

    @model_validator(mode='after')
    def validate_hyperparameter_fields(self) -> 'XGBoostTrainingConfig':
        """
        Validate field lists from hyperparameters if they are used by the XGBoost script.
        This is inherited from the PyTorch example; its relevance depends on your XGBoost script.
        """
        if not self.hyperparameters:
            # This should not happen if the field is non-optional, but good check.
            raise ValueError("XGBoost hyperparameters must be provided.")

        # The following checks are from your PyTorch example.
        # They assume your XGBoost script or data prep relies on these fields
        # from the ModelHyperparameters base. If not, these can be removed or adjusted.
        all_fields = set(self.hyperparameters.full_field_list)
        if not set(self.hyperparameters.tab_field_list).issubset(all_fields):
            raise ValueError("All fields in tab_field_list must be in full_field_list (from hyperparameters).")
        if not set(self.hyperparameters.cat_field_list).issubset(all_fields):
            raise ValueError("All fields in cat_field_list must be in full_field_list (from hyperparameters).")
        
        if self.hyperparameters.label_name not in all_fields:
            raise ValueError(f"label_name '{self.hyperparameters.label_name}' must be in full_field_list (from hyperparameters).")
        # id_name might not always be required for training itself, but for data prep.
        if self.hyperparameters.id_name not in all_fields:
            raise ValueError(f"id_name '{self.hyperparameters.id_name}' must be in full_field_list (from hyperparameters).")

        return self
    
    @field_validator('training_instance_type')
    @classmethod
    def _validate_sagemaker_xgboost_instance_type(cls, v: str) -> str:
        # Common CPU instances for XGBoost. XGBoost can also use GPU instances (e.g., ml.g4dn, ml.g5)
        # if tree_method='gpu_hist' is used and framework supports it.
        valid_cpu_instances = [
            "ml.m5.large", "ml.m5.xlarge", "ml.m5.2xlarge", "ml.m5.4xlarge",
            "ml.m5.12xlarge", "ml.m5.24xlarge",
            "ml.c5.large", "ml.c5.xlarge", "ml.c5.2xlarge", "ml.c5.4xlarge",
            "ml.c5.9xlarge", "ml.c5.18xlarge",
        ]
        valid_gpu_instances = [ # For GPU accelerated XGBoost
            "ml.g4dn.xlarge", "ml.g4dn.2xlarge", "ml.g4dn.4xlarge", 
            "ml.g4dn.8xlarge", "ml.g4dn.12xlarge", "ml.g4dn.16xlarge",
            "ml.g5.xlarge", "ml.g5.2xlarge", "ml.g5.4xlarge",
            "ml.g5.8xlarge", "ml.g5.12xlarge", "ml.g5.16xlarge",
             "ml.p3.2xlarge" # Older but sometimes used
        ]
        valid_instances = valid_cpu_instances + valid_gpu_instances
        if v not in valid_instances:
            raise ValueError(
                f"Invalid training instance type for XGBoost: {v}. "
                f"Must be one of: {', '.join(valid_instances)}"
            )
        return v

    def get_checkpoint_uri(self) -> Optional[str]:
        """Returns the S3 URI for checkpoints."""
        return self.checkpoint_path

    def has_checkpoint(self) -> bool:
        """Checks if a checkpoint path is configured."""
        return self.checkpoint_path is not None
```


- [[XGBoost and LightGBM]]


-----------
##  Recommended Notes


- [[Config for Pytorch Training Step]]