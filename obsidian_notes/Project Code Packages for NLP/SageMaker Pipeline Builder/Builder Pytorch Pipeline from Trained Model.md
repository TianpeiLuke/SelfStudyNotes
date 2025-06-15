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
>In this code, we provide a **SageMaker Pipeline**
>- *after* the model has already *been trained offline*
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
- [[Builder Packaging Step]]
- [[Builder MODS Model Registration Step]]

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
class BSMPytorchPipelineBuilder:
    """
    Builder for model deployment pipeline without training.
    
    The MODS Pipeline consists of three sequentially connected steps
    1. Model Step: 
        - This step create the model object in SageMaker using a pretrained model.tar.gz
    2. Packaging Step
        - This step would unpack the model.tar.gz, inject source code locally and repack the model.tar.gz
    3. MIMS Model Registration Step
        - This step would register the model in MMS using MIMS
    """
    
    def __init__(
        self,
        config_path: str,
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None
    ):
        """Initialize pipeline builder."""
        logger.info(f"Loading configs from: {config_path}")
        self.configs = load_configs(config_path, CONFIG_CLASSES)
        
        # Extract and validate configs
        self._validate_and_extract_configs()
        
        self.session = sagemaker_session
        self.role = role
        self.notebook_root = notebook_root or Path.cwd()
        
        # for Execution Documentation
        self.registration_configs: Dict[str, Dict[str, Any]] = {}

        logger.info(f"Initialized PipelineBuilder for pipeline: {self.base_config.pipeline_name}")

    def _validate_and_extract_configs(self):
        """Extract and validate individual configs."""
        required_steps = ['Base', 'PytorchModel', 'Package', 'Registration', 'Payload']
        missing_steps = [step for step in required_steps if step not in self.configs]
        if missing_steps:
            raise ValueError(f"Missing required configurations for steps: {missing_steps}")

        self.base_config = self.configs['Base']
        self.model_config = self.configs['PytorchModel']
        self.package_config = self.configs['Package']
        self.registration_config = self.configs['Registration']
        self.payload_config = self.configs['Payload']

        # Validate config types
        if not isinstance(self.package_config, PackageStepConfig):
            raise TypeError(f"Expected PackageStepConfig, got {type(self.package_config)}")
        if not isinstance(self.registration_config, ModelRegistrationConfig):
            raise TypeError(f"Expected ModelRegistrationConfig, got {type(self.registration_config)}")

    def _create_model_step(self, model_s3_path: str):
        """Create model step using provided model S3 path."""
        logger.info(f"Creating model step with model from: {model_s3_path}")
        
        # Force the model region to be NA
        model_config_copy = self.model_config.model_copy()
        model_config_copy.region = 'NA'
        model_config_copy.aws_region = 'us-east-1'
        logger.info(f"Model aws region: {model_config_copy.aws_region}")

        model_builder = PytorchModelStepBuilder(
            config=model_config_copy,
            sagemaker_session=self.session,
            role=self.role
        )
        return model_builder.create_model_step(model_data=model_s3_path)

    def _create_packaging_step(self, model_step):
        """Create MIMS packaging step."""
        logger.info("Creating MIMS packaging step")
        
        # Ensure processing script exists
        script_path = self.package_config.get_script_path()
        if script_path:
            logger.info(f"Using packaging script: {script_path}")
        else:
            raise ValueError("No packaging script path found in config")

        packaging_builder = MIMSPackagingStepBuilder(
            config=self.package_config,
            sagemaker_session=self.session,
            role=self.role,
            notebook_root=self.notebook_root
        )
        
        return packaging_builder.create_packaging_step(
            model_data=model_step.model_artifacts_path,
            dependencies=[model_step]
        )

    def _create_registration_steps(self, packaging_step: ProcessingStep) -> Dict[str, ProcessingStep]:
        """Create model registration steps and store execution configs."""
        logger.info("Creating registration steps")
        
        # Generate and upload payloads first
        logger.info("Generating and uploading payloads")
        try:
            self.payload_config.generate_and_upload_payloads()
        except Exception as e:
            logger.error(f"Failed to generate/upload payloads: {str(e)}")
            raise

        # Get inference image URI
        try:
            source_model_inference_image_arn = retrieve(
                framework="pytorch",
                region=self.model_config.aws_region,
                version=self.model_config.framework_version,
                py_version=self.model_config.py_version,
                instance_type=self.model_config.inference_instance_type,
                image_scope="inference"
            )
        except Exception as e:
            logger.error(f"Failed to retrieve inference image URI: {str(e)}")
            raise RuntimeError(f"Failed to retrieve inference image URI: {str(e)}") from e

        # Create execution config
        execution_doc_config = {
            "model_domain": self.payload_config.model_registration_domain,
            "model_objective": self.payload_config.model_registration_objective,
            "source_model_inference_content_types": self.payload_config.source_model_inference_content_types,
            "source_model_inference_response_types": self.payload_config.source_model_inference_response_types,
            "source_model_inference_input_variable_list": self.payload_config.source_model_inference_input_variable_list,
            "source_model_inference_output_variable_list": self.payload_config.source_model_inference_output_variable_list,
            "model_registration_region": self.payload_config.region,
            "source_model_inference_image_arn": source_model_inference_image_arn,
            "source_model_region": self.payload_config.aws_region,
            "model_owner": self.payload_config.model_owner,
            "source_model_environment_variable_map": {
                "SAGEMAKER_CONTAINER_LOG_LEVEL": "20",
                "SAGEMAKER_PROGRAM": self.model_config.inference_entry_point,
                "SAGEMAKER_REGION": self.payload_config.aws_region,
                "SAGEMAKER_SUBMIT_DIRECTORY": '/opt/ml/model/code',
            },
            'load_testing_info_map': {
                "sample_payload_s3_bucket": self.payload_config.bucket,
                "sample_payload_s3_key": self.payload_config.sample_payload_s3_key,
                "expected_tps": self.payload_config.expected_tps,
                "max_latency_in_millisecond": self.payload_config.max_latency_in_millisecond,
                "instance_type_list": [self.package_config.get_instance_type()],
                "max_acceptable_error_rate": self.payload_config.max_acceptable_error_rate,
            },
        }

        registration_builder = ModelRegistrationStepBuilder(
            config=self.registration_config,
            sagemaker_session=self.session,
            role=self.role
        )

        try:
            outputs = packaging_step.properties.ProcessingOutputConfig.Outputs
            s3_uri = outputs[0].S3Output.S3Uri
            logger.info(f"Using output expression: {outputs[0].expr}")

            # Create registration steps and get result
            result = registration_builder.create_step(
                packaging_step_output=s3_uri,
                payload_s3_key=self.payload_config.sample_payload_s3_key,
                dependencies=[packaging_step],
                regions=[self.base_config.region]
            )

            # Store config using actual step name(s)
            if isinstance(result, dict):
                for step in result.values():
                    self.registration_configs[step.name] = execution_doc_config
                return list(result.values())
            else:
                self.registration_configs[result.name] = execution_doc_config
                return [result]

        except Exception as e:
            logger.error(f"Error in creating registration steps: {str(e)}")
            logger.error("Available packaging step outputs:")
            for output in outputs:
                logger.error(f"- {output.OutputName}: {output.S3Output.S3Uri}")
            raise RuntimeError(f"Failed to create registration steps: {str(e)}") from e

    def _get_pipeline_parameters(self) -> List[ParameterString]:
        """Get pipeline parameters."""
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
        if not model_s3_path.endswith('.tar.gz'):
            logger.warning(f"Model path {model_s3_path} does not end with .tar.gz")
        logger.info(f"Validated model S3 path: {model_s3_path}")

    def generate_pipeline(self, model_s3_path: str) -> Pipeline:
        """Create deployment pipeline using existing model."""
        logger.info(f"Creating deployment pipeline: {self.base_config.pipeline_name}")
        
        self.validate_model_path(model_s3_path)

        try:
            # Create steps
            model_step = self._create_model_step(model_s3_path)
            packaging_step = self._create_packaging_step(model_step)
            registration_steps = self._create_registration_steps(packaging_step)

            # Combine all steps
            steps = [
                model_step,
                packaging_step,
                *registration_steps  # Unpack the list of registration steps
            ]

            # Create pipeline
            return Pipeline(
                name=self.base_config.pipeline_name,
                parameters=self._get_pipeline_parameters(),
                steps=steps,
                sagemaker_session=self.session
            )

        except Exception as e:
            logger.error(f"Failed to generate pipeline: {str(e)}")
            raise

    def fill_execution_document(self, execution_document: Dict[str, Any]) -> Dict[str, Any]:
        """
        Fill in the execution document with model registration configurations.

        Args:
            execution_document (Dict[str, Any]): The execution document to be filled.

        Returns:
            Dict[str, Any]: The updated execution document.

        Raises:
            ValueError: If pipeline hasn't been generated yet (no stored configs)
            KeyError: If execution document doesn't have expected structure
        """
        if not self.registration_configs:
            raise ValueError(
                "No registration configs found. "
                "Make sure to call generate_pipeline() before fill_execution_document()"
            )

        if "PIPELINE_STEP_CONFIGS" not in execution_document:
            raise KeyError("Execution document missing 'PIPELINE_STEP_CONFIGS' key")

        pipeline_configs = execution_document["PIPELINE_STEP_CONFIGS"]
        
        for step_name, config in self.registration_configs.items():
            if step_name not in pipeline_configs:
                logger.warning(f"Registration step '{step_name}' not found in execution document")
                continue
            
            if "STEP_CONFIG" not in pipeline_configs[step_name]:
                pipeline_configs[step_name]["STEP_CONFIG"] = {}
            
            pipeline_configs[step_name]["STEP_CONFIG"] = config
            logger.info(f"Updated execution config for registration step: {step_name}")

        return execution_document
```

>[!info]
>Note that since SAIS is in `us-east-1`, all model step and training step must be in `us-east-1`


-----------
##  Recommended Notes

- [[MODS Pytorch Pipeline Builder with Existing Model File]]

- [[MLOps]]
- [[Continuous Delivery or CD in DevOps and MLOps]]
- [[Continuous Integration or CI in DevOps and MLOps]]
