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
date of note: 2025-05-22
---

## Code Snippet Summary

>[!important]


## Code

```python
from typing import Dict, Optional, List, Union # Added Union
from pathlib import Path
import logging

from sagemaker.workflow.pipeline_context import PipelineSession
from sagemaker.workflow.steps import ProcessingStep, Step
from sagemaker.processing import ProcessingInput, ProcessingOutput
from sagemaker.sklearn import SKLearnProcessor
from sagemaker.workflow.properties import Properties # For type hinting sources

logger = logging.getLogger(__name__)

```

### Import Config and Base

```python
from .builder_step_base import StepBuilderBase
from .workflow_config import ModelConfig
```

### Builder

```python
class PayloadGenerationStepBuilder(StepBuilderBase):
    """Builds a SageMaker Pipeline ProcessingStep for payload generation."""

    def __init__(
        self,
        config: ModelConfig,
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None
    ):
        super().__init__(config, sagemaker_session, role, notebook_root)

    def validate_configuration(self) -> None:
        """Validate specific configuration requirements for payload generation."""
        logger.info(f"Running PayloadGenerationStepBuilder specific configuration validation.")
        required_attrs = [
            'payload_script_path', # e.g., "scripts/create_payload.py" relative to notebook_root or absolute
            'processing_instance_type_small',
            'processing_instance_count',
            'processing_volume_size'
        ]
        for attr in required_attrs:
            if not hasattr(self.config, attr) or getattr(self.config, attr) is None:
                raise ValueError(f"ModelConfig missing required attribute for payload generation: {attr}")
        
        # Validate script path if it's meant to be a local file
        if isinstance(self.config.payload_script_path, str) and not self.config.payload_script_path.startswith('s3://'):
            script_full_path = self.notebook_root / self.config.payload_script_path
            if not script_full_path.exists() or not script_full_path.is_file():
                raise FileNotFoundError(f"Payload script not found at resolved path: {script_full_path}")


    def create_step(self,
                    artifacts_source: Union[str, Properties],
                    dependencies: Optional[List[Step]] = None) -> ProcessingStep:
        """
        Creates a ProcessingStep for payload generation.

        Args:
            artifacts_source: S3 URI (str) or Properties object from a previous step
                              pointing to the input artifacts.
            dependencies: Optional list of SageMaker Pipeline steps that this step depends on.

        Returns:
            A SageMaker ProcessingStep instance.
        """
        step_name = self._get_step_name('Payload') # Uses 'PayloadGenerationStep' from STEP_NAMES

        logger.info(f"Defining {step_name} using script: {self.config.payload_script_path}")
        logger.info(f"  Input artifacts source: {artifacts_source}")

        # Determine if the script path is S3 or local
        code_location = self.config.payload_script_path
        if not str(code_location).startswith('s3://'):
            # If it's a relative path, make it absolute based on notebook_root
            # The SKLearnProcessor will handle uploading from this local path
            code_location = str((self.notebook_root / code_location).resolve())
            logger.info(f"  Resolved local script path to: {code_location}")


        sklearn_processor = SKLearnProcessor(
            framework_version="1.2-1", # Consider making this configurable via ModelConfig
            role=self.role, # Use the role passed to the builder
            instance_type=self.config.processing_instance_type_small,
            instance_count=self.config.payload_processing_instance_count,
            volume_size_in_gb=self.config.payload_processing_volume_size,
            sagemaker_session=self.session, # This is a PipelineSession
            # base_job_name can be added here for better job naming in AWS console
            base_job_name=f"{self._sanitize_name_for_sagemaker(self.config.pipeline_name, 30)}-payload-gen"
        )

        processing_inputs = [
            ProcessingInput(
                source=artifacts_source,
                destination="/opt/ml/processing/input/artifacts", # Container path
                input_name="artifacts"
            )
        ]

        processing_outputs = [
            ProcessingOutput(
                output_name="payload_output", # This name is referenced in ProcessingOutputConfig.Outputs
                source="/opt/ml/processing/mims_payload", # Source path inside the container
                # destination will be an S3 path auto-generated by SageMaker
            )
        ]
        
        # Add job arguments if your create_payload.py script expects them
        job_arguments = getattr(self.config, 'payload_script_arguments', None) # e.g., ["--verbose"]

        return ProcessingStep(
            name=step_name,
            processor=sklearn_processor,
            inputs=processing_inputs,
            outputs=processing_outputs,
            code=code_location, # Path to your create_payload.py script
            job_arguments=job_arguments,
            depends_on=dependencies or [],
            cache_config=self._get_cache_config() # Using cache config from base
        )
```

- [[Config for Pytorch Training Step]]
- [[Base Step Builder]]


## Next Step

- [[Builder MODS Model Registration Step]]


-----------
##  Recommended Notes


- [[MLOps]]
- [[Continuous Delivery or CD in DevOps and MLOps]]
- [[Continuous Integration or CI in DevOps and MLOps]]
