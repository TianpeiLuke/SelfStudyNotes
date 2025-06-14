---
tags:
  - code
  - code_snippet
  - amazon/mods_pipeline
  - aws/sagemaker_pipeline
  - python/aws_python_sdk
keywords: 
topics: 
language: python
date of note: 2025-06-03
---

## Code Snippet Summary

>[!important]


## Code

### Import

```python
from typing import Dict, Optional, Any, List
from pathlib import Path
```


```python
from sagemaker.sklearn import SKLearnProcessor
from sagemaker.processing import ProcessingInput, ProcessingOutput
from sagemaker.workflow.steps import ProcessingStep
```


```python
import logging
logger = logging.getLogger(__name__)
```


```python
from .config_tabular_preprocessing_step import TabularPreprocessingConfig
from .builder_step_base import StepBuilderBase
```

- [[Config for Tabular Preprocessing Step]]

### Main

```python
class TabularPreprocessingStepBuilder(StepBuilderBase):
    """
    Builder for a Tabular Preprocessing ProcessingStep.
    This class is responsible for configuring and creating a SageMaker ProcessingStep
    that executes the tabular data preprocessing script. It handles the setup of
    the processor, inputs, outputs, and script arguments.
    """

    def __init__(
        self,
        config: TabularPreprocessingConfig,
        sagemaker_session=None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None,
    ):
        """
        Initializes the builder with a specific configuration for the preprocessing step.

        Args:
            config: A TabularPreprocessingConfig instance containing all necessary settings,
                    such as instance types, script paths, and hyperparameters.
            sagemaker_session: The SageMaker session object to manage interactions with AWS.
            role: The IAM role ARN to be used by the SageMaker Processing Job.
            notebook_root: The root directory of the notebook environment, used for resolving
                         local paths if necessary.
        """
        if not isinstance(config, TabularPreprocessingConfig):
            raise ValueError(
                "TabularPreprocessingStepBuilder requires a TabularPreprocessingConfig instance."
            )
        super().__init__(
            config=config,
            sagemaker_session=sagemaker_session,
            role=role,
            notebook_root=notebook_root
        )
        self.config: TabularPreprocessingConfig = config

    def validate_configuration(self) -> None:
        """
        Validates the provided configuration to ensure all required fields for this
        specific step are present and valid before attempting to build the step.

        Raises:
            ValueError: If any required configuration is missing or invalid.
        """
        logger.info("Validating TabularPreprocessingConfig…")
        if not self.config.hyperparameters.label_name:
            raise ValueError("hyperparameters.label_name must be provided and non‐empty")
        if not getattr(self.config, 'job_type', None):
            raise ValueError(
                "job_type must be provided (e.g. 'training','validation','testing')"
            )
        if "data_input" not in (self.config.input_names or {}):
            raise ValueError("input_names must contain key 'data_input'")
        
        # Ensures that the configuration specifies the name for the primary output channel.
        if "processed_data" not in (self.config.output_names or {}):
            raise ValueError(
                "output_names must contain the key 'processed_data'"
            )
        logger.info("TabularPreprocessingConfig validation succeeded.")

    def _get_environment_variables(self) -> Dict[str, str]:
        """
        Constructs a dictionary of environment variables to be passed to the processing job.
        These variables are used to control the behavior of the preprocessing script
        without needing to pass them as command-line arguments.

        Returns:
            A dictionary of environment variables.
        """
        env_vars = {
            "LABEL_FIELD": str(self.config.hyperparameters.label_name),
            "TRAIN_RATIO": str(self.config.train_ratio),
            "TEST_VAL_RATIO": str(self.config.test_val_ratio)
        }
        logger.info(f"Processing environment variables: {env_vars}")
        return env_vars

    def _create_processor(self) -> SKLearnProcessor:
        """
        Creates and configures the SKLearnProcessor for the SageMaker Processing Job.
        This defines the execution environment for the script, including the instance
        type, framework version, and environment variables.

        Returns:
            An instance of sagemaker.sklearn.SKLearnProcessor.
        """
        return SKLearnProcessor(
            framework_version=self.config.processing_framework_version,
            command=["python3"],
            role=self.role,
            instance_count=self.config.processing_instance_count,
            instance_type=self.config.get_instance_type(),
            volume_size_in_gb=self.config.processing_volume_size,
            base_job_name=self._sanitize_name_for_sagemaker(
                f"{self._get_step_name('Processing')}-{self.config.job_type}"
            ),
            sagemaker_session=self.session,
            env=self._get_environment_variables(),
        )

    def _get_processor_inputs(self, inputs: Dict[str, Any]) -> List[ProcessingInput]:
        """
        Constructs a list of ProcessingInput objects from the provided inputs dictionary.
        This defines the data channels for the processing job, mapping S3 locations
        to local directories inside the container.

        Args:
            inputs: A dictionary mapping logical input channel names (e.g., 'raw_data')
                    to their S3 URIs or dynamic Step properties.

        Returns:
            A list of sagemaker.processing.ProcessingInput objects.
        """
        key_in = self.config.input_names["data_input"]
        if not inputs or key_in not in inputs:
            raise ValueError(f"Must supply an S3 URI for '{key_in}' in 'inputs'")

        # Define the primary data input channel.
        processing_inputs = [
            ProcessingInput(
                input_name=key_in,
                source=inputs[key_in],
                destination="/opt/ml/processing/input/data"
            )
        ]
        return processing_inputs

    def _get_processor_outputs(self, outputs: Dict[str, Any]) -> List[ProcessingOutput]:
        """
        Constructs the single ProcessingOutput object needed for this step.
        This defines the S3 location where the results of the processing job will be stored.

        Args:
            outputs: A dictionary mapping the logical output channel name ('processed_data')
                     to its S3 destination URI.

        Returns:
            A list containing a single sagemaker.processing.ProcessingOutput object.
        """
        key_proc = self.config.output_names["processed_data"]
        if not outputs or key_proc not in outputs:
            raise ValueError(f"Must supply an S3 URI for '{key_proc}' in 'outputs'")
        
        # Define a single output. The script writes to subfolders (train, val, test)
        # inside the '/opt/ml/processing/output' directory. Setting this as the source
        # ensures all created subfolders are uploaded to the specified S3 destination.
        return [
            ProcessingOutput(
                output_name=key_proc,
                source="/opt/ml/processing/output",
                destination=outputs[key_proc]
            )
        ]

    def _get_job_arguments(self) -> List[str]:
        """
        Constructs the list of command-line arguments to be passed to the processing script.
        This allows for parameterizing the script's execution at runtime.

        Returns:
            A list of strings representing the command-line arguments (e.g., ['--job_type', 'training']).
        """
        return ["--job_type", self.config.job_type]

    def create_step(
        self,
        inputs: Optional[Dict[str, Any]] = None,
        outputs: Optional[Dict[str, Any]] = None,
        enable_caching: bool = True
    ) -> ProcessingStep:
        """
        Creates the final, fully configured SageMaker ProcessingStep for the pipeline.
        This method orchestrates the assembly of the processor, inputs, outputs, and
        script arguments into a single, executable pipeline step.

        Args:
            inputs: A dictionary mapping input channel names to their sources (S3 URIs or Step properties).
            outputs: A dictionary mapping output channel names to their S3 destinations.
            enable_caching: A boolean indicating whether to cache the results of this step
                            to speed up subsequent pipeline runs with the same inputs.

        Returns:
            A configured sagemaker.workflow.steps.ProcessingStep instance.
        """
        logger.info("Creating TabularPreprocessing ProcessingStep...")

        processor = self._create_processor()
        proc_inputs = self._get_processor_inputs(inputs)
        proc_outputs = self._get_processor_outputs(outputs)
        job_args = self._get_job_arguments()

        step_name = f"{self._get_step_name('Processing')}-{self.config.job_type.capitalize()}"
        
        processing_step = ProcessingStep(
            name=step_name,
            processor=processor,
            inputs=proc_inputs,
            outputs=proc_outputs,
            code=self.config.get_script_path(),
            job_arguments=job_args,
            cache_config=self._get_cache_config(enable_caching)
        )
        logger.info(f"Created ProcessingStep with name: {processing_step.name}")
        return processing_step

    def create_processing_step(
        self,
        inputs: Optional[Dict[str, Any]] = None,
        outputs: Optional[Dict[str, Any]] = None,
        enable_caching: bool = True
    ) -> ProcessingStep:
        """Backwards compatible method for creating processing step"""
        logger.warning("create_processing_step is deprecated, use create_step instead.")
        return self.create_step(inputs, outputs, enable_caching)

```


### Related Tasks

- [[Processor Risk Table Mapping]]
- [[Processor Binning]]

## Variants



## Previous Step

- [[MODS Cradle Data Loading Step Builder]]
- [[MODS Cradle Data Downloader]]

## Next Step

- [[Builder XGBoost Training Step]]




-----------
##  Recommended Notes


