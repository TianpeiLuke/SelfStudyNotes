---
tags:
  - code
  - code_snippet
  - aws/sagemaker_pipeline
keywords: 
topics: 
language: python
date of note: 2025-06-15
---

## Code Snippet Summary

>[!important]


## Code

```python
from pydantic import Field, model_validator
from typing import Optional, Dict, ClassVar
```


```python
from .config_processing_step_base import ProcessingStepConfigBase
from .hyperparameters_base import ModelHyperparameters
```

- [[Base Config for Processing Step]]
- [[Hyperparameter for Training Step]]


```python
class XGBoostModelEvalConfig(ProcessingStepConfigBase):
    """
    Configuration for XGBoost model evaluation step.
    Inherits from ProcessingStepConfigBase.
    """
    processing_entry_point: str = Field(
        default="model_evaluation_xgboost.py",
        description="Entry point script for model evaluation."
    )

    # Input/output names for evaluation with defaults
    INPUT_CHANNELS: ClassVar[Dict[str, str]] = {
        "model_input": "Model artifacts input",
        "eval_data_input": "Evaluation data input",
        #"code_input": "Processing code input"
    }

    OUTPUT_CHANNELS: ClassVar[Dict[str, str]] = {
        "eval_output": "Output name for evaluation predictions",
        "metrics_output": "Output name for evaluation metrics"
    }

    job_type: str = Field(
        default="calibration",
        description="Which split to evaluate on (e.g., 'training', 'calibration', 'validation', 'test')."
    )

    hyperparameters: ModelHyperparameters = Field(
        ...,
        description="Model hyperparameters config, including id_name, label_name, field lists, etc."
    )

    eval_metric_choices: Optional[list] = Field(
        default_factory=lambda: ["auc", "average_precision", "f1_score"],
        description="List of evaluation metrics to compute"
    )

    # XGBoost specific fields
    xgboost_framework_version: str = Field(
        default="1.5-1",
        description="XGBoost framework version for processing"
    )

    class Config(ProcessingStepConfigBase.Config):
        pass

    @model_validator(mode='after')
    def validate_eval_config(self) -> 'XGBoostModelEvalConfig':
        """Additional validation specific to evaluation configuration"""
        if not self.processing_entry_point:
            raise ValueError("evaluation step requires a processing_entry_point")
            
        valid_job_types = {"training", "calibration", "validation", "test"}
        if self.job_type not in valid_job_types:
            raise ValueError(f"job_type must be one of {valid_job_types}, got '{self.job_type}'")
        
        if not isinstance(self.hyperparameters, ModelHyperparameters):
            raise ValueError("hyperparameters must be an instance of ModelHyperparameters")
            
        return self

    def get_input_names(self) -> Dict[str, str]:
        return self.INPUT_CHANNELS

    def get_output_names(self) -> Dict[str, str]:
        return self.OUTPUT_CHANNELS

    def get_script_path(self) -> str:
        return super().get_script_path() or self.processing_entry_point
```





-----------
##  Recommended Notes

