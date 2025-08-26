---
tags:
  - code
  - code_snippet
  - aws/sagemaker_pipeline
keywords: 
topics: 
language: python
date of note: 2025-06-03
---

## Code Snippet Summary

>[!important]


## Code

```python
from typing import Dict, Optional, List
from pathlib import Path

from sagemaker.xgboost import XGBoostModel
from sagemaker.workflow.pipeline_context import PipelineSession
from sagemaker.workflow.model_step import ModelStep
from sagemaker.workflow.parameters import Parameter
from sagemaker.workflow.steps import Step
from sagemaker import image_uris
```


```python
import logging
logger = logging.getLogger(__name__)
```

### Base Class and Config

```python
from .config_model_step_xgboost import XGBoostModelCreationConfig
from .builder_step_base import StepBuilderBase
```

- [[Base Step Builder]]
- [[Config for XGBoost Model Step]]

### Main Builder

```python
class XGBoostModelStepBuilder(StepBuilderBase):
    """Model step builder for XGBoost models"""

    def __init__(
        self, 
        config: XGBoostModelCreationConfig, 
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None
    ):
        """
        Initialize XGBoost model builder
        
        Args:
            config: Pydantic ModelConfig instance with hyperparameters
            sagemaker_session: SageMaker session
            role: IAM role ARN
            notebook_root: Root directory of notebook
        """
        super().__init__(config, sagemaker_session, role, notebook_root)

    def validate_configuration(self) -> None:
        """Validate configuration requirements"""
        required_attrs = [
            'inference_entry_point',
            'source_dir',
            'inference_instance_type',
            'framework_version',
            'container_startup_health_check_timeout',
            'container_memory_limit',
            'data_download_timeout',
            'inference_memory_limit',
            'max_concurrent_invocations',
            'max_payload_size'
        ]
        
        for attr in required_attrs:
            if not hasattr(self.config, attr):
                raise ValueError(f"ModelConfig missing required attribute: {attr}")
                
        if not self.config.inference_entry_point:
            raise ValueError("inference_entry_point cannot be empty")

    def _get_image_uri(self) -> str:
        """Get the XGBoost inference image URI"""
        return image_uris.retrieve(
            framework="xgboost",
            region=self.aws_region,
            version=self.config.framework_version,
            instance_type=self.config.inference_instance_type,
            image_scope="inference"
        )

    def _create_env_config(self) -> dict:
        """Create and validate environment configuration"""
        env_config = {
            'MMS_DEFAULT_RESPONSE_TIMEOUT': str(self.config.container_startup_health_check_timeout),
            'SAGEMAKER_CONTAINER_LOG_LEVEL': '20',
            'SAGEMAKER_PROGRAM': self.config.inference_entry_point,
            'SAGEMAKER_SUBMIT_DIRECTORY': '/opt/ml/model/code',
            'SAGEMAKER_CONTAINER_MEMORY_LIMIT': str(self.config.container_memory_limit),
            'SAGEMAKER_MODEL_DATA_DOWNLOAD_TIMEOUT': str(self.config.data_download_timeout),
            'SAGEMAKER_INFERENCE_MEMORY_LIMIT': str(self.config.inference_memory_limit),
            'SAGEMAKER_MAX_CONCURRENT_INVOCATIONS': str(self.config.max_concurrent_invocations),
            'SAGEMAKER_MAX_PAYLOAD_IN_MB': str(self.config.max_payload_size),
            'AWS_REGION': self.aws_region
        }

        for key, value in env_config.items():
            if value is None or (isinstance(value, str) and not value.strip() and key in ['SAGEMAKER_PROGRAM']):
                raise ValueError(f"Missing or empty environment variable value for critical key: {key}")
            elif value is None or (isinstance(value, str) and not value.strip()):
                logger.warning(f"Environment variable {key} has an effectively empty value: '{value}'. "
                             "This might be acceptable depending on the variable.")

        return env_config

    def _create_xgboost_model(self, model_data: str) -> XGBoostModel:
        """Create XGBoost model"""
        safe_date_string = self.config.current_date.replace(":", "-").replace("T", "-").replace("Z", "")
        model_name = f"xgb-model-{safe_date_string}"[:63]

        return XGBoostModel(
            name=model_name,
            model_data=model_data,
            role=self.role,
            entry_point=self.config.inference_entry_point,
            source_dir=self.config.source_dir,
            framework_version=self.config.framework_version,
            sagemaker_session=self.session,
            env=self._create_env_config(),
            image_uri=self._get_image_uri()
        )

    def create_step(self, model_data: str, dependencies: Optional[List] = None) -> Step:
        """
        Create model step for deployment.
        
        Args:
            model_data: S3 path to model artifacts
            dependencies: List of dependent steps
            
        Returns:
            ModelStep instance
        """
        logger.info(f"Creating model step with instance type: {self.config.inference_instance_type} "
                   f"in region: {self.aws_region}")

        instance_type_param = Parameter(
            name="InferenceInstanceType",
            default_value=self.config.inference_instance_type
        )

        model = self._create_xgboost_model(model_data)
        step_creation_args = model.create(
            instance_type=instance_type_param,
            accelerator_type=None
        )
        
        step_name = self._get_step_name('Model')
        
        model_step = ModelStep(
            name=step_name,
            step_args=step_creation_args
        )
        
        # Store model data path for subsequent steps
        model_step.model_artifacts_path = model_data
        
        return model_step

    # Maintain backwards compatibility
    def create_model_step(self, model_data: str) -> ModelStep:
        """Backwards compatible method for creating model step"""
        return self.create_step(model_data)
```


## Previous Step

- [[Builder XGBoost Training Step]]

## Next Step

- [[Builder Packaging Step]]


-----------
##  Recommended Notes

- [[Builder Pytorch Model Step]]