---
tags:
  - code
  - code_snippet
  - python/pydantic
  - aws/step_function
  - aws/sagemaker_pipeline
keywords: 
topics: 
language: python
date of note: 2025-05-22
---

## Code Snippet Summary

>[!important]
>Create Config Class for **Pytorch Model Creation** Step
>- Based on `Pydantic` version 2
>- Derived from `BasePipelineConfig`
>- Used to define `PytorchModelStepBuilder`

### Builder

- [[Builder Pytorch Model Step]]

## Code

```python
from pydantic import BaseModel, Field, model_validator, field_validator
from typing import List, Optional, Dict, Any
from pathlib import Path
import json
from datetime import datetime
```

### Import Base Config

```python
from .config_base import BasePipelineConfig
```

- [[Base Config]]

```python
class PytorchModelCreationConfig(BasePipelineConfig): 
    """Configuration specific to the SageMaker Model creation (for inference)."""
    inference_instance_type: str = Field(default='ml.m5.large', description="Instance type for inference endpoint/transform job.")
    inference_entry_point: str = Field(default='inference.py', description="Entry point script for inference.")
    # source_dir is inherited from BasePipelineConfig, assumed to contain inference_entry_point
    # framework_version, py_version are inherited from BasePipelineConfig

    # Endpoint / Container specific settings
    initial_instance_count: int = Field(default=1, ge=1, description="Initial instance count for endpoint (used by EndpointConfig).")
    container_startup_health_check_timeout: int = Field(default=300, ge=60, description="Container startup health check timeout (seconds).")
    container_memory_limit: int = Field(default=6144, ge=1024, description="Container memory limit (MB).")
    data_download_timeout: int = Field(default=900, ge=60, description="Model data download timeout (seconds).")
    inference_memory_limit: int = Field(default=6144, ge=1024, description="Inference memory limit (MB).")
    max_concurrent_invocations: int = Field(default=10, ge=1, description="Max concurrent invocations per instance.") # Increased default
    max_payload_size: int = Field(default=6, ge=1, le=100, description="Max payload size (MB) for inference.") # Increased range

    class Config(BasePipelineConfig.Config):
        pass
    
    @model_validator(mode='after')
    def validate_configuration(self) -> 'ModelCreationConfig':
        """Validate the complete configuration"""
        self._validate_memory_constraints()
        self._validate_timeouts()
        self._validate_entry_point()
        return self

    def _validate_memory_constraints(self) -> None:
        """Validate memory-related constraints"""
        if self.inference_memory_limit > self.container_memory_limit:
            raise ValueError(
                f"Inference memory limit ({self.inference_memory_limit}MB) cannot exceed "
                f"container memory limit ({self.container_memory_limit}MB)"
            )
            
    def _validate_timeouts(self) -> None:
        """Validate timeout-related configurations"""
        if self.container_startup_health_check_timeout > self.data_download_timeout:
            raise ValueError(
                "Container startup health check timeout should not exceed data download timeout"
            )

    def _validate_entry_point(self) -> None:
        """Validate entry point script"""
        if self.source_dir and not self.source_dir.startswith('s3://'):
            entry_point_path = Path(self.source_dir) / self.inference_entry_point
            if not entry_point_path.exists():
                raise ValueError(f"Inference entry point script not found: {entry_point_path}")
    
    @field_validator('inference_memory_limit')
    @classmethod
    def validate_memory_limits(cls, v: int, info) -> int:
        container_memory_limit = info.data.get('container_memory_limit')
        if container_memory_limit and v > container_memory_limit:
            raise ValueError("Inference memory limit cannot exceed container memory limit")
        return v

    @field_validator('inference_instance_type')
    @classmethod
    def _validate_sagemaker_inference_instance_type(cls, v: str) -> str:
        if not v.startswith('ml.'):
            raise ValueError(f"Invalid inference instance type: {v}. Must start with 'ml.'")
        return v

    
    def get_model_name(self) -> str:
        """Generate a unique model name"""
        timestamp = datetime.now().strftime("%Y%m%d-%H%M%S")
        return f"{self.pipeline_name}-model-{timestamp}"

    def get_endpoint_config_name(self) -> str:
        """Generate endpoint configuration name"""
        return f"{self.get_model_name()}-config"

    def get_endpoint_name(self) -> str:
        """Generate endpoint name"""
        return f"{self.pipeline_name}-endpoint"
```




-----------
##  Recommended Notes

- [[Simple Data Class from Pydantic]]