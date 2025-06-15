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
from typing import Optional, List, Union
from pathlib import Path
import logging
```

```python
logger = logging.getLogger(__name__)
```
### Import from SageMaker SDK

```python
from sagemaker.transformer import Transformer
from sagemaker.workflow.steps import TransformStep, Step
from sagemaker.inputs import TransformInput
from sagemaker.workflow.properties import Properties
from sagemaker.workflow.pipeline_context import PipelineSession
```

### Import Config and Base

```python
from .config_batch_transform_step import BatchTransformStepConfig
from .builder_step_base import StepBuilderBase
```

- [[Base Step Builder]]
- [[Config for Batch Transform Step]]

### Main

```python
class BatchTransformStepBuilder(StepBuilderBase):
    """
    Builder for creating a SageMaker Batch Transform step in a workflow.
    """

    def __init__(
        self,
        config: BatchTransformStepConfig,
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None
    ):
        if not isinstance(config, BatchTransformStepConfig):
            raise ValueError(
                "BatchTransformStepBuilder requires a BatchTransformStepConfig instance."
            )
        super().__init__(config=config, sagemaker_session=sagemaker_session, role=role)
        self.config: BatchTransformStepConfig = config

    def validate_configuration(self) -> None:
        """
        Validate that all required transform settings are provided.
        """
        # batch_input_location and batch_output_location already validated by Pydantic
        # transform_instance_type and count likewise
        if self.config.job_type not in {"training", "testing", "validation", "calibration"}:
            raise ValueError(f"Unsupported job_type: {self.config.job_type}")
        logger.info(f"BatchTransformStepBuilder configuration for '{self.config.job_type}' validated.")

    def _create_transformer(self, model_name: Union[str, Properties]) -> Transformer:
        """
        Instantiate the SageMaker Transformer object.
        """
        return Transformer(
            model_name=model_name,
            instance_type=self.config.transform_instance_type,
            instance_count=self.config.transform_instance_count,
            output_path=self.config.batch_output_location,
            accept=self.config.accept,
            assemble_with=self.config.assemble_with,
            sagemaker_session=self.session,
        )

    def create_step(
        self,
        model_name: Union[str, Properties],
        dependencies: Optional[List[Step]] = None
    ) -> TransformStep:
        """
        Create a TransformStep for a batch transform.

        Args:
            model_name: The name of the SageMaker model (string or Properties).
            dependencies: Optional list of Pipeline Step dependencies.

        Returns:
            TransformStep: configured batch transform step.
        """
        self.validate_configuration()

        # Build the transformer
        transformer = self._create_transformer(model_name)

        # Configure the transform job inputs
        transform_input = TransformInput(
            data=self.config.batch_input_location,
            content_type=self.config.content_type,
            split_type=self.config.split_type,
            join_source=self.config.join_source,
            input_filter=self.config.input_filter,
            output_filter=self.config.output_filter,
        )

        # Name the step using registry or fallback
        step_name = f"{self._get_step_name('BatchTransform')}-{self.config.job_type.capitalize()}"

        transform_step = TransformStep(
            name=step_name,
            transformer=transformer,
            inputs=transform_input,
            depends_on=dependencies or [],
        )

        logger.info(f"Created TransformStep with name: {step_name}")
        return transform_step

```



## Previous Steps

- [[Builder Tabular Preprocessing Step]]
- [[Builder XGBoost Model Step]]
- [[Builder Pytorch Model Step]]




-----------
##  Recommended Notes

