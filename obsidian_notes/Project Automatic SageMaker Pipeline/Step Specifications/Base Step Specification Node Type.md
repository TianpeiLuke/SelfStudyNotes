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
class NodeType(Enum):
    """Types of nodes in the pipeline based on their dependency/output characteristics."""
    SOURCE = "source"      # No dependencies, has outputs (e.g., data loading)
    INTERNAL = "internal"  # Has both dependencies and outputs (e.g., processing, training)
    SINK = "sink"         # Has dependencies, no outputs (e.g., model registration)
    SINGULAR = "singular" # No dependencies, no outputs (e.g., standalone operations)
    
    def __eq__(self, other):
        """Compare enum instances by value."""
        if isinstance(other, NodeType):
            return self.value == other.value
        return super().__eq__(other)
        
    def __hash__(self):
        """Ensure hashability is maintained when used as dictionary keys."""
        return hash(self.value)

```


- [[Base Step Specification]]

## Node Type Constraints

### SOURCE Nodes

>[!important]
> - **No Dependencies** - Cannot have any dependencies
> - **Must Have Outputs** - Must produce at least one output
> - **Examples**: Data loading steps, configuration generators

### INTERNAL Nodes

>[!important]
> - **Must Have Dependencies** - Requires at least one dependency
> - **Must Have Outputs** - Must produce at least one output
> - **Examples**: Processing steps, training steps, transformation steps

### SINK Nodes

>[!important]
> - **Must Have Dependencies** - Requires at least one dependency
> - **No Outputs** - Cannot produce any outputs
> - **Examples**: Model registration, deployment steps, notification steps

### SINGULAR Nodes

>[!important]
> - **No Dependencies** - Cannot have any dependencies
> - **No Outputs** - Cannot produce any outputs
> - **Examples**: Standalone operations, cleanup tasks


-----------
##  Recommended Notes


- [[Step Specification Design as Declarative Pipeline Architecture]]
- [[Specification Registry Design]]
- [[Config-Driven vs Specification-Driven Design]]
