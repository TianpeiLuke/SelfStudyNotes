---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - aws/step_function
  - python/aws_python_sdk
keywords: 
topics: 
language: python
date of note: 2025-05-20
---

## Code Snippet Summary

>[!important]
>**Builder** of `Pipeline`
>- Connect `TrainingStep`, `ModelStep`

- [[Design Pattern Builder Pattern]]

## Code

```python
from sagemaker.workflow.pipeline import Pipeline
from sagemaker.workflow.pipeline_context import PipelineSession
from pathlib import Path
from typing import Optional, Dict, Tuple
import json
import logging

from sagemaker.pytorch import PyTorchModel # Added for deploy_endpoint
```

### Load Config

- [[Config for Training Step]]
- [[Hyperparameter for Training Step]]

### Load Builders

- [[Builder Training Step]]
- [[Builder Model Step]]


### Workflow


```python
class BSMWorkflowBuilder:
    """Builder for BSM model training and inference pipeline"""

    def __init__(
        self,
        sagemaker_session: Optional[PipelineSession] = None,
        execution_role: Optional[str] = None,
        config_path: str = "config/config.json",
    ):
        try:
            self.sagemaker_session = sagemaker_session or PipelineSession()
            self.execution_role = execution_role or self.sagemaker_session.get_caller_identity_arn()

            self.config, self.hyperparams = self._load_config(config_path)

            self.region = self.config.region
            logger.info(f"Using region from configuration: {self.region}")
            logger.info(f"Initializing pipeline builder with role: {self.execution_role}")

            self._initialize_builders()
            self._create_pipeline_steps()

        except Exception as e:
            logger.error(f"Failed to initialize pipeline builder: {e}", exc_info=True)
            raise

    def _load_config(self, config_path: str) -> Tuple[ModelConfig, ModelHyperparameters]:
        config_file = Path(config_path)
        if not config_file.exists():
            raise FileNotFoundError(f"Config file not found: {config_file}")

        with open(config_file, "r") as f:
            config_data = json.load(f)

        model_config_data = {k: v for k, v in config_data.items() if k in ModelConfig.model_fields.keys()}
        hyperparams_data = {k: v for k, v in config_data.items() if k in ModelHyperparameters.model_fields.keys()}

        logger.info(f"Loading configurations from: {config_file}")

        return ModelConfig(**model_config_data), ModelHyperparameters(**hyperparams_data)

    def _initialize_builders(self) -> None:
        self.training_builder = PyTorchTrainingStepBuilder(
            config=self.config,
            hyperparams=self.hyperparams,
            sagemaker_session=self.sagemaker_session,
            role=self.execution_role
        )

        self.inference_builder = PytorchModelStepBuilder(
            config=self.config,
            sagemaker_session=self.sagemaker_session,
            role=self.execution_role
        )

        logger.info("Initialized training and inference builders")

    def _create_pipeline_steps(self) -> None:
        try:
            self.training_step = self.training_builder.create_training_step()
            logger.info("Created training step")

            self.inference_step = self.inference_builder.create_model_step(
                model_data=self.training_step.properties.ModelArtifacts.S3ModelArtifacts
            )
            logger.info("Created inference step (model registration step)")

        except Exception as e:
            logger.error(f"Failed to create pipeline steps: {e}", exc_info=True)
            raise

    def generate_pipeline(self) -> Pipeline:
        logger.info(f"Setting up pipeline '{self.config.pipeline_name}' with steps in region: {self.config.region}")
        return Pipeline(
            name=self.config.pipeline_name,
            steps=[self.training_step, self.inference_step],
            sagemaker_session=self.sagemaker_session
        )

    def create_or_update_pipeline(self) -> Pipeline:
        pipeline = self.generate_pipeline()
        logger.info(f"Creating/updating pipeline: {self.config.pipeline_name}")
        pipeline.upsert(
            role_arn=self.execution_role,
            description=f"BSM RnR Training and Model Registration Pipeline - {self.config.current_date}"
        )
        return pipeline

    def execute_pipeline(self, wait: bool = True):
        pipeline = self.create_or_update_pipeline()
        logger.info(f"Starting pipeline execution for '{self.config.pipeline_name}'")
        execution = pipeline.start()

        if wait:
            logger.info(f"Waiting for pipeline execution {execution.arn} to complete...")
            execution.wait()
            logger.info(f"Pipeline execution completed with status: {execution.describe()['PipelineExecutionStatus']}")

        return execution

    def get_pipeline_parameters(self) -> Dict:
        params = {
            'PipelineName': self.config.pipeline_name,
            'ExecutionRole': self.execution_role,
            'Region': self.config.region,
            'InputPath': self.config.input_path,
            'OutputPath': self.config.output_path,
            'TrainingInstanceType': self.config.instance_type,
            'InferenceInstanceType': self.config.inference_instance_type,
            'BatchSize': self.hyperparams.batch_size,
            'MaxEpochs': self.hyperparams.max_epochs,
            'LearningRate': self.hyperparams.lr,
            'Tokenizer': self.hyperparams.tokenizer_choice,
            'ModelClass': self.hyperparams.model_class
        }
        if self.config.checkpoint_path:
            params['CheckpointPath'] = self.config.checkpoint_path
        return params

    def get_pipeline_steps_info(self) -> Dict:
        if not hasattr(self, 'training_step') or not hasattr(self, 'inference_step'):
            return {"Error": "Pipeline steps have not been initialized yet."}

        return {
            self.training_step.name: {
                'Type': self.training_step.step_type.value,
                'DependsOn': self.training_step.depends_on or []
            },
            self.inference_step.name: {
                'Type': self.inference_step.step_type.value,
                'DependsOn': self.inference_step.depends_on or [self.training_step.name]
            }
        }

```


### Learning: Pipeline

```python
Pipeline(
            name=self.config.pipeline_name,
            steps=[self.training_step, self.inference_step],
            sagemaker_session=self.sagemaker_session
        )
```


- `sagemaker.workflow.pipeline.Pipeline`
	- [reference](https://sagemaker.readthedocs.io/en/stable/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.pipeline.Pipeline)
	- Pipeline for workflow.
		- Initialize a Pipeline
	- **name** ([_str_](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the pipeline.
	- **parameters** 
		- The list of the parameters.
	- **steps**  – The list of the non-conditional steps associated with the pipeline. 
		- Any steps that are within the if_steps or else_steps of a ConditionStep cannot be listed in the steps of a pipeline. 
		- Of particular note, the workflow service rejects any pipeline definitions that specify a step in the list of steps of a pipeline and that step in the if_steps or else_steps of any ConditionStep.
	- 





-----------
##  Recommended Notes

