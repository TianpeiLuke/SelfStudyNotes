---
tags:
  - code
  - code_snippet
  - python/aws_python_sdk
  - aws/step_function
  - aws/sagemaker_pipeline
keywords: 
topics: 
language: python
date of note: 2025-05-21
---

## Code Snippet Summary

>[!important]
>Builder for **Packaging**
>- return `ProcessingStep`
>- use `SKLearnProcessor`
>- execute script `mims_package.py`

- [[Script for Model and Code Packaging]]

## Code

```python
from typing import Optional, List, Union
from pathlib import Path
import os

from sagemaker.processing import ProcessingInput, ProcessingOutput
from sagemaker.sklearn import SKLearnProcessor
from sagemaker.workflow.steps import ProcessingStep, Step
from sagemaker.workflow.pipeline_context import PipelineSession
from sagemaker.workflow.properties import Properties
```


```python
import logging
logger = logging.getLogger(__name__)
```

### Import  Package Config and Base Model

```python
from .config_mims_packaging_step import PackageStepConfig
from .builder_step_base import StepBuilderBase
```

- [[Config for Packaging Step]]
- [[Base Step Builder]]

### Script

- Put `mims_package.py` in the root of `source_dir`
	- [[Script for Model and Code Packaging]]

### Builder

```python
class MIMSPackagingStepBuilder(StepBuilderBase):
    """Builder for MIMS packaging processing step"""

    def __init__(
        self, 
        config: PackageStepConfig, 
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None
    ):
        """
        Initialize MIMS packaging step builder
        
        Args:
            config: PackageStepConfig instance with configuration parameters
            sagemaker_session: SageMaker session
            role: IAM role ARN
            notebook_root: Root directory of notebook
        """
        super().__init__(config, sagemaker_session, role, notebook_root)

    def validate_configuration(self) -> None:
        """Validate required configuration settings for MIMS packaging."""
        logger.info(f"Running {self.__class__.__name__} specific configuration validation.")
        
        required_attrs = [
            'processing_entry_point',
            'processing_instance_count', 
            'processing_volume_size',
            'pipeline_name', 
            'pipeline_s3_loc'
        ]
        
        # Check for either processing_source_dir or source_dir
        if not (hasattr(self.config, 'processing_source_dir') and self.config.processing_source_dir) and \
           not (hasattr(self.config, 'source_dir') and self.config.source_dir):
            raise ValueError("Either processing_source_dir or source_dir must be set.")

        # Validate instance types
        if getattr(self.config, 'use_large_processing_instance', False):
            required_attrs.append('processing_instance_type_large')
        else:
            required_attrs.append('processing_instance_type_small')

        # Validate required attributes
        for attr in required_attrs:
            if not hasattr(self.config, attr) or getattr(self.config, attr) in [None, ""]:
                raise ValueError(f"PackageStepConfig missing required attribute for builder: {attr}")

        # Validate input/output names
        input_names = self.config.get_input_names()
        output_names = self.config.get_output_names()
        
        if "model_input" not in input_names or "inference_scripts_input" not in input_names:
            raise ValueError("Required input names 'model_input' and 'inference_scripts_input' must be defined")
        
        if "packaged_model_output" not in output_names:
            raise ValueError("Required output name 'packaged_model_output' must be defined")

        logger.info(f"{self.__class__.__name__} configuration attributes presence check passed.")

    def _create_processor(self) -> SKLearnProcessor:
        """Create SKLearn processor for MIMS packaging."""
        instance_type = self.config.get_instance_type(
            'large' if self.config.use_large_processing_instance else 'small'
        )
        logger.info(f"Using processing instance type for packaging: {instance_type}")

        base_job_name_prefix = self._sanitize_name_for_sagemaker(self.config.pipeline_name, 30)

        return SKLearnProcessor(
            framework_version=self.config.processing_framework_version,
            role=self.role,
            instance_type=instance_type,
            instance_count=self.config.processing_instance_count,
            volume_size_in_gb=self.config.processing_volume_size,
            sagemaker_session=self.session,
            base_job_name=f"{base_job_name_prefix}-mims-pkg"
        )

    def _get_processing_inputs(
        self, 
        model_artifacts_input_source: Union[str, Properties]
    ) -> List[ProcessingInput]:
        """
        Define processing inputs for the packaging step.
        
        Args:
            model_artifacts_input_source: Source location of model artifacts
            
        Returns:
            List of ProcessingInput objects
        """
        inference_source_dir = self.config.source_dir
        input_names = self.config.get_input_names()
        
        inputs = [
            ProcessingInput(
                source=model_artifacts_input_source,
                destination="/opt/ml/processing/input/model",
                input_name=input_names["model_input"]
            ),
            ProcessingInput(
                source=inference_source_dir,
                destination="/opt/ml/processing/input/script",
                input_name=input_names["inference_scripts_input"]
            )
        ]
        #logger.info(f"Processing inputs: {[str(i.source) for i in inputs]}")
        safe_sources = [
            i.source.expr if hasattr(i.source, 'expr') else str(i.source) 
            for i in inputs
        ]
        logger.info(f"Processing inputs: {safe_sources}")
        return inputs

    def _get_processing_outputs(self, step_name_for_s3_path: str) -> List[ProcessingOutput]:
        """
        Define processing outputs for the packaging step.
        
        Args:
            step_name_for_s3_path: Step name for constructing S3 path
            
        Returns:
            List of ProcessingOutput objects
        """
        output_names = self.config.get_output_names()
        
        output_s3_destination = os.path.join(
            str(self.config.pipeline_s3_loc).rstrip('/'),
            step_name_for_s3_path,
            "packaged_model_artifacts"
        )

        outputs = [
            ProcessingOutput(
                output_name=output_names["packaged_model_output"],
                source="/opt/ml/processing/output",
                destination=output_s3_destination
            )
        ]
        logger.info(f"Processing outputs defined: {outputs}")
        return outputs

    def _get_cache_config(self, enable_caching: bool = True) -> Optional[CacheConfig]:
        """
        Get cache configuration for the step.
        
        Args:
            enable_caching: Whether to enable caching
            
        Returns:
            CacheConfig object or None
        """
        if not enable_caching:
            return None
        
        expire_after = "30d"  # Cache expires after 30 days

        return CacheConfig(
            enable_caching=enable_caching,
            expire_after=expire_after
        )

    def create_step(
        self,
        model_artifacts_input_source: Union[str, Properties],
        dependencies: Optional[List[Step]] = None
    ) -> ProcessingStep:
        """
        Creates a ProcessingStep for MIMS model packaging.
        
        Args:
            model_artifacts_input_source: Source location of model artifacts
            dependencies: Optional list of step dependencies
            
        Returns:
            ProcessingStep object
        """
        step_name = self._get_step_name('Package')

        effective_source_dir = self.config.get_effective_source_dir()
        
        if str(effective_source_dir).startswith('s3://'):
            main_processing_script_uri = f"{effective_source_dir.rstrip('/')}/{self.config.processing_entry_point}"
            logger.warning(
                f"SKLearnProcessor 'code' argument is an S3 URI: {main_processing_script_uri}. "
                f"Ensure processor supports this for non-tar.gz S3 scripts or it's a tar.gz."
            )
        else:
            main_processing_script_uri = str(Path(effective_source_dir) / self.config.processing_entry_point)
        
        logger.info(f"Defining {step_name} with main script: {main_processing_script_uri}")

        processor = self._create_processor()
        processing_inputs = self._get_processing_inputs(model_artifacts_input_source)
        processing_outputs = self._get_processing_outputs(step_name)
        job_arguments = self.config.processing_script_arguments
        cache_config = self._get_cache_config(
            getattr(self.config, 'enable_caching_package_step', True)
        )

        return ProcessingStep(
            name=step_name,
            processor=processor,
            inputs=processing_inputs,
            outputs=processing_outputs,
            code=main_processing_script_uri,
            job_arguments=job_arguments,
            depends_on=dependencies or [],
            cache_config=cache_config
        )

    def create_packaging_step(
        self,
        model_data: str,
        dependencies: Optional[List] = None
    ) -> ProcessingStep:
        """
        Backwards compatible method for creating packaging step.
        
        Args:
            model_data: Location of model data
            dependencies: Optional list of step dependencies
            
        Returns:
            ProcessingStep object
        """
        return self.create_step(model_data, dependencies)

```

