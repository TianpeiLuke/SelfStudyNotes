---
tags:
  - code
  - code_snippet
  - python/aws_python_sdk
  - aws/step_function
  - aws/sagemaker_pipeline
  - amazon/mods_pipeline
keywords: 
topics: 
language: python
date of note: 2025-05-21
---

## Code Snippet Summary

>[!important]
>In this code, we provide an end-to-end **SageMaker Pipeline**.
>
>This pipeline consists of the following steps
>- **Training Step**
>- **Model Creation Step**
>- **Model Packaging Step**
>- **Model Registration Step**


## Code

```python
from typing import Dict, Optional, List
from pathlib import Path
```

```python
import logging
logger = logging.getLogger(__name__)
```

### SageMaker Pipeline

```python
from sagemaker.workflow.pipeline import Pipeline
from sagemaker.workflow.parameters import ParameterString
from sagemaker.workflow.steps import ProcessingStep
from sagemaker.workflow.pipeline_context import PipelineSession
```

### Import Builders

```python
# Import Builders
from .builder_model_step_pytorch import PytorchModelStepBuilder
from .builder_mims_packaging_step import MIMSPackagingStepBuilder
from .builder_mims_registration_step import ModelRegistrationStepBuilder
```

- [[Base Step Builder]]
- [[Builder Pytorch Training Step]]
- [[Builder Pytorch Model Step]]
- [[MODS Packaging Step Builder]]
- [[MODS Model Registration Step Builder]]

### Import Configs

```python
# Import Builders
from .utils import load_configs

# Import all Configs
from .config_base import BasePipelineConfig
from .config_training_step_pytorch import PytorchTrainingConfig
from .config_model_step_pytorch import PytorchModelCreationConfig
from .config_processing_step_base import ProcessingStepConfigBase
from .config_mims_packaging_step import PackageStepConfig
from .config_mims_registration_step import ModelRegistrationConfig
from .config_mims_payload_step import PayloadConfig
```


```python
CONFIG_CLASSES = {
        'BasePipelineConfig': BasePipelineConfig,
        'PytorchTrainingConfig': PytorchTrainingConfig,
        'PytorchModelCreationConfig': PytorchModelCreationConfig,
        'ProcessingStepConfigBase': ProcessingStepConfigBase,
        'PackageStepConfig': PackageStepConfig,
        'ModelRegistrationConfig': ModelRegistrationConfig,
        'PayloadConfig': PayloadConfig
    }
```

- [[Base Config]]
- [[Config for Pytorch Training Step]]
- [[Config for Pytorch Model Step]]
- [[Base Config for Processing Step]]
- [[Config for Packaging Step]]
- [[Config for Model Registration Step]]
- [[Config for Payload Generation Step]]
- [[Serialize and Save all Configs in one JSON]]

###  Pipeline Builder

