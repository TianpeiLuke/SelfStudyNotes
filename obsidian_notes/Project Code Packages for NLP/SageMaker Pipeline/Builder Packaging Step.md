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
        Initialize PyTorch model builder
        
        Args:
            config: Pydantic ModelConfig instance with hyperparameters
            sagemaker_session: SageMaker session
            role: IAM role ARN
            notebook_root: Root directory of notebook
        """
        super().__init__(config, sagemaker_session, role, notebook_root)
        

    def _resolve_local_or_s3_path(self, configured_path: str, is_dir_check: bool = False) -> str:
        """Resolves a path from config. If local, prepends notebook_root. Returns str."""
        if str(configured_path).startswith('s3://'):
            logger.info(f"Using S3 path from config: {configured_path}")
            return str(configured_path)
        
        resolved_local_path = (self.notebook_root / configured_path).resolve()
        target_type_str = "directory" if is_dir_check else "file"
        exists_check = resolved_local_path.is_dir if is_dir_check else resolved_local_path.is_file
        
        if not exists_check():
            raise FileNotFoundError(
                f"Local {target_type_str} '{configured_path}' (resolved to '{resolved_local_path}') "
                "specified in config not found."
            )
        logger.info(f"Using resolved local {target_type_str} from config: {resolved_local_path}")
        return str(resolved_local_path)


    def _get_resolved_script_entry_point_for_processor(self) -> str:
        """
        Determines the absolute local path to the packaging entry point script.
        """
        if not self.config.source_dir: # from BasePipelineConfig part of PackageStepConfig
            raise ValueError("PackageStepConfig.source_dir must be set to locate the packaging_entry_point.")
        if str(self.config.source_dir).startswith('s3://'):
            raise ValueError(
                "For MIMSPackagingStepBuilder, 'source_dir' containing the 'packaging_entry_point' "
                "is expected to be a local path. S3 source_dir for the main script is not directly supported "
                "by this builder's current SKLearnProcessor setup for the 'code' argument."
            )

        full_local_script_path = (self.notebook_root / self.config.source_dir / self.config.packaging_entry_point).resolve()
        if not full_local_script_path.is_file():
            raise FileNotFoundError(
                f"Packaging entry point script '{self.config.packaging_entry_point}' "
                f"not found within local source_dir '{self.config.source_dir}'. "
                f"Looked at: {full_local_script_path}"
            )
        logger.info(f"Resolved packaging script entry point for processor: {full_local_script_path}")
        return str(full_local_script_path)


    def validate_configuration(self) -> None:
        """Validate required configuration settings for MIMS packaging."""
        logger.info(f"Running {self.__class__.__name__} specific configuration validation.")
        # Attributes from PackageStepConfig or its bases (ProcessingStepConfigBase, BasePipelineConfig)
        required_attrs = [
            'source_dir', 'packaging_entry_point', 'inference_scripts_input_path',
            'processing_instance_count', 'processing_volume_size',
            'pipeline_name', 'pipeline_s3_loc'
        ]
        if self.config.use_large_processing_instance: # Check which instance type is expected
            required_attrs.append('processing_instance_type_large')
        else:
            required_attrs.append('processing_instance_type_small')

        for attr in required_attrs:
            if not hasattr(self.config, attr) or getattr(self.config, attr) is None:
                raise ValueError(f"PackageStepConfig missing required attribute: {attr}")

        try:
            self._get_resolved_script_entry_point_for_processor() # Validates main packaging script
            # Validate inference_scripts_input_path (existence checked by _resolve_local_or_s3_path if local)
            self._resolve_local_or_s3_path(self.config.inference_scripts_input_path, is_dir_check=True)
        except FileNotFoundError as e:
            raise ValueError(f"Configuration error for script/source paths: {e}")
        logger.info("MIMS Packaging configuration paths validated.")


    def _create_processor(self) -> SKLearnProcessor:
        """Create SKLearn processor for MIMS packaging."""
        if self.config.use_large_processing_instance:
            instance_type = self.config.processing_instance_type_large
        else:
            instance_type = self.config.processing_instance_type_small
        logger.info(f"Using processing instance type for packaging: {instance_type}")

        base_job_name_prefix = self._sanitize_name_for_sagemaker(self.config.pipeline_name, 30)

        return SKLearnProcessor(
            framework_version="1.2-1",
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
        Defines the list of ProcessingInput objects for the MIMS packaging step.
        """
        # Resolve the path for inference scripts (this will be S3 URI or absolute local path)
        resolved_inference_scripts_path = self._resolve_local_or_s3_path(
            self.config.inference_scripts_input_path,
            is_dir_check=True
        )

        inputs = [
            ProcessingInput(
                source=model_artifacts_input_source,
                destination="/opt/ml/processing/input/model", # Corresponds to MODEL_PATH in mims_package.py
                input_name=self.config.model_input_name_in_job
            ),
            ProcessingInput(
                source=resolved_inference_scripts_path,
                destination="/opt/ml/processing/input/script", # Corresponds to SCRIPT_PATH in mims_package.py
                input_name=self.config.inference_scripts_input_name_in_job
            ),
        ]
        logger.info(f"Processing inputs defined: {inputs}")
        return inputs


    def _get_processing_outputs(self, step_name_for_s3_path: str) -> List[ProcessingOutput]:
        """
        Defines the list of ProcessingOutput objects for the MIMS packaging step.
        """
        # The mims_package.py script writes to /opt/ml/processing/output/model.tar.gz
        # So, the source for ProcessingOutput is the directory /opt/ml/processing/output
        output_s3_destination = os.path.join(
            self.config.pipeline_s3_loc,
            step_name_for_s3_path, # Use the actual step name for better S3 organization
            "packaged_model_artifacts" # Descriptive subfolder
        )

        outputs = [
            ProcessingOutput(
                output_name=self.config.packaged_model_output_name_from_job,
                source="/opt/ml/processing/output",
                destination=output_s3_destination
            )
        ]
        logger.info(f"Processing outputs defined: {outputs}")
        return outputs


    def create_step(
        self,
        model_artifacts_input_source: Union[str, Properties],
        # common_artifacts_source removed as mims_package.py doesn't seem to use a third distinct input like that
        dependencies: Optional[List[Step]] = None
    ) -> ProcessingStep:
        """
        Creates a ProcessingStep for MIMS model packaging.
        Args:
            model_artifacts_input_source: S3 URI (str) or Properties object from a previous step
                                          pointing to the primary model artifacts.
            dependencies: Optional list of SageMaker Pipeline steps that this step depends on.
        Returns:
            A SageMaker ProcessingStep instance.
        """
        # self.validate_configuration() # Called by super().__init__

        step_name = self._get_step_name('Package') # Uses 'PackagingStep' from STEP_NAMES

        packaging_script_local_path = self._get_resolved_script_entry_point_for_processor()

        logger.info(f"Defining {step_name}:")
        logger.info(f"  Packaging Script (processor code arg): {packaging_script_local_path}")

        processor = self._create_processor()
        processing_inputs = self._get_processing_inputs(model_artifacts_input_source)
        processing_outputs = self._get_processing_outputs(step_name) # Pass step_name for S3 path
        
        job_arguments = self.config.packaging_script_arguments

        return ProcessingStep(
            name=step_name,
            processor=processor,
            inputs=processing_inputs,
            outputs=processing_outputs,
            code=packaging_script_local_path, # Absolute local path to the entry script
            job_arguments=job_arguments,
            depends_on=dependencies or [],
            cache_config=self._get_cache_config(getattr(self.config, 'enable_caching_package_step', True))
        )

    # Maintain backwards compatibilityity
    def create_packaging_step(
        self,
        model_data: str,
        dependencies: Optional[List] = None
    ) -> ProcessingStep:
        """Backwards compatible method for creating packaging step"""
        return self.create_step(model_data, dependencies)
```

- [[Script for Model and Code Packaging]]
- [[Base Step Builder]]
- [[Config for Training Step]]


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



## Next Step

- [[MIMS Model Registration Step Builder]]



-----------
##  Recommended Notes

