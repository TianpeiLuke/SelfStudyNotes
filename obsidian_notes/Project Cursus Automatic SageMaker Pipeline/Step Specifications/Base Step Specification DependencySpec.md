---
tags:
  - code
  - code_snippet
  - aws/sagemaker_pipeline
  - amazon/mods_pipeline
keywords: 
topics: 
language: python
date of note: 2025-07-16
---

## Code Snippet Summary

>[!important]


## Code

```python
from typing import Dict, List, Optional, Any, Set, Union, TYPE_CHECKING, Tuple
from enum import Enum
from abc import ABC, abstractmethod
import logging
import re
```

```python
from pydantic import BaseModel, Field, field_validator, model_validator, ConfigDict
```

- [[Base Step Specification Dependency Type]]

```python
class DependencySpec(BaseModel):
    """Declarative specification for a step's dependency requirement."""
    
    model_config = ConfigDict(
        # Enable enum validation by value
        use_enum_values=True,
        # Validate assignment after object creation
        validate_assignment=True,
        # Allow arbitrary types for complex objects
        arbitrary_types_allowed=True,
        # Generate JSON schema
        json_schema_extra={
            "examples": [
                {
                    "logical_name": "training_data",
                    "dependency_type": "processing_output",
                    "required": True,
                    "compatible_sources": ["DataLoadingStep", "PreprocessingStep"],
                    "semantic_keywords": ["data", "dataset", "input"],
                    "data_type": "S3Uri",
                    "description": "Training dataset for model training"
                }
            ]
        }
    )
    
    logical_name: str = Field(
        ...,
        description="How this dependency is referenced",
        min_length=1,
        examples=["training_data", "model_input", "config_data"]
    )
    dependency_type: DependencyType = Field(
        ...,
        description="Type of dependency"
    )
    required: bool = Field(
        default=True,
        description="Whether this dependency is required"
    )
    compatible_sources: List[str] = Field(
        default_factory=list,
        description="Compatible step types that can provide this dependency"
    )
    semantic_keywords: List[str] = Field(
        default_factory=list,
        description="Keywords for semantic matching during dependency resolution"
    )
    data_type: str = Field(
        default="S3Uri",
        description="Expected data type of the dependency"
    )
    description: str = Field(
        default="",
        description="Human-readable description of the dependency"
    )
    
    @field_validator('logical_name')
    @classmethod
    def validate_logical_name(cls, v: str) -> str:
        """Validate logical name is not empty and follows naming conventions."""
        if not v or not v.strip():
            raise ValueError("logical_name cannot be empty or whitespace")
        
        # Optional: Add naming convention validation
        if not v.replace('_', '').replace('-', '').isalnum():
            raise ValueError("logical_name should contain only alphanumeric characters, underscores, and hyphens")
        
        return v.strip()
    
    @field_validator('dependency_type')
    @classmethod
    def validate_dependency_type(cls, v) -> DependencyType:
        """Validate dependency type is a valid enum value."""
        if isinstance(v, str):
            try:
                return DependencyType(v)
            except ValueError:
                valid_values = [e.value for e in DependencyType]
                raise ValueError(f"dependency_type must be one of: {valid_values}")
        elif isinstance(v, DependencyType):
            # With use_enum_values=True, we should return the enum value
            return v
        else:
            raise ValueError("dependency_type must be a DependencyType enum or valid string value")
    
    @field_validator('compatible_sources')
    @classmethod
    def validate_compatible_sources(cls, v: List[str]) -> List[str]:
        """Validate compatible sources list."""
        if not isinstance(v, list):
            raise ValueError("compatible_sources must be a list")
        
        # Remove empty strings and duplicates
        cleaned = list(set(source.strip() for source in v if source and source.strip()))
        return cleaned
    
    @field_validator('semantic_keywords')
    @classmethod
    def validate_semantic_keywords(cls, v: List[str]) -> List[str]:
        """Validate semantic keywords list."""
        if not isinstance(v, list):
            raise ValueError("semantic_keywords must be a list")
        
        # Remove empty strings, convert to lowercase, and remove duplicates
        cleaned = list(set(keyword.strip().lower() for keyword in v if keyword and keyword.strip()))
        return cleaned
```


- [[Base Step Specification]]


-----------
##  Recommended Notes


- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Specification Registry Design]]
- [[Config-Driven vs Specification-Driven Design]]
