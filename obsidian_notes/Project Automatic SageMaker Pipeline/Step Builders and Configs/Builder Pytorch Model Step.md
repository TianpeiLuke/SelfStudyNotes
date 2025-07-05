---
tags:
  - code
  - code_snippet
  - python/aws_python_sdk
  - aws/sagemaker
  - aws/step_function
keywords: 
topics: 
language: python
date of note: 2025-05-20
---

## Code Snippet Summary

>[!important]
>**Builder** for `PytorchModelStep`
>- Create a SageMaker model object (`sagemaker.model.Model` or `sagemaker.pytorch.model.PyTorchModel`)
>- Register that model in SageMaker using `model.create(...)`

- [[Design Pattern Builder Pattern]]


### Previous Step

- [[Builder Pytorch Training Step]]

## Code


```python
from typing import Dict, Optional, List
from pathlib import Path

from sagemaker.pytorch import PyTorchModel
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


### Import Model Config and Base Class

```python
from .config_model_step_pytorch import PytorchModelCreationConfig
from .builder_step_base import StepBuilderBase
```

- [[Config for Pytorch Model Step]]
- [[Base Step Builder]]

### Builder Class

```python
class PytorchModelStepBuilder(StepBuilderBase):
    """Model step builder for PyTorch models"""

    def __init__(
        self, 
        config: PytorchModelCreationConfig, 
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None
    ):
        """
        Initialize PyTorch model builder
        
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
            'py_version',
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
        """Get the PyTorch inference image URI"""
        return image_uris.retrieve(
            framework="pytorch",
            region=self.aws_region,
            version=self.config.framework_version,
            py_version=self.config.py_version,
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

    def _create_pytorch_model(self, model_data: str) -> PyTorchModel:
        """Create PyTorch model"""
        safe_date_string = self.config.current_date.replace(":", "-").replace("T", "-").replace("Z", "")
        model_name = f"bsm-rnr-model-{safe_date_string}"[:63]

        return PyTorchModel(
            name=model_name,
            model_data=model_data,
            role=self.role,
            entry_point=self.config.inference_entry_point,
            source_dir=self.config.source_dir,
            framework_version=self.config.framework_version,
            py_version=self.config.py_version,
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

        model = self._create_pytorch_model(model_data)
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


### Learning: Model Step

```python
        model = PyTorchModel(
            name=model_name,
            model_data=model_data,  # This is the Properties object from the training step
            role=self.role,
            entry_point=self.config.inference_entry_point, # From your _create_env_config, e.g., "inference.py"
            source_dir=self.config.source_dir,          # Path to your inference code directory
            framework_version=self.config.framework_version,
            py_version=self.config.py_version,
            sagemaker_session=self.session,
            env=self._create_env_config(),
            image_uri=self._get_image_uri()
            # You can add other PyTorchModel parameters if needed (e.g., dependencies)
        )

        # The step_args should come from model.create()
        step_creation_args = model.create(
            instance_type=instance_type_param,
            accelerator_type=None # Or configure as needed
        )

        ModelStep(
            name="CreateInferenceModel", # Or your preferred step name
            step_args=step_creation_args
        )
```


- `sagemaker.workflow.model_step.ModelStep`
	- [reference](https://sagemaker.readthedocs.io/en/stable/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.model_step.ModelStep)
	- ModelStep for SageMaker Pipelines Workflows.
		- Constructs a ModelStep.
	- **name** ([_str_](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the ModelStep. A name is required and must be unique within a pipeline.
	- **step_args** (__ModelStepArguments_) 
		- The arguments for the ModelStep definition, generated by invoking the [`register()`](https://sagemaker.readthedocs.io/en/stable/api/inference/model.html#sagemaker.model.Model.register "sagemaker.model.Model.register") or [`create()`](https://sagemaker.readthedocs.io/en/stable/api/inference/model.html#sagemaker.model.Model.create "sagemaker.model.Model.create") under the [`PipelineSession`](https://sagemaker.readthedocs.io/en/stable/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.pipeline_context.PipelineSession "sagemaker.workflow.pipeline_context.PipelineSession"). Example:


## Previous Step

- [[Builder Pytorch Training Step]]

## Next Step

- [[AWS Step Functions - Endpoint Step]]


-----------
##  Recommended Notes


- [[Pytorch Estimator Inference for RnR BSM]]


- [[AWS Step Functions - One-Step Processing Workflow]]
- [[Amazon SageMaker Python SDK 3 Frameworks]]
- [[Amazon SageMaker Python SDK 3.1.1 Pytorch Train]]
- [[Amazon SageMaker Python SDK 3.1.2 Pytorch Deploy and Hosting]]


- [[Design Pattern Builder Pattern]]
- [[Docker Container Images]]

- [[MLOps]]
- [[Continuous Delivery or CD in DevOps and MLOps]]
- [[Continuous Integration or CI in DevOps and MLOps]]
