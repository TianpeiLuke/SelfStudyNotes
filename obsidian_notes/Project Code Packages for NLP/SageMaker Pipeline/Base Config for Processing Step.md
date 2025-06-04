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
>Base Class for **Processing Steps**
>- Based on `Pydantic` version 2
>- Derived from `BasePipelineConfig`
>- Define common shared attributes
>	- 


## Code

```python
from pydantic import BaseModel, Field, model_validator, field_validator
from typing import List, Optional, Dict, Any
from pathlib import Path
import json
from datetime import datetime
```

### Import Base

```python
from .config_base import BasePipelineConfig
```

- [[Base Config]]

### Base Processing Config

```python
class ProcessingStepConfigBase(BasePipelineConfig):
    """Base configuration for SageMaker Processing Steps."""
    processing_instance_count: int = Field(default=1, ge=1, le=10, description="Instance count for processing jobs")
    processing_volume_size: int = Field(default=500, ge=10, le=1000, description="Volume size for processing jobs in GB")
    # Which instance type to use can be decided by subclass or further fields
    # processing_instance_type_small from original ModelConfig -> maps to a specific instance type
    # processing_instance_type_large from original ModelConfig -> maps to a specific instance type
    processing_instance_type_large: str = Field(default='ml.m5.4xlarge', description="Large instance type for this processing step.")
    processing_instance_type_small: str = Field(default='ml.m5.large', description="Small instance type for this processing step.")
    
    processing_source_dir: Optional[str] = Field(
        default=None, 
        description="Source directory for processing scripts. If not provided, falls back to base source_dir."
    )

    class Config(BasePipelineConfig.Config):
        pass
    
    @field_validator('processing_source_dir')
    @classmethod
    def validate_processing_source_dir(cls, v: Optional[str]) -> Optional[str]:
        """Validate processing source directory if provided"""
        if v is not None:
            if v.startswith('s3://'):
                # Validate S3 path format
                if not v.replace('s3://', '').strip('/'):
                    raise ValueError(f"Invalid S3 path format: {v}")
            else:
                # Validate local path
                path = Path(v)
                if not path.exists():
                    raise ValueError(f"Processing source directory does not exist: {v}")
                if not path.is_dir():
                    raise ValueError(f"Processing source directory is not a directory: {v}")
                
                # Validate presence of processing scripts (optional, uncomment if needed)
                # required_scripts = ['processing.py', 'requirements.txt']
                # for script in required_scripts:
                #     if not (path / script).exists():
                #         raise ValueError(f"Required script {script} not found in {v}")
                
        return v
    
    def get_processing_source_dir(self) -> Optional[str]:
        """
        Get the effective processing source directory.
        Returns the processing_source_dir if set, otherwise falls back to base source_dir.
        """
        return self.processing_source_dir or self.source_dir
    
    def get_instance_type(self, size: str = 'small') -> str:
        """
        Get the appropriate instance type based on size parameter.
        
        Args:
            size (str): 'small' or 'large'
            
        Returns:
            str: The corresponding instance type
        """
        if size.lower() == 'large':
            return self.processing_instance_type_large
        elif size.lower() == 'small':
            return self.processing_instance_type_small
        else:
            raise ValueError(f"Invalid size parameter: {size}. Must be 'small' or 'large'")
```



## Derived Classes

- [[Config for Packaging Step]]
- [[Config for Payload Generation Step]]



-----------
##  Recommended Notes


- [[Data Class with Pydantic]]
- [[Simple Data Class from Pydantic]]

