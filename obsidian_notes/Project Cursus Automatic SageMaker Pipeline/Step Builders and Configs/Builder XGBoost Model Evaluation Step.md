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
>Model Evaluation step
>- Load Trained Model `model.tar.gz`
>- Evaluation on calibration dataset
>- Make Inference 
>- Compute AUC-ROC, Precision-Recall
>- Plot ROC, PR curve
>- Save prediction outcome, and PR, ROC curve


## Code

```python
from typing import Dict, Optional, Any, List
from pathlib import Path
```

```python
from sagemaker.processing import ProcessingInput, ProcessingOutput
from sagemaker.xgboost import XGBoostProcessor
from sagemaker.workflow.steps import ProcessingStep, Step
from sagemaker.workflow.pipeline_context import PipelineSession
from sagemaker.workflow.properties import Properties
from sagemaker.workflow.steps import CacheConfig
```



```python
import logging
logger = logging.getLogger(__name__)
```


```python
from .config_model_eval_step_xgboost import XGBoostModelEvalConfig
from .builder_step_base import StepBuilderBase

```

- [[Base Step Builder]]
- [[Config for XGBoost Model Evaluation Step]]

```python
class XGBoostModelEvalStepBuilder(StepBuilderBase):
    """
    Builder for XGBoost model evaluation ProcessingStep.
    """

    def __init__(
        self,
        config: XGBoostModelEvalConfig,
        sagemaker_session=None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None,
    ):
        if not isinstance(config, XGBoostModelEvalConfig):
            raise ValueError("XGBoostModelEvalStepBuilder requires a XGBoostModelEvalConfig instance.")
        super().__init__(
            config=config,
            sagemaker_session=sagemaker_session,
            role=role,
            notebook_root=notebook_root
        )
        self.config: XGBoostModelEvalConfig = config

    def validate_configuration(self) -> None:
        logger.info(f"Running {self.__class__.__name__} specific configuration validation.")
        
        required_attrs = [
            'processing_entry_point',
            'processing_source_dir',
            'processing_instance_count', 
            'processing_volume_size',
            'pipeline_name',
            'job_type',
            'hyperparameters',
            'xgboost_framework_version'
        ]
        
        for attr in required_attrs:
            if not hasattr(self.config, attr) or getattr(self.config, attr) in [None, ""]:
                raise ValueError(f"XGBoostModelEvalConfig missing required attribute: {attr}")

        input_names = self.config.get_input_names()
        output_names = self.config.get_output_names()
        
        required_inputs = {"model_input", "eval_data_input"} #, "code_input"}
        required_outputs = {"eval_output", "metrics_output"}
        
        if not all(name in input_names for name in required_inputs):
            raise ValueError(f"Required input names {required_inputs} must be defined")
        
        if not all(name in output_names for name in required_outputs):
            raise ValueError(f"Required output names {required_outputs} must be defined")

        logger.info(f"{self.__class__.__name__} configuration validation passed.")
        
    def _get_environment_variables(self) -> Dict[str, str]:
        env_vars = {
            "ID_FIELD": str(self.config.hyperparameters.id_name),
            "LABEL_FIELD": str(self.config.hyperparameters.label_name),
        }
        logger.info(f"Evaluation environment variables: {env_vars}")
        return env_vars

    def _create_processor(self) -> XGBoostProcessor:
        """Create XGBoost processor for model evaluation."""
        instance_type = self.config.get_instance_type(
            'large' if self.config.use_large_processing_instance else 'small'
        )
        logger.info(f"Using processing instance type for evaluation: {instance_type}")

        base_job_name_prefix = self._sanitize_name_for_sagemaker(self.config.pipeline_name, 30)
        
        # Create a command that will run the entry point from within the package
        # Construct the command to run the entry point script from the source directory

        return XGBoostProcessor(
            framework_version=self.config.xgboost_framework_version,
            role=self.role,
            instance_type=instance_type,
            instance_count=self.config.processing_instance_count,
            volume_size_in_gb=self.config.processing_volume_size,
            sagemaker_session=self.session,
            base_job_name=f"{base_job_name_prefix}-xgb-eval",
            env=self._get_environment_variables(),
        )

    def _get_processing_inputs(self, inputs: Dict[str, Any]) -> List[ProcessingInput]:
        required_inputs = self.config.INPUT_CHANNELS.keys()
        
        if not inputs or not all(k in inputs for k in required_inputs):
            raise ValueError(f"Must supply S3 URIs for all required inputs: {required_inputs}")

        input_destinations = {
            "model_input": "/opt/ml/processing/input/model",
            "eval_data_input": "/opt/ml/processing/input/eval_data",
            #"code_input": "/opt/ml/processing/input/sourcecode"
        }

        return [
            ProcessingInput(
                input_name=channel_name,
                source=inputs[channel_name],
                destination=input_destinations[channel_name]
            )
            for channel_name in required_inputs
        ]

    def _get_processing_outputs(self, outputs: Dict[str, Any]) -> List[ProcessingOutput]:
        required_outputs = self.config.OUTPUT_CHANNELS.keys()
        
        if not outputs or not all(k in outputs for k in required_outputs):
            raise ValueError(f"Must supply S3 URIs for all required outputs: {required_outputs}")

        output_sources = {
            "eval_output": "/opt/ml/processing/output/eval",
            "metrics_output": "/opt/ml/processing/output/metrics"
        }

        return [
            ProcessingOutput(
                output_name=channel_name,
                source=output_sources[channel_name],
                destination=outputs[channel_name]
            )
            for channel_name in required_outputs
        ]

    def _get_job_arguments(self) -> List[str]:
        return ["--job_type", self.config.job_type]
    
    def _get_cache_config(self, enable_caching: bool = True) -> Optional[CacheConfig]:
        if not enable_caching:
            return None
        return CacheConfig(
            enable_caching=enable_caching,
            expire_after="30d"
        )

    def create_step(
        self,
        inputs: Dict[str, Any],
        outputs: Dict[str, Any],
        dependencies: Optional[List[Step]] = None,
        enable_caching: bool = True
    ) -> ProcessingStep:
        logger.info("Creating XGBoost Model Evaluation ProcessingStep...")

        processor = self._create_processor()
        proc_inputs = self._get_processing_inputs(inputs)
        proc_outputs = self._get_processing_outputs(outputs)
        job_args = self._get_job_arguments()

        # FIX: The processor's `.run()` method is called to correctly package the code,
        # entrypoint, and dependencies. The output of this call (`step_args`) is then passed
        # to the ProcessingStep.
        step_args = processor.run(
            code=self.config.processing_entry_point, #self.config.get_script_path(),
            source_dir=self.config.processing_source_dir, # This is the crucial part
            inputs=proc_inputs,
            outputs=proc_outputs,
            arguments=job_args,
        )
        
        step_name = f"{self._get_step_name('XGBoostModelEval')}-{self.config.job_type.capitalize()}"

        return ProcessingStep(
            name=step_name,
            step_args=step_args,
            depends_on=dependencies or [],
            cache_config=self._get_cache_config(enable_caching)
        )
        
        logger.info(f"Created ProcessingStep with name: {processing_step.name}")
        return processing_step

```





-----------
##  Recommended Notes

