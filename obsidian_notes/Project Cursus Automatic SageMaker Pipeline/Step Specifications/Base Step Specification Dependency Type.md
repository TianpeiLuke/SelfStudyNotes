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


```python
class DependencyType(Enum):
    """Types of dependencies in the pipeline."""
    MODEL_ARTIFACTS = "model_artifacts"
    PROCESSING_OUTPUT = "processing_output"
    TRAINING_DATA = "training_data"
    HYPERPARAMETERS = "hyperparameters"
    PAYLOAD_SAMPLES = "payload_samples"
    CUSTOM_PROPERTY = "custom_property"
    
    def __eq__(self, other):
        """Compare enum instances by value."""
        if isinstance(other, DependencyType):
            return self.value == other.value
        return super().__eq__(other)
        
    def __hash__(self):
        """Ensure hashability is maintained when used as dictionary keys."""
        return hash(self.value)
```


- [[Base Step Specification]]
- [[Base Step Specification DependencySpec]]

### Creating Dependency Specifications

```python
from src.pipeline_deps.base_specifications import DependencySpec, DependencyType

# Define a training data dependency
training_data_dep = DependencySpec(
    logical_name="training_data",
    dependency_type=DependencyType.PROCESSING_OUTPUT,
    required=True,
    compatible_sources=["DataLoadingStep", "PreprocessingStep"],
    semantic_keywords=["data", "dataset", "training"],
    data_type="S3Uri",
    description="Training dataset for model training"
)
```



-----------
##  Recommended Notes


- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Specification Registry Design]]
- [[Config-Driven vs Specification-Driven Design]]
