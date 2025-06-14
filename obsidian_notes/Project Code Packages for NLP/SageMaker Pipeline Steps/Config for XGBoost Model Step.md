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



- [[Builder XGBoost Model Step]]
## Code

```python
from pydantic import BaseModel, Field, model_validator, field_validator
from typing import List, Optional, Dict, Any
from pathlib import Path
import json
from datetime import datetime

```

```python
from .config_base import BasePipelineConfig
```

- [[Base Config]]

### XGBoost Model Creation Config

```python
class XGBoostModelCreationConfig(BasePipelineConfig):
    """Configuration specific to the SageMaker XGBoost Model creation (for inference)."""
    inference_instance_type: str = Field(
        default='ml.m5.large', 
        description="Instance type for inference endpoint/transform job."
    )
    inference_entry_point: str = Field(
        default='inference.py', 
        description="Entry point script for inference."
    )
    framework_version: str = Field(
        default='1.5-1',  # Updated default to XGBoost version
        description="XGBoost framework version"
    )
    # source_dir is inherited from BasePipelineConfig

    # Endpoint / Container specific settings
    initial_instance_count: int = Field(
        default=1, 
        ge=1, 
        description="Initial instance count for endpoint (used by EndpointConfig)."
    )
    container_startup_health_check_timeout: int = Field(
        default=300, 
        ge=60, 
        description="Container startup health check timeout (seconds)."
    )
    container_memory_limit: int = Field(
        default=6144, 
        ge=1024, 
        description="Container memory limit (MB)."
    )
    data_download_timeout: int = Field(
        default=900, 
        ge=60, 
        description="Model data download timeout (seconds)."
    )
    inference_memory_limit: int = Field(
        default=6144, 
        ge=1024, 
        description="Inference memory limit (MB)."
    )
    max_concurrent_invocations: int = Field(
        default=10, 
        ge=1, 
        description="Max concurrent invocations per instance."
    )
    max_payload_size: int = Field(
        default=6, 
        ge=1, 
        le=100, 
        description="Max payload size (MB) for inference."
    )

    class Config(BasePipelineConfig.Config):
        pass
    
    @model_validator(mode='after')
    def validate_configuration(self) -> 'XGBoostModelCreationConfig':
        """Validate the complete configuration"""
        self._validate_memory_constraints()
        self._validate_timeouts()
        self._validate_entry_point()
        self._validate_framework_version()
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

    def _validate_framework_version(self) -> None:
        """Validate XGBoost framework version"""
        valid_versions = ['1.5-1', '1.3-1', '1.2-2', '1.2-1']  # Add more versions as needed
        if self.framework_version not in valid_versions:
            raise ValueError(
                f"Invalid XGBoost framework version: {self.framework_version}. "
                f"Must be one of {valid_versions}"
            )
    
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
        return f"xgb-{self.pipeline_name}-model-{timestamp}"

    def get_endpoint_config_name(self) -> str:
        """Generate endpoint configuration name"""
        return f"{self.get_model_name()}-config"

    def get_endpoint_name(self) -> str:
        """Generate endpoint name"""
        return f"xgb-{self.pipeline_name}-endpoint"
```


-----------
##  Recommended Notes


- [[Config for Pytorch Model Step]]