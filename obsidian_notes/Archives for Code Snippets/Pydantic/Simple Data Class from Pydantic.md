---
tags:
  - code
  - code_snippet
  - python/pydantic
keywords: 
topics: 
language: python
date of note: 2025-04-04
---

## Code Snippet Summary

>[!important]
>Create a simple `pydantic`  data class 


## Code


```python
from typing import Dict, List, Tuple, Optional
from pydantic import BaseModel, Field
```


```python
class BSMAnalysis(BaseModel):
    """Structured container for analysis results with validation"""
    category: str = Field(default="Unknown")
    confidence_score: float = Field(default=0.0, ge=0.0, le=1.0)
    message_evidence: List[str] = Field(default_factory=list)
    shipping_evidence: List[str] = Field(default_factory=list)
    timeline_evidence: List[str] = Field(default_factory=list)
    primary_factors: List[str] = Field(default_factory=list)
    supporting_evidence: List[str] = Field(default_factory=list)
    contradicting_evidence: List[str] = Field(default_factory=list)
    raw_response: str = Field(default="")
    error: Optional[str] = Field(default=None)
    latency: Optional[float] = Field(default=None)

    class Config:
        validate_assignment = True
```

- `pydantic.BaseModel`
	- [reference](https://docs.pydantic.dev/latest/api/base_model/)
	- [pydantic concept: models](https://docs.pydantic.dev/latest/concepts/models/)
	- `.model_dump`: [link](https://docs.pydantic.dev/latest/api/base_model/#pydantic.BaseModel.model_dump)


- `pydantic.Field`
	- [pydantic concept: field](https://docs.pydantic.dev/latest/concepts/fields/)
	- `default`: 
		- default values for fields; can also use the normal assignment syntax
	- `default_factory`: 
		- default defined by a *callable* to generate a default value
	- `validate_default` (or the [`validate_default`](https://docs.pydantic.dev/latest/api/config/#pydantic.config.ConfigDict.validate_default) configuration value) 
		- used to validate default values
		- By default, Pydantic will _not_ validate default values. 
	- `alias`: 
		- define an alias for a field; work for both *validation* and *serialization*
		- `Field(alias='foo')`
		- `Field(validation_alias='foo')`
		- `Field(serialization_alias='foo')`
	- `frozen`: 
		- *prevent* the field from being assigned a new value after the model is created (immutability).
	- `exclude` 
		- control which fields should be excluded from the model *when exporting* the model.
	- Numerical Constraint
		- `gt` - greater than
		- `lt` - less than
		- `ge` - greater than or equal to
		- `le` - less than or equal to
		- `multiple_of` - a multiple of the given number
		- `allow_inf_nan` - allow `'inf'`, `'-inf'`, `'nan'` values
	- String Constraint
		- There are fields that can be used to constrain strings:
		- `min_length`: Minimum length of the string.
		- `max_length`: Maximum length of the string.
		- `pattern`: A regular expression that the string must match.





-----------
##  Recommended Notes



- [[Prompt RnR Reason Code 02 1-Parse]]