- [[Script for Model and Code Packaging]]
- [[Base Step Builder]]



### Learning: ProcessingStep

```python
ProcessingStep(
            name=step_name,
            processor=processor,
            inputs=processing_inputs,
            outputs=processing_outputs,
            code=packaging_script_local_path, # Absolute local path to the entry script
            job_arguments=job_arguments,
            depends_on=dependencies or [],
            cache_config=self._get_cache_config(getattr(self.config, 'enable_caching_package_step', True))
        )
```


- `sagemaker.workflow.steps.ProcessingStep`
	- [reference](https://sagemaker.readthedocs.io/en/stable/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.ProcessingStep)
	- `ProcessingStep` for SageMaker Pipelines Workflows.
		- Construct a `ProcessingStep`, given a Processor instance.
		- In addition to the Processor instance, the other arguments are those that are supplied to the process method of the `sagemaker.processing.Processor`.
	- **name** ([_str_](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the ProcessingStep.
	- **step_args** (JobStepArguments) 
		- The arguments for the ProcessingStep definition.
	- **processor** ([_Processor_](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.Processor "sagemaker.processing.Processor")) 
		- A `sagemaker.processing.Processor` instance.
	- **inputs** (List\[ [ProcessingInput](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingInput "sagemaker.processing.ProcessingInput") \]) 
		- A list of `sagemaker.processing.ProcessorInput` instances. Defaults to None.
	- **outputs** (List\[ [ProcessingOutput](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingOutput "sagemaker.processing.ProcessingOutput") \]) 
		- A list of `sagemaker.processing.ProcessorOutput` instances. 
		- Defaults to None.
	- **code** ([_str_](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) 
		- This can be an S3 URI or a local path to a file with the framework script to run. 
		- Defaults to None.
	- **cache_config** ([_CacheConfig_](https://sagemaker.readthedocs.io/en/stable/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.CacheConfig "sagemaker.workflow.steps.CacheConfig"))
		- A `sagemaker.workflow.steps.CacheConfig` instance.
	- **job_arguments** (List[str])
		- A list of strings to be passed into the processing job. Defaults to None.
	- **depends_on**
		- A list of `Step`/`StepCollection` names or `Step` instances or `StepCollection` instances that this `ProcessingStep` depends on.

### Learning: SKLearnProcessor




## Previous Step

- [[Builder Pytorch Training Step]]
- [[Builder XGBoost Training Step]]


## Next Step

- [[Builder MODS Model Registration Step]]



-----------
##  Recommended Notes

