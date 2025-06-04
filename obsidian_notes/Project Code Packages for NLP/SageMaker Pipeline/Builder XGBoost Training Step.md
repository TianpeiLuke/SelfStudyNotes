---
tags:
  - code
  - code_snippet
  - aws/sagemaker_pipeline
keywords: 
topics: 
language: 
date of note: 2025-06-03
---

## Code Snippet Summary

>[!important]


## Code

```python
import os
from pathlib import Path
from typing import Optional, List, Dict


from sagemaker.xgboost.estimator import XGBoost # Changed from PyTorch
from sagemaker.debugger import ProfilerConfig
from sagemaker.inputs import TrainingInput
from sagemaker.workflow.steps import TrainingStep, Step # Step used for typing
from sagemaker.workflow.pipeline_context import PipelineSession
```

```python
import logging

logger = logging.getLogger(__name__)
```

### Base Class and Config

```python
from .hyperparameters_xgboost import XGBoostModelHyperparameters
from .config_training_step_xgboost import XGBoostTrainingConfig
from .builder_step_base import StepBuilderBase
```

- [[Base Step Builder]]
- [[Config for XGBoost Training Step]]
- [[Hyperparameter for XGBoost Training Step]]

### Main Builder

```python
# --- XGBoost Training Step Builder ---
class XGBoostTrainingStepBuilder(StepBuilderBase):
    """XGBoost model training step builder"""

    def __init__(
        self,
        config: XGBoostTrainingConfig, # Use XGBoostTrainingConfig
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None
    ):
        """
        Initialize XGBoost model builder

        Args:
            config: XGBoostTrainingConfig instance
            sagemaker_session: SageMaker PipelineSession
            role: IAM role ARN
            notebook_root: Root directory of notebook (optional, often unused in this context)
        """
        super().__init__(config, sagemaker_session, role, notebook_root)
        self.config: XGBoostTrainingConfig # For type hinting

        if not isinstance(self.config.hyperparameters, XGBoostModelHyperparameters):
            raise ValueError("Config for XGBoostTrainingStepBuilder must include XGBoostModelHyperparameters.")
            
        logger.info(f"Initialized XGBoostTrainingStepBuilder with hyperparams: {self.config.hyperparameters.get_config()}")
        self.validate_configuration()


    def validate_configuration(self) -> None:
        """Validate configuration requirements for XGBoost training"""
        # For XGBoost in script mode, entry_point and source_dir are essential.
        # For built-in, they are not used. This builder assumes script mode.
        required_attrs = [
            'training_entry_point',
            'source_dir',
            'training_instance_type',
            'training_instance_count',
            'training_volume_size',
            'framework_version', # XGBoost framework version (e.g., "1.7-1")
            'py_version',        # Python version (e.g., "py3")
            'input_path',
            'output_path'
        ]
        
        missing_attrs = [attr for attr in required_attrs if not getattr(self.config, attr, None)]
        if missing_attrs:
            raise ValueError(f"XGBoostTrainingConfig missing required attributes: {', '.join(missing_attrs)}")
        
        if not Path(self.config.source_dir).is_dir():
            logger.warning(f"Source directory {self.config.source_dir} does not exist locally. Ensure it's correctly set for SageMaker.")
        if not (Path(self.config.source_dir) / self.config.training_entry_point).exists():
             logger.warning(f"Entry point script {self.config.training_entry_point} does not exist in source_dir {self.config.source_dir} locally.")


    def _create_profiler_config(self) -> ProfilerConfig:
        """Create profiler configuration"""
        return ProfilerConfig(
            system_monitor_interval_millis=1000
            # profile_params for XGBoost might differ or be less relevant than for PyTorch
        )

    def _get_metric_definitions(self) -> List[Dict[str, str]]:
        """Get metric definitions for XGBoost training monitoring"""
        # Common XGBoost metrics. Adjust based on your specific objective and eval_metric.
        metrics = [
            {'Name': 'validation:rmse', 'Regex': r'\[\d+\]\s*validation-rmse:([0-9\.]+)'},
            {'Name': 'validation:auc', 'Regex': r'\[\d+\]\s*validation-auc:([0-9\.]+)'},
            {'Name': 'validation:logloss', 'Regex': r'\[\d+\]\s*validation-logloss:([0-9\.]+)'},
            {'Name': 'validation:error', 'Regex': r'\[\d+\]\s*validation-error:([0-9\.]+)'}, # For binary classification
            {'Name': 'validation:merror', 'Regex': r'\[\d+\]\s*validation-merror:([0-9\.]+)'}, # For multiclass classification
            {'Name': 'train:auc', 'Regex': r'\[\d+\]\s*train-auc:([0-9\.]+)'},
            {'Name': 'train:rmse', 'Regex': r'\[\d+\]\s*train-rmse:([0-9\.]+)'},
        ]
        # If specific eval_metrics are set in hyperparameters, try to create regex for them
        hp_eval_metrics = self.config.hyperparameters.eval_metric
        if hp_eval_metrics:
            if isinstance(hp_eval_metrics, str):
                hp_eval_metrics = [hp_eval_metrics]
            for metric in hp_eval_metrics:
                metric_name_val = f"validation:{metric}"
                if not any(m['Name'] == metric_name_val for m in metrics):
                    metrics.append({'Name': metric_name_val, 'Regex': rf'\[\d+\]\s*validation-{metric}:([0-9\.]+)'})
                metric_name_train = f"train:{metric}"
                if not any(m['Name'] == metric_name_train for m in metrics):
                     metrics.append({'Name': metric_name_train, 'Regex': rf'\[\d+\]\s*train-{metric}:([0-9\.]+)'})
        return metrics
    
    def _create_xgboost_estimator(self, checkpoint_s3_uri: Optional[str]) -> XGBoost:
        """Create SageMaker XGBoost Estimator"""
        
        # Hyperparameters need to be in the format SageMaker expects for XGBoost
        # The serialize_config method from ModelHyperparametersBase handles this.
        hyperparameters = self.config.hyperparameters.serialize_config()

        return XGBoost(
            entry_point=self.config.training_entry_point, # For script mode
            source_dir=self.config.source_dir,           # For script mode
            role=self.role,
            instance_count=self.config.training_instance_count,
            instance_type=self.config.training_instance_type,
            framework_version=self.config.framework_version,
            py_version=self.config.py_version, # Required for script mode
            volume_size=self.config.training_volume_size,
            max_run=4 * 24 * 60 * 60, # Example: 4 days
            output_path=self.config.output_path,
            sagemaker_session=self.session,
            hyperparameters=hyperparameters,
            profiler_config=self._create_profiler_config(),
            metric_definitions=self._get_metric_definitions(),
            checkpoint_s3_uri=checkpoint_s3_uri,
            checkpoint_local_path="/opt/ml/checkpoints", # Standard path for checkpoints
            # use_spot_instances, max_wait, etc. can be added from config
        )

    def _get_checkpoint_uri(self) -> Optional[str]:
        """Get checkpoint URI for training"""
        if self.config.has_checkpoint():
            return self.config.get_checkpoint_uri()
        
        # Default checkpoint path if not explicitly set in config.checkpoint_path
        return os.path.join(
            self.config.output_path,
            "checkpoints", # A subfolder for checkpoints
            self.config.pipeline_name, # Added pipeline_name for better organization
            self.config.current_date
        )

    def create_step(self, dependencies: Optional[List[Step]] = None) -> TrainingStep:
        """
        Create XGBoost training step with dataset inputs.

        Args:
            dependencies: List of dependent steps

        Returns:
            TrainingStep instance
        """
        # Validate input path structure - assuming parquet files as per PyTorch example
        # These paths are relative to the S3 bucket defined in self.config.input_path
        # For XGBoost, often a 'train' and 'validation' channel are sufficient.
        # The 'test' channel is more for a separate evaluation/batch transform step.
        train_data_path = os.path.join(self.config.input_path, "train", "train.parquet")
        val_data_path = os.path.join(self.config.input_path, "val", "val.parquet")
        # test_data_path = os.path.join(self.config.input_path, "test", "test.parquet") # Optional

        logger.info(f"Train data path: {train_data_path}")
        logger.info(f"Validation data path: {val_data_path}")

        inputs = {
            "train": TrainingInput(
                s3_data=train_data_path,
                distribution='FullyReplicated', # Or 'ShardedByS3Key' for large datasets
                content_type='text/parquet', # Or 'text/csv', 'application/x-parquet'
                s3_data_type='S3Prefix'
            ),
            "validation": TrainingInput( # XGBoost uses 'validation' channel
                s3_data=val_data_path,
                distribution='FullyReplicated',
                content_type='text/parquet',
                s3_data_type='S3Prefix'
            )
            # "test": TrainingInput(s3_data=test_data_path) # If you have a test channel for the training script
        }

        checkpoint_uri = self._get_checkpoint_uri()
        logger.info(
            f"Creating XGBoost estimator:"
            f"\n\tCheckpoint URI: {checkpoint_uri}"
            f"\n\tInstance Type: {self.config.training_instance_type}"
            f"\n\tFramework Version: {self.config.framework_version}"
            f"\n\tPython Version: {self.config.py_version}"
            f"\n\tEntry Point: {self.config.training_entry_point}"
            f"\n\tSource Dir: {self.config.source_dir}"
        )
        estimator = self._create_xgboost_estimator(checkpoint_uri)
        
        step_name = self._get_step_name('XGBoostTraining')
        
        return TrainingStep(
            name=step_name,
            estimator=estimator,
            inputs=inputs,
            depends_on=dependencies or []
        )

    # Maintain backwards compatibility if this method name was conventional
    def create_training_step(self, dependencies: Optional[List[Step]] = None) -> TrainingStep:
        """Backwards compatible method for creating training step"""
        logger.warning("create_training_step is deprecated, use create_step instead.")
        return self.create_step(dependencies)
```

## Next Step

- [[Builder XGBoost Model Step]]


-----------
##  Recommended Notes

- [[Builder Pytorch Training Step]]