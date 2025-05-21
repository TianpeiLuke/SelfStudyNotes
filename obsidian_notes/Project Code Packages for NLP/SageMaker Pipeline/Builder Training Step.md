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
>**Builder** class for `TrainingStep`
>- Create `Pytorch` Estimator
>- Create `TrainingStep`
>	- Construct metric monitor
>	- Configure `TrainingInput`
>	- Configure `output_path`
>	- Configure `source_dir` and `entry_point`
>	- Configure training instance

- [[Design Pattern Builder Pattern]]

## Code

```python
from sagemaker.pytorch import PyTorch
from sagemaker.debugger import ProfilerConfig
from sagemaker.inputs import TrainingInput
from sagemaker.workflow.steps import TrainingStep
from sagemaker.workflow.pipeline_context import PipelineSession
from typing import Dict, List, Optional
import os
```

### Import Model Config and Hyperparameters

- [[Model Config for Training Step]]
- [[Hyperparameter for Training Step]]

### Builder Class

```python
class PyTorchTrainingStepBuilder:
    """PyTorch model builder"""
    def __init__(self, 
                 config: ModelConfig, 
                 hyperparams: ModelHyperparameters,
                 sagemaker_session: Optional[PipelineSession] = None, 
                 role: str = None):
        """
        Initialize PyTorch model builder
        
        Args:
            config: Pydantic ModelConfig instance
            hyperparams: Pydantic ModelHyperparameters instance
            sagemaker_session: SageMaker session
            role: IAM role ARN
        """
        self.config = config
        self.hyperparams = hyperparams
        self.session = sagemaker_session
        self.role = role
        logger.info(f"Initialized PyTorchModelBuilder with hyperparams: {hyperparams.get_config()}")
        
    def _create_profiler_config(self) -> ProfilerConfig:
        """Create profiler configuration"""
        return ProfilerConfig(
            system_monitor_interval_millis=1000
        )

    def _get_metric_definitions(self) -> List[Dict[str, str]]:
        """Get metric definitions for training monitoring"""
        return [
            {'Name': 'Train Loss', 'Regex': 'train_loss=([0-9\\.]+)'},
            {'Name': 'Validation Loss', 'Regex': 'val_loss=([0-9\\.]+)'},
            {'Name': 'Validation F1 Score', 'Regex': 'val/f1_score=([0-9\\.]+)'},
            {'Name': 'Validation AUC ROC', 'Regex': 'val/auroc=([0-9\\.]+)'},
        ]
    
    
    def _create_pytorch_estimator(self, checkpoint_s3_uri) -> PyTorch:
        return PyTorch(
            entry_point=self.config.entry_point,
            source_dir=self.config.source_dir,
            role=self.role,
            instance_count=self.config.instance_count,
            instance_type=self.config.instance_type,
            framework_version=self.config.framework_version,
            py_version=self.config.py_version,
            volume_size=self.config.volume_size,
            max_run=4 * 24 * 60 * 60,
            output_path=self.config.output_path,
            checkpoint_s3_uri=checkpoint_s3_uri,
            checkpoint_local_path="/opt/ml/checkpoints",
            sagemaker_session=self.session,
            hyperparameters=self.hyperparams.serialize_config(),
            profiler_config=self._create_profiler_config(),
            metric_definitions=self._get_metric_definitions()
        )

    
    def create_estimator(self) -> PyTorch:
        """Create PyTorch estimator"""
        # Use checkpoint path from config if available
        checkpoint_s3_uri = None
        if self.config.has_checkpoint():
            checkpoint_s3_uri = self.config.get_checkpoint_uri()
        else:
            # Create default checkpoint path
            checkpoint_s3_uri = os.path.join(
                self.config.output_path,
                "checkpoints",
                self.config.current_date
            )
    
        logger.info(
            f"Creating PyTorch estimator:"
            f"\n\tCheckpoint URI: {checkpoint_s3_uri}"
            f"\n\tInstance Type: {self.config.instance_type}"
            f"\n\tFramework Version: {self.config.framework_version}"
            f"\n\tPython Version: {self.config.py_version}"
        )
        
        return self._create_pytorch_estimator(checkpoint_s3_uri)

    
    def create_training_step(self) -> TrainingStep:
        """Create training step with dataset inputs"""
        # Validate input path structure
        train_path = os.path.join(self.config.input_path, "train", "train.parquet")
        val_path = os.path.join(self.config.input_path, "val", "val.parquet")
        test_path = os.path.join(self.config.input_path, "test", "test.parquet")

        # Create training inputs
        inputs = {
            "train": TrainingInput(train_path),
            "val": TrainingInput(val_path),
            "test": TrainingInput(test_path)
        }

        estimator = self.create_estimator()
        
        return TrainingStep(
            name="ModelTraining",
            estimator=estimator,
            inputs=inputs,
            depends_on=[]
        )
```


- [[Hyperparameter for Training Step]]
- [[Model Config for Training Step]]

### Learning: TrainingStep

```python
 estimator = PyTorch(...)

train_path = os.path.join(self.config.input_path, "train", "train.parquet")
val_path = os.path.join(self.config.input_path, "val", "val.parquet")
test_path = os.path.join(self.config.input_path, "test", "test.parquet")

inputs = {
    "train": TrainingInput(train_path),
     "val": TrainingInput(val_path),
     "test": TrainingInput(test_path)
}

TrainingStep(
            name="ModelTraining",
            estimator=estimator,
            inputs=inputs,
            depends_on=[]
        )
```


- `sagemaker.workflow.steps.TrainingStep`
	- [reference](https://sagemaker.readthedocs.io/en/stable/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.steps.TrainingStep)
	- `TrainingStep` for SageMaker Pipelines Workflows.
		- Construct a TrainingStep, given an `EstimatorBase` instance.
	- **name** ([_str_](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the TrainingStep.
	- **estimator** ([_EstimatorBase_](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html#sagemaker.estimator.EstimatorBase "sagemaker.estimator.EstimatorBase")) – A sagemaker.estimator.EstimatorBase instance.
	- **inputs** (`Union[str, dict, TrainingInput, FileSystemInput]`)
		- Information about the training data. This can be one of three types:
			- (`str`) the S3 location where training data is saved, or a [file://](file://) path in local mode.
			- (`dict[str, str]` or `dict[str, sagemaker.inputs.TrainingInput]`) If using multiple channels for training data, you can specify a dictionary mapping channel names to strings or [`TrainingInput()`](https://sagemaker.readthedocs.io/en/stable/api/utility/inputs.html#sagemaker.inputs.TrainingInput "sagemaker.inputs.TrainingInput") objects.
			- (`sagemaker.inputs.TrainingInput`) - channel configuration for S3 data sources that can provide additional information as well as the path to the training dataset. See [`sagemaker.inputs.TrainingInput()`](https://sagemaker.readthedocs.io/en/stable/api/utility/inputs.html#sagemaker.inputs.TrainingInput "sagemaker.inputs.TrainingInput") for full details.
			- (`sagemaker.inputs.FileSystemInput`) - channel configuration for a file system data source that can provide additional information as well as the path to the training dataset.
	- **depends_on** 
		- A list of Step/StepCollection names or Step instances or StepCollection instances that this TrainingStep depends on.



## Next Step

- [[Builder Model Step]]



-----------
##  Recommended Notes


- [[Pytorch Estimator Training for RnR BSM]]
