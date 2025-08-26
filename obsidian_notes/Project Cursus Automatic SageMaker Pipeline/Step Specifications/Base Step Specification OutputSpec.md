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
class OutputSpec(BaseModel):
    """Declarative specification for a step's output."""
    
    model_config = ConfigDict(
        use_enum_values=True,
        validate_assignment=True,
        arbitrary_types_allowed=True,
        json_schema_extra={
            "examples": [
                {
                    "logical_name": "processed_data",
                    "aliases": ["ProcessedData", "DATA"],
                    "output_type": "processing_output",
                    "property_path": "properties.ProcessingOutputConfig.Outputs['processed_data'].S3Output.S3Uri",
                    "data_type": "S3Uri",
                    "description": "Processed training data output"
                }
            ]
        }
    )
    
    logical_name: str = Field(
        ...,
        description="Primary name for this output",
        min_length=1,
        examples=["processed_data", "model_artifacts", "evaluation_results"]
    )
    aliases: List[str] = Field(
        default_factory=list,
        description="Alternative names that can be used to reference this output"
    )
    output_type: DependencyType = Field(
        ...,
        description="Type of output"
    )
    property_path: str = Field(
        ...,
        description="Runtime SageMaker property path to access this output",
        min_length=1
    )
    data_type: str = Field(
        default="S3Uri",
        description="Output data type"
    )
    description: str = Field(
        default="",
        description="Human-readable description of the output"
    )
    
    @field_validator('logical_name')
    @classmethod
    def validate_logical_name(cls, v: str) -> str:
        """Validate logical name is not empty and follows naming conventions."""
        if not v or not v.strip():
            raise ValueError("logical_name cannot be empty or whitespace")
        
        if not v.replace('_', '').replace('-', '').isalnum():
            raise ValueError("logical_name should contain only alphanumeric characters, underscores, and hyphens")
        
        return v.strip()
    
    @field_validator('output_type')
    @classmethod
    def validate_output_type(cls, v) -> DependencyType:
        """Validate output type is a valid enum value."""
        if isinstance(v, str):
            try:
                return DependencyType(v)
            except ValueError:
                valid_values = [e.value for e in DependencyType]
                raise ValueError(f"output_type must be one of: {valid_values}")
        elif isinstance(v, DependencyType):
            # With use_enum_values=True, we should return the enum value
            return v
        else:
            raise ValueError("output_type must be a DependencyType enum or valid string value")
    
    @field_validator('aliases')
    @classmethod
    def validate_aliases(cls, v: List[str]) -> List[str]:
        """Validate aliases list."""
        if not isinstance(v, list):
            raise ValueError("aliases must be a list")
        
        # Remove empty strings, strip whitespace, and remove duplicates
        cleaned = []
        seen = set()
        for alias in v:
            if alias and alias.strip():
                alias_clean = alias.strip()
                # Validate alias follows same naming conventions as logical names
                if not alias_clean.replace('_', '').replace('-', '').isalnum():
                    raise ValueError(f"alias '{alias_clean}' should contain only alphanumeric characters, underscores, and hyphens")
                if alias_clean.lower() not in seen:
                    cleaned.append(alias_clean)
                    seen.add(alias_clean.lower())
        
        return cleaned
    
    @field_validator('property_path')
    @classmethod
    def validate_property_path(cls, v: str) -> str:
        """Validate property path is not empty and has basic structure."""
        if not v or not v.strip():
            raise ValueError("property_path cannot be empty or whitespace")
        
        # Basic validation for SageMaker property path structure
        v = v.strip()
        if not v.startswith('properties.'):
            raise ValueError("property_path should start with 'properties.'")
        
        return v
    
    @model_validator(mode='after')
    def validate_aliases_no_conflict(self) -> 'OutputSpec':
        """Validate that aliases don't conflict with the logical name."""
        if self.aliases:
            # Check if any alias matches the logical name (case-insensitive)
            logical_name_lower = self.logical_name.lower()
            for alias in self.aliases:
                if alias.lower() == logical_name_lower:
                    raise ValueError(f"alias '{alias}' cannot be the same as logical_name '{self.logical_name}'")
        
        return self
```

- [[Property Reference Class as Bridge between Definition-time and Runtime]]
- [[Base Step Specification Dependency Type]]
- [[Base Step Specification]]

### Creating Output Specifications

```python
from src.pipeline_deps.base_specifications import OutputSpec, DependencyType

# Define a model artifacts output with aliases
model_output = OutputSpec(
    logical_name="model_output",
    output_type=DependencyType.MODEL_ARTIFACTS,
    property_path="properties.ModelArtifacts.S3ModelArtifacts",
    data_type="S3Uri",
    description="Trained model artifacts",
    aliases=["ModelArtifacts", "model_data", "output_path", "model_input"]
)
```

### Using Output Aliases

```python
# Access output by primary name
primary_output = step_spec.get_output("model_output")

# Access output by alias
alias_output = step_spec.get_output_by_name_or_alias("ModelArtifacts")
legacy_output = step_spec.get_output_by_name_or_alias("model_data")

# All references point to the same output
assert primary_output == alias_output == legacy_output

# List all available names for an output
all_names = [model_output.logical_name] + model_output.aliases
print(f"Available names: {all_names}")
# Output: ['model_output', 'ModelArtifacts', 'model_data', 'output_path', 'model_input']
```



-----------
##  Recommended Notes


- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Specification Registry Design]]
- [[Config-Driven vs Specification-Driven Design]]
