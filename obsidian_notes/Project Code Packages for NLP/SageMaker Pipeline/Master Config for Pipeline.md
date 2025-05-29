---
tags:
  - code
  - code_snippet
  - python/pydantic
keywords: 
topics: 
language: python
date of note: 2025-05-20
---

## Code Snippet Summary

>[!important]
>Create Config Class for Model Training Step
>- Based on `Pydantic` version 2
>- Used to define `PyTorchTrainingStepBuilder`


- [[Config for Training Step]]
- [[Config for Model Step]]
- [[Hyperparameter for Training Step]]
- [[Config for Packaging Step]]
- [[Config for Payload Generation Step]]
- [[Config for Model Registration Step]]

## Code

```python
from pydantic import BaseModel, Field, model_validator, field_validator
from typing import List, Optional, Dict, Any
from pathlib import Path
import json
from datetime import datetime
```


```python
class ModelConfig(BaseModel):
    """Primary model configuration"""
    # Required fields from config
    bucket: str = Field(description="S3 bucket name")
    current_date: str = Field(
        default_factory=lambda: datetime.now().strftime("%Y-%m-%d"),
        description="Current date in YYYY-MM-DD format")
    region: str = Field(default='NA', description="region (NA, EU, FE)")
    aws_region: Optional[str] = Field(default=None, description="AWS region based on model registration region")

    # S3 paths with updated pattern
    input_path: str = Field(
        description="S3 path for input data",
        pattern=r'^s3://[a-zA-Z0-9.-][a-zA-Z0-9.-]*(?:/[a-zA-Z0-9.-][a-zA-Z0-9._-]*)*$'
    )
    output_path: str = Field(
        description="S3 path for output data",
        pattern=r'^s3://[a-zA-Z0-9.-][a-zA-Z0-9.-]*(?:/[a-zA-Z0-9.-][a-zA-Z0-9._-]*)*$'
    )
    checkpoint_path: Optional[str] = Field(
        default=None,
        description="Optional S3 path for model checkpoints",
        pattern=r'^s3://[a-zA-Z0-9.-][a-zA-Z0-9.-]*(?:/[a-zA-Z0-9.-][a-zA-Z0-9._-]*)*$'
    )
    
    # Pipeline Config
    author: str = Field(description="Author of the pipeline")
    pipeline_name: str = Field(description="Name of the pipeline")
    pipeline_description: str = Field(description="Description of the pipeline")
    pipeline_version: str = Field(description="Version of the pipeline")
    pipeline_s3_loc: str = Field(
        description="S3 location for pipeline artifacts",
        pattern=r'^s3://[a-zA-Z0-9.-][a-zA-Z0-9.-]*(?:/[a-zA-Z0-9.-][a-zA-Z0-9._-]*)*$'
    )

    # Training Configuration
    instance_type: str = Field(default='ml.g5.12xlarge', description="Instance type for training")
    framework_version: str = Field(default='2.1.0', description="Framework version")
    py_version: str = Field(default='py310', description="Python version")
    volume_size: int = Field(default=500, ge=10, le=1000, description="Volume size in GB")
    entry_point: str = Field(default='train.py', description="Entry point for training script")
    source_dir: str = Field(default=None, description="Source directory for training script")
    instance_count: int = Field(default=1)
    
    # Endpoint Configuration
    inference_instance_type: str = Field(default='ml.m5.4xlarge', description="Instance type for inference")
    inference_entry_point: str = Field(default='inference.py',  description="Entry point for inference script")
    initial_instance_count: int = Field(default=1, ge=1, le=10, description="Initial instance count for inference")
    
    container_startup_health_check_timeout: int = Field(default=300, ge=0, le=3600, description="Timeout for container startup health check")
    container_memory_limit: int = Field(default=6144, ge=1024, le=61440, description="Memory limit for the container in MB")
    data_download_timeout: int = Field(default=900, ge=0, le=3600, description="Timeout for data download in seconds")
    inference_memory_limit: int = Field(default=6144, ge=1024, le=61440, description="Memory limit for inference in MB")
    max_concurrent_invocations: int = Field(default=1, ge=1, le=10, description="Max concurrent invocations for the endpoint")
    
    
    # Model Registration Configuration
    model_owner: str = Field(default="amzn1.abacus.team.djmdvixm5abr3p75c5ca", description="Team ID of abuse-analytics")
    model_registration_domain: str = Field(default="BuyerSellerMessaging", description="Domain of model registry")
    model_registration_objective: Optional[str] = Field(default=None, description="Objective of model registry")
    
    
    # Payload Test
    payload_script_path: str = Field(default=None, description="Path to the payload creation script (relative to notebook_root or S3 URI)") # payload test script
    payload_script_arguments: Optional[List[str]] = Field(default=None, description="Optional arguments for the payload creation script") # payload test argument
    expected_tps: int = Field(default=2, description="Expected transactions per second")
    max_latency_in_millisecond: int = Field(default=800, description="Maximum latency in milliseconds")
    max_acceptable_error_rate: float = Field(default=0.2, description="Maximum acceptable error rate")
    max_payload_size: int = Field(default=6, ge=1, le=6, description="Max payload size for the endpoint in MB")
    sample_payload_s3_key: str = Field(
        default="",
        description="S3 key for the sample payload file"
    )
    model_var_list: List[str] = Field(default_factory=list, description="List of model variables")

    source_model_inference_output_variable_list: Dict[str, str] = Field(
        default={
            'legacy-score': 'NUMERIC'
        },
        description="Source model inference output variable list"
    )
    source_model_inference_input_variable_list: Dict[str, str] = Field(
        default_factory=dict,
        description="Dictionary of input variables and their types"
    )
    source_model_inference_content_types: List[str] = Field(
        default=["text/csv"],
        description="Allowed content types for model inference input"
    )
    source_model_inference_response_types: List[str] = Field(
        default=["application/json"],
        description="Allowed response types for model inference output"
    )


    # Processing Step Configuration
    processing_instance_type_large: str = Field(default='ml.m5.4xlarge', description="Instance type for large processing jobs")
    processing_instance_type_small: str = Field(default='ml.m5.2xlarge', description="Instance type for small processing jobs")
    processing_instance_count: int = Field(default=1, ge=1, le=10, description="Instance count for processing jobs")
    processing_volume_size: int = Field(default=500, ge=10, le=1000, description="Volume size for processing jobs in GB")

    # Add reference to hyperparameters
    hyperparameters: Optional[ModelHyperparameters] = Field(None, description="Model hyperparameters")

    class Config:
        arbitrary_types_allowed = True
        validate_assignment = True
        extra = 'forbid'
        protected_namespaces = ()
    
    
    @model_validator(mode='before')
    @classmethod
    def construct_paths(cls, values: dict) -> dict:
        """Construct S3 paths before validation"""
        bucket = values.get('bucket', sais_session.team_owned_s3_bucket_name())

        current_date = values.get('current_date', datetime.now().strftime("%Y-%m-%d"))
        region = values.get('region', 'NA')
        author = values.get('author', sais_session.owner_alias())
        region_mapping = {
            'NA': "us-east-1",
            'EU': "eu-west-1",
            'FE': "us-west-2"
        }
        if 'aws_region' not in values:
            values['aws_region'] = region_mapping[region]

        # Construct paths if not provided
        if not values.get('input_path'):
            values['input_path'] = f"s3://{bucket}/train_test_val/{current_date}"
        
        if not values.get('output_path'):
            values['output_path'] = f"s3://{bucket}/models/{current_date}"
        
        if not values.get('checkpoint_path'):
            values['checkpoint_path'] = f"s3://{bucket}/checkpointing/{current_date}"

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
            
        # Construct sample payload S3 key
        model_objective= f'RnR_BSM_Model_{region}'
        payload_file_name = f'payload_{pipeline_name}_{pipeline_version}_{model_objective}'
        values['sample_payload_s3_key'] = f'mods/payload/{payload_file_name}.tar.gz'
        
        return values

    
    @model_validator(mode='after')
    def validate_paths(self) -> 'ModelConfig':
        """Validate all path relationships and requirements"""
        paths = {
            'input_path': self.input_path,
            'output_path': self.output_path
        }
        if self.checkpoint_path:
            paths['checkpoint_path'] = self.checkpoint_path

        # Check for uniqueness
        if len(set(paths.values())) != len(paths):
            raise ValueError("All paths (input, output, checkpoint) must be different")

        # Validate minimum path depths
        min_depth = 2
        for path_name, path in paths.items():
            depth = len(path.split('/')[3:])
            if depth < min_depth:
                raise ValueError(f"{path_name} must have at least {min_depth} levels of hierarchy")

        return self

    
    @model_validator(mode='after')
    def validate_field_lists(self) -> 'ModelConfig':
        """Validate field lists from hyperparameters"""
        if not self.hyperparameters:
            raise ValueError("hyperparameters must be provided")

        # Check if all fields in tab_field_list and cat_field_list are in full_field_list
        all_fields = set(self.hyperparameters.full_field_list)
        if not set(self.hyperparameters.tab_field_list).issubset(all_fields):
            raise ValueError("All fields in tab_field_list must be in full_field_list")
        if not set(self.hyperparameters.cat_field_list).issubset(all_fields):
            raise ValueError("All fields in cat_field_list must be in full_field_list")
        
        # Check if label_name and id_name are in full_field_list
        if self.hyperparameters.label_name not in all_fields:
            raise ValueError(f"label_name '{self.hyperparameters.label_name}' must be in full_field_list")
        if self.hyperparameters.id_name not in all_fields:
            raise ValueError(f"id_name '{self.hyperparameters.id_name}' must be in full_field_list")

        return self

    

    def get_checkpoint_uri(self) -> Optional[str]:
        """Returns the checkpoint URI if it exists"""
        return self.checkpoint_path

    def has_checkpoint(self) -> bool:
        """Returns whether a checkpoint path is configured"""
        return self.checkpoint_path is not None

    
    @field_validator('source_dir')
    @classmethod
    def validate_source_dir(cls, v: str) -> str:
        if not Path(v).exists():
            raise ValueError(f"Source directory does not exist: {v}")
        return v


    @field_validator('instance_type')
    @classmethod
    def validate_instance_type(cls, v: str) -> str:
        valid_instances = [
            "ml.g4dn.16xlarge", 
            "ml.g5.12xlarge", 
            "ml.g5.16xlarge",
            "ml.p3.8xlarge", 
            "ml.m5.12xlarge",
            "ml.p3.16xlarge"
        ]
        if v not in valid_instances:
            raise ValueError(
                f"Invalid training instance type: {v}. "
                f"Must be one of: {', '.join(valid_instances)}"
            )
        return v

    @field_validator('inference_memory_limit')
    @classmethod
    def validate_memory_limits(cls, v: int, info) -> int:
        container_memory_limit = info.data.get('container_memory_limit')
        if container_memory_limit and v > container_memory_limit:
            raise ValueError("Inference memory limit cannot exceed container memory limit")
        return v
    
    @field_validator('region')
    @classmethod
    def validate_region(cls, v: str) -> str:
        valid_regions = ['NA', 'EU', 'FE']
        if v not in valid_regions:
            raise ValueError(f"Invalid region: {v}. Must be one of {valid_regions}")
        return v

    @field_validator('max_acceptable_error_rate')
    @classmethod
    def validate_max_acceptable_error_rate(cls, v: float) -> float:
        if not 0 <= v <= 1:
            raise ValueError(f"max_acceptable_error_rate must be between 0 and 1, got {v}")
        return v

    @field_validator('source_model_inference_content_types', 'source_model_inference_response_types')
    @classmethod
    def validate_types(cls, v):
        allowed_types = {"text/csv", "application/json"}
        if not set(v).issubset(allowed_types):
            raise ValueError(f"Only 'text/csv' and 'application/json' are allowed. Got: {v}")
        return v
```


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

- [[Hyperparameter for Training Step]]
- [[Data Class with Pydantic]]
- [[Simple Data Class from Pydantic]]
- [[Pytorch Estimator Training for RnR BSM]]



-----------
##  Recommended Notes


- [[Pytorch Estimator Inference for RnR BSM]]
- [[Batch Transform using Endpoint from SageMaker]]
- [[RnR JUMIC URES Pipeline Production]]