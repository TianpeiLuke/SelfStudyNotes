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
from sagemaker.workflow.steps import TrainingStep, Step
from sagemaker.workflow.pipeline_context import PipelineSession
from pathlib import Path

from typing import Optional, Dict, List
import os
```


```python
import logging
logger = logging.getLogger(__name__)
```
### Import Model Config and Base Class

```python
from .workflow_config import ModelConfig
from .builder_step_base import StepBuilderBase
```

### Builder Class

```python
class PyTorchTrainingStepBuilder(StepBuilderBase):
    """PyTorch model builder"""
    
    def __init__(
        self, 
        config: ModelConfig, 
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
        
        if not self.config.hyperparameters:
            raise ValueError("ModelConfig must include hyperparameters for training")
            
        logger.info(f"Initialized PyTorchTrainingStepBuilder with hyperparams: {self.config.hyperparameters.get_config()}")

    def validate_configuration(self) -> None:
        """Validate configuration requirements"""
        required_attrs = [
            'entry_point',
            'source_dir',
            'instance_type',
            'instance_count',
            'framework_version',
            'py_version',
            'volume_size',
            'input_path',
            'output_path'
        ]
        
        for attr in required_attrs:
            if not hasattr(self.config, attr):
                raise ValueError(f"ModelConfig missing required attribute: {attr}")
        
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
    
    def _create_pytorch_estimator(self, checkpoint_s3_uri: str) -> PyTorch:
        """Create PyTorch estimator"""
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
            hyperparameters=self.config.hyperparameters.serialize_config(),
            profiler_config=self._create_profiler_config(),
            metric_definitions=self._get_metric_definitions()
        )

    def _get_checkpoint_uri(self) -> str:
        """Get checkpoint URI for training"""
        if self.config.has_checkpoint():
            return self.config.get_checkpoint_uri()
        
        return os.path.join(
            self.config.output_path,
            "checkpoints",
            self.config.current_date
        )

    def create_step(self, dependencies: Optional[List] = None) -> Step:
        """
        Create training step with dataset inputs.
        
        Args:
            dependencies: List of dependent steps
            
        Returns:
            TrainingStep instance
        """
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

        # Get checkpoint URI and create estimator
        checkpoint_uri = self._get_checkpoint_uri()
        logger.info(
            f"Creating PyTorch estimator:"
            f"\n\tCheckpoint URI: {checkpoint_uri}"
            f"\n\tInstance Type: {self.config.instance_type}"
            f"\n\tFramework Version: {self.config.framework_version}"
            f"\n\tPython Version: {self.config.py_version}"
        )
        estimator = self._create_pytorch_estimator(checkpoint_uri)
        
        # Get step name
        step_name = self._get_step_name('Training')
        
        return TrainingStep(
            name=step_name,
            estimator=estimator,
            inputs=inputs,
            depends_on=dependencies or []
        )

    # Maintain backwards compatibility
    def create_training_step(self, dependencies: Optional[List] = None) -> TrainingStep:
        """Backwards compatible method for creating training step"""
        return self.create_step(dependencies)

```

- [[Model Config for Training Step]]
- [[Hyperparameter for Training Step]]
- [[Base Step Builder]]


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