```python
class PytorchPipelineBuilder:
    """Builder for model deployment pipeline without training"""

    def __init__(
        self,
        config_path: str,
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None
    ):
        """
        Initialize pipeline builder.
        
        Args:
            config_path: Path to the JSON config file
            sagemaker_session: SageMaker session
            role: IAM role
            notebook_root: Root directory of notebook
        """
        # Load configs from JSON
        self.configs = load_configs(config_path, CONFIG_CLASSES)
        
        # Extract individual configs
        self.base_config = self.configs['Base']
        self.model_config = self.configs['Model']
        self.package_config = self.configs['Package']
        self.registration_config = self.configs['Registration']
        self.payload_config = self.configs['Payload']

        self.session = sagemaker_session
        self.role = role
        self.notebook_root = notebook_root or Path.cwd()

        logger.info(f"Initializing PipelineBuilder for pipeline: {self.base_config.pipeline_name}")

    def _create_model_step(self, model_s3_path: str):
        """Create model step using provided model S3 path."""
        logger.info(f"Creating model step with model from: {model_s3_path}")
        
        logger.info("Force the model region to be NA")
        self.model_config.region = 'NA'
        self.model_config.aws_region = 'us-east-1'
        logger.info(f"Model aws region {self.model_config.aws_region}")

        model_builder = PytorchModelStepBuilder(
            config=self.model_config,
            sagemaker_session=self.session,
            role=self.role
        )
        return model_builder.create_model_step(model_data=model_s3_path)

    def _create_packaging_step(self, model_step):
        """Create MIMS packaging step"""
        logger.info("Creating MIMS packaging step")
        packaging_builder = MIMSPackagingStepBuilder(
            config=self.package_config,
            sagemaker_session=self.session,
            role=self.role,
            notebook_root=self.notebook_root  # Added notebook_root
        )
        return packaging_builder.create_packaging_step(
            model_data=model_step.model_artifacts_path,
            dependencies=[model_step]
        )

    def _create_registration_steps(self, packaging_step: ProcessingStep) -> Dict[str, ProcessingStep]:
        """Create model registration steps"""
        logger.info("Creating registration steps")
        registration_builder = ModelRegistrationStepBuilder(
            config=self.registration_config,
            sagemaker_session=self.session,
            role=self.role
        )
        logger.info("Save Payload")
        self.payload_config.generate_and_upload_payloads()
    
        try:
            # Get output name from package config
            output_name = self.package_config.packaged_model_output_name_from_job
            logger.info(f"Looking for output with name: {output_name}")
        
            # Get the S3 URI directly from the first output
            outputs = packaging_step.properties.ProcessingOutputConfig.Outputs
            s3_uri = outputs[0].S3Output.S3Uri
        
            # Log using expr
            logger.info(f"Using output expression: {outputs[0].expr}")
        
            return registration_builder.create_registration_steps(
                packaging_step_output=s3_uri,
                payload_s3_key=self.payload_config.sample_payload_s3_key,
                dependencies=[packaging_step],
                regions=[self.base_config.region]
            )
        
        except Exception as e:
            logger.error(f"Error in creating registration steps: {str(e)}")
            logger.error("Packaging step properties:")
            # Only show non-private properties
            logger.error(f"Available properties: {[p for p in dir(packaging_step.properties) if not p.startswith('_')]}")
            if hasattr(packaging_step.properties, 'ProcessingOutputConfig'):
                try:
                    logger.error(f"Output config expression: {packaging_step.properties.ProcessingOutputConfig.expr}")
                except:
                    logger.error("Could not access output config expression")
            raise


    def _get_pipeline_parameters(self) -> List[ParameterString]:
        """Get pipeline parameters"""
        return [
            PIPELINE_EXECUTION_TEMP_DIR,
            KMS_ENCRYPTION_KEY_PARAM,
            VPC_SUBNET,
            SECURITY_GROUP_ID,
        ]

    def validate_model_path(self, model_s3_path: str) -> None:
        """Validate the provided model S3 path."""
        if not model_s3_path.startswith('s3://'):
            raise ValueError(f"Invalid S3 path: {model_s3_path}. Must start with 's3://'")
        logger.info(f"Validated model S3 path: {model_s3_path}")

    def generate_pipeline(self, model_s3_path: str) -> Pipeline:
        """
        Create deployment pipeline using existing model.
        
        Args:
            model_s3_path: S3 path to the model artifacts
            
        Returns:
            SageMaker Pipeline instance
        """
        logger.info(f"Creating deployment pipeline: {self.base_config.pipeline_name}")
        
        # Validate model path
        self.validate_model_path(model_s3_path)

        # Create steps
        model_step = self._create_model_step(model_s3_path)
        packaging_step = self._create_packaging_step(model_step)
        registration_steps = self._create_registration_steps(packaging_step)

        # Combine all steps
        steps = [
            model_step,
            packaging_step,
            *registration_steps.values()
        ]

        # Create and return pipeline
        return Pipeline(
            name=self.base_config.pipeline_name,
            parameters=self._get_pipeline_parameters(),
            steps=steps,
            sagemaker_session=self.session
        )
```

>[!info]
>Note that since SAIS is in `us-east-1`, all model step and training step must be in `us-east-1`


-----------
##  Recommended Notes


- [[MLOps]]
- [[Continuous Delivery or CD in DevOps and MLOps]]
- [[Continuous Integration or CI in DevOps and MLOps]]
