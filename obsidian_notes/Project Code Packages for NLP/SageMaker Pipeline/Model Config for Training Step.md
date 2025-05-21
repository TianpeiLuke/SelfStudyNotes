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


- [[Builder Training Step]]

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
    pipeline_name: str = Field(default='pipeline', description="Pipeline name")

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

    # Rest of the configurations...
    instance_type: str = Field(default='ml.g5.12xlarge', description="Instance type for training")
    framework_version: str = Field(default='2.1.0', description="Framework version")
    py_version: str = Field(default='py310', description="Python version")
    volume_size: int = Field(default=500, ge=10, le=1000, description="Volume size in GB")
    entry_point: str = Field(default='train.py', description="Entry point for training script")
    source_dir: str = Field(default=None, description="Source directory for training script")
    instance_count: int = Field(default=1)
    
    inference_instance_type: str = Field(default='ml.m5.4xlarge', description="Instance type for inference")
    inference_entry_point: str = Field(default='inference.py',  description="Entry point for inference script")
    initial_instance_count: int = Field(default=1, ge=1, le=10, description="Initial instance count for inference")

    endpoint_name_prefix: Optional[str] = Field(
        default=None,
        description="Prefix for the endpoint name. If None, a random name will be generated."
    )
    tags: Optional[List[Dict[str, str]]] = Field(
        default=None,
        description="List of tags to apply to the SageMaker resources"
    )

    container_startup_health_check_timeout: int = Field(default=300, ge=0, le=3600, description="Timeout for container startup health check")
    container_memory_limit: int = Field(default=6144, ge=1024, le=61440, description="Memory limit for the container in MB")
    data_download_timeout: int = Field(default=900, ge=0, le=3600, description="Timeout for data download in seconds")
    inference_memory_limit: int = Field(default=6144, ge=1024, le=61440, description="Memory limit for inference in MB")
    max_concurrent_invocations: int = Field(default=1, ge=1, le=10, description="Max concurrent invocations for the endpoint")
    max_payload_size: int = Field(default=6, ge=1, le=6, description="Max payload size for the endpoint in MB")
    
    processing_instance_type: str = Field(default='ml.m5.4xlarge', description="Instance type for processing jobs")
    processing_instance_count: int = Field(default=1, ge=1, le=10, description="Instance count for processing jobs")
    processing_volume_size: int = Field(default=500, ge=10, le=1000, description="Volume size for processing jobs in GB")


    class Config:
        arbitrary_types_allowed = True
        validate_assignment = True
        extra = 'forbid'
        protected_namespaces = ()
    
    
    @model_validator(mode='before')
    @classmethod
    def construct_paths(cls, values: dict) -> dict:
        """Construct S3 paths before validation"""
        bucket = values.get('bucket')
        if not bucket:
            raise ValueError("Bucket name is required")

        current_date = values.get('current_date', datetime.now().strftime("%Y-%m-%d"))

        # Construct paths if not provided
        if not values.get('input_path'):
            values['input_path'] = f"s3://{bucket}/train_test_val/{current_date}"
        
        if not values.get('output_path'):
            values['output_path'] = f"s3://{bucket}/models/{current_date}"
        
        if not values.get('checkpoint_path'):
            values['checkpoint_path'] = f"s3://{bucket}/checkpointing/{current_date}"

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
```

- [[Data Class with Pydantic]]
- [[Pytorch Estimator Training for RnR BSM]]



-----------
##  Recommended Notes


- [[Pytorch Estimator Inference for RnR BSM]]
- [[Batch Transform using Endpoint from SageMaker]]
