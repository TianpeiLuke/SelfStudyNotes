---
tags:
  - code
  - code_snippet
  - python/aws_python_sdk
keywords: 
topics: 
language: python
date of note: 2025-05-21
---

## Code Snippet Summary

>[!important]



### Standardization

#### Input and Output Name Format

- [[Rule Standard Input and Output Names and Usage]]

#### Matching Principle

- Use the **VALUE** of **output_names** in dependent steps to match the **KEY** of **input_names** of current step

#### Rule for Updating the Pipeline Builder

- We prefer **pipeline builder** to be as generic as possible
- Prioritize updates on **step builder** first
- Keep **message passing** generic

#### Output Names

>[!important]
> Standard Pattern for `output_names`:
> 
> 1. In config classes, define `output_names` as mapping from **logical names** to **descriptive values**:
> 
> `output_names = {"logical_name": "DescriptiveValue"}`
> 
> 2. In template, `_generate_outputs` will create *outputs dictionary* using **VALUES as keys**:
> 
> `outputs = {"DescriptiveValue": "s3://path/..."}`
> 
> 3. In step builders, use the **VALUES** from `output_names` as keys when validating outputs:
> 
> ```python
> value = self.config.output_names["logical_name"] # Gets "DescriptiveValue"
> if value not in outputs: # Checks if "DescriptiveValue" is in outputs
> 	raise ValueError(f"Must supply an S3 URI for '{value}'")
> ```
> 
> 4. Special case for **processing scripts**: 
> 	- If the script expects specific `output_name` values, use those *directly* for `output_name` while still using **VALUES** for outputs *dictionary lookup*
> 
> 



### Avoid 

```
TypeError: Pipeline variables do not support __str__ operation. Please use `.to_string()` to convert it to string 
type in execution time or use `.expr` to translate it to Json for display purpose in Python SDK.
```

## Code

```python
from abc import ABC, abstractmethod
from typing import Dict, Optional, Any
from pathlib import Path

from sagemaker.workflow.pipeline_context import PipelineSession
from sagemaker.workflow.steps import Step
```


```python
import logging
logger = logging.getLogger(__name__)
```

### Import Base Config

```python
from .config_base import BasePipelineConfig
```

- [[Base Config]]

### Step Name Registry

```python
STEP_NAMES = {
    'Base':                 'BaseStep',
    'Processing':           'ProcessingStep',
    'PytorchTraining':      'PytorchTrainingStep',
    'XGBoostTraining':      'XGBoostTrainingStep',
    'PytorchModel':         'CreatePytorchModelStep',
    'XGBoostModel':         'CreateXGBoostModelStep',
    'Package':              'PackagingStep',
    'Payload':              'PayloadTestStep',
    'Registration':         'RegistrationStep',
    'TabularPreprocessing': 'TabularPreprocessingStep',
    'CurrencyConversion':   'CurrencyConversionStep',
    'CradleDataLoading':    'CradleDataLoadingStep',
    'BatchTransform':       'BatchTransformStep'
    }
```

- [[Builder MODS Cradle Data Loading Step]]
- [[Builder Tabular Preprocessing Step]]
- [[Builder Pytorch Model Step]]
- [[Builder Pytorch Training Step]]
- [[Builder XGBoost Model Step]]
- [[Builder XGBoost Training Step]]
- [[Builder XGBoost Model Evaluation Step]]
- [[Builder Packaging Step]]
- [[Builder Payload Generation Step]]
- [[Builder MODS Model Registration Step]]
- [[Builder Batch Transform Step]]

### Base Builder

```python
class StepBuilderBase(ABC):
    """Base class for all step builders"""

    REGION_MAPPING: Dict[str, str] = {
        "NA": "us-east-1",
        "EU": "eu-west-1",
        "FE": "us-west-2"
    }

    # Define standard step names
    STEP_NAMES = STEP_NAMES

    def __init__(
        self,
        config: BasePipelineConfig,
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None
    ):
        """
        Initialize base step builder.
        
        Args:
            config: Model configuration
            sagemaker_session: SageMaker session
            role: IAM role
            notebook_root: Root directory of notebook
        """
        self.config = config
        self.session = sagemaker_session
        self.role = role
        self.notebook_root = notebook_root or Path.cwd()

        # Validate and set AWS region
        self.aws_region = self.REGION_MAPPING.get(self.config.region)
        if not self.aws_region:
            raise ValueError(
                f"Invalid region code: {self.config.region}. "
                f"Must be one of: {', '.join(self.REGION_MAPPING.keys())}"
            )

        logger.info(f"Initializing {self.__class__.__name__} with region: {self.config.region}")
        self.validate_configuration()

    def _sanitize_name_for_sagemaker(self, name: str, max_length: int = 63) -> str:
        """
        Sanitize a string to be a valid SageMaker resource name component.
        
        Args:
            name: Name to sanitize
            max_length: Maximum length of sanitized name
            
        Returns:
            Sanitized name
        """
        if not name:
            return "default-name"
        sanitized = "".join(c if c.isalnum() else '-' for c in str(name))
        sanitized = '-'.join(filter(None, sanitized.split('-')))
        return sanitized[:max_length].rstrip('-')

    def _get_step_name(self, step_type: str) -> str:
        """
        Get standard step name.
        
        Args:
            step_type: Type of step (e.g., 'Training', 'Model', 'Package')
            
        Returns:
            Standard step name
        """
        if step_type not in self.STEP_NAMES:
            logger.warning(f"Unknown step type: {step_type}. Using default name.")
            return f"Default{step_type}Step"
        return self.STEP_NAMES[step_type]

    def _get_cache_config(self, enable_caching: bool = True) -> Dict[str, Any]:
        """
        Get cache configuration for step.
        
        Args:
            enable_caching: Whether to enable caching
            
        Returns:
            Cache configuration dictionary
        """
        return {
            "enable_caching": enable_caching,
            "expire_after": "P30D"  # Cache expires after 30 days
        }

    @abstractmethod
    def validate_configuration(self) -> None:
        """
        Validate configuration requirements.
        
        Raises:
            ValueError: If configuration is invalid
        """
        pass

    @abstractmethod
    def create_step(self, *args, **kwargs) -> Step:
        """
        Create pipeline step.
        
        Args:
            *args: Positional arguments
            **kwargs: Keyword arguments
            
        Returns:
            SageMaker pipeline step
        """
        pass
```


## Derived Classes

- [[Builder Pytorch Training Step]]
- [[Builder Pytorch Model Step]]



-----------
##  Recommended Notes

- [[Design Pattern Builder Pattern]]
- [[Design Pattern Abstract Factory Pattern]]

- [[MLOps]]
- [[Continuous Delivery or CD in DevOps and MLOps]]
- [[Continuous Integration or CI in DevOps and MLOps]]
