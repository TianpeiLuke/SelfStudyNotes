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
    # Processing instance settings
    processing_instance_count: int = Field(
        default=1, 
        ge=1, 
        le=10, 
        description="Instance count for processing jobs"
    )
    processing_volume_size: int = Field(
        default=500, 
        ge=10, 
        le=1000, 
        description="Volume size for processing jobs in GB"
    )
    processing_instance_type_large: str = Field(
        default='ml.m5.4xlarge', 
        description="Large instance type for processing step."
    )
    processing_instance_type_small: str = Field(
        default='ml.m5.2xlarge', 
        description="Small instance type for processing step."
    )
    use_large_processing_instance: bool = Field(
        default=False,
        description="Set to True to use large instance type, False for small instance type."
    )
    
    # Script and directory settings
    processing_source_dir: Optional[str] = Field(
        default=None, 
        description="Source directory for processing scripts. Falls back to base source_dir if not provided."
    )
    processing_entry_point: Optional[str] = Field(
        default=None,
        description="Entry point script for processing, must be relative to source directory. Can be overridden by derived classes."
    )
    processing_script_arguments: Optional[List[str]] = Field(
        default=None,
        description="Optional arguments for the processing script."
    )
    
    # Framework version
    processing_framework_version: str = Field(
        default='0.23-1',
        description="Version of the scikit-learn framework to use in SageMaker Processing. Format: '<sklearn-version>-<build-number>'"
    )

    # Optional Input/Output settings - to be defined by derived classes
    input_names: Optional[Dict[str, str]] = Field(
        default=None,
        description="Optional dictionary mapping input names to their descriptions. Should be defined in derived classes."
    )
    output_names: Optional[Dict[str, str]] = Field(
        default=None,
        description="Optional dictionary mapping output names to their descriptions. Should be defined in derived classes."
    )

    class Config(BasePipelineConfig.Config):
        pass

    @field_validator('processing_source_dir')
    @classmethod
    def validate_processing_source_dir(cls, v: Optional[str]) -> Optional[str]:
        """Validate processing source directory if provided"""
        if v is not None:
            if v.startswith('s3://'):
                if not v.replace('s3://', '').strip('/'):
                    raise ValueError(f"Invalid S3 path format: {v}")
            else:
                path = Path(v)
                if not path.exists():
                    raise ValueError(f"Processing source directory does not exist: {v}")
                if not path.is_dir():
                    raise ValueError(f"Processing source directory is not a directory: {v}")
        return v

    @field_validator('processing_entry_point')
    @classmethod
    def validate_entry_point_is_relative(cls, v: Optional[str]) -> Optional[str]:
        """Validate entry point is a relative path if provided"""
        if v is not None:
            if not v:
                raise ValueError("processing_entry_point if provided cannot be empty.")
            if Path(v).is_absolute() or v.startswith('/') or v.startswith('s3://'):
                raise ValueError(
                    f"processing_entry_point ('{v}') must be a relative path within source directory."
                )
        return v
    
    @field_validator('processing_framework_version')
    @classmethod
    def validate_framework_version(cls, v: str) -> str:
        """
        Validate processing framework version matches SageMaker SKLearn versions.
        Reference: https://sagemaker.readthedocs.io/en/stable/frameworks/sklearn/sagemaker.sklearn.html
        """
        valid_versions = [
            '0.20.0-1',
            '0.23-1',  # Supports scikit-learn 0.23.2
            '1.0-1',   # Supports scikit-learn 1.0.2
            '1.2-1'    # Supports scikit-learn 1.2.2
        ]
        if v not in valid_versions:
            raise ValueError(
                f"Invalid processing framework version: {v}. "
                f"Must be one of {valid_versions}. "
                "These versions correspond to SageMaker's SKLearn processing container versions."
            )
        return v

    @model_validator(mode='after')
    def validate_entry_point_paths(self) -> 'ProcessingStepConfigBase':
        """Validate entry point exists in the effective source directory if both are provided"""
        if self.processing_entry_point is None:
            logger.info("No processing_entry_point provided in base config. Skipping path validation.")
            return self

        effective_source_dir = self.get_effective_source_dir()
        
        if not effective_source_dir:
            if not self.processing_entry_point.startswith('s3://'):
                raise ValueError(
                    "Either processing_source_dir or source_dir must be defined "
                    "to locate local processing_entry_point."
                )
        elif effective_source_dir.startswith('s3://'):
            logger.info(
                f"Processing source directory ('{effective_source_dir}') is S3. "
                f"Assuming processing_entry_point '{self.processing_entry_point}' exists within it."
            )
        else:
            script_full_path = Path(effective_source_dir) / self.processing_entry_point
            if not script_full_path.is_file():
                raise FileNotFoundError(
                    f"Processing entry point script '{self.processing_entry_point}' "
                    f"not found within effective source directory '{effective_source_dir}'. "
                    f"Looked at: '{script_full_path}'"
                )
            logger.info(f"Validated processing_entry_point '{script_full_path}' exists.")
            
        return self

    def get_effective_source_dir(self) -> Optional[str]:
        """Get the effective source directory"""
        return self.processing_source_dir or self.source_dir

    def get_instance_type(self, size: Optional[str] = None) -> str:
        """
        Get the appropriate instance type based on size parameter or configuration.
        
        Args:
            size (Optional[str]): Override 'small' or 'large'. If None, uses use_large_processing_instance.
            
        Returns:
            str: The corresponding instance type
        """
        if size is None:
            size = 'large' if self.use_large_processing_instance else 'small'
            
        if size.lower() == 'large':
            return self.processing_instance_type_large
        elif size.lower() == 'small':
            return self.processing_instance_type_small
        else:
            raise ValueError(f"Invalid size parameter: {size}. Must be 'small' or 'large'")

    def get_script_path(self) -> Optional[str]:
        """
        Get the full path to the processing script if entry point is provided.
        
        Returns:
            Optional[str]: Full path to the script or None if no entry point is set
        """
        if self.processing_entry_point is None:
            return None
            
        effective_source_dir = self.get_effective_source_dir()
        if effective_source_dir.startswith('s3://'):
            return f"{effective_source_dir.rstrip('/')}/{self.processing_entry_point}"
        return str(Path(effective_source_dir) / self.processing_entry_point)

```



## Derived Classes

- [[Config for Packaging Step]]
- [[Config for Payload Generation Step]]



-----------
##  Recommended Notes


- [[Data Class with Pydantic]]
- [[Simple Data Class from Pydantic]]

