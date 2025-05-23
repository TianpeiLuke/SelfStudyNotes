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

### Base Config

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

    class Config(BasePipelineConfig.Config):
        pass
```



## Derived Classes

- [[Config for Packaging Step]]
- [[Config for Payload Generation Step]]



-----------
##  Recommended Notes


- [[Data Class with Pydantic]]
- [[Simple Data Class from Pydantic]]

