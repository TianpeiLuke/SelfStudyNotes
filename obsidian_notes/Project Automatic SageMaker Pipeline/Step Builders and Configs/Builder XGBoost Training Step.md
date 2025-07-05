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
from sagemaker.xgboost.estimator import XGBoost
from sagemaker.debugger import ProfilerConfig
from sagemaker.inputs import TrainingInput
from sagemaker.workflow.steps import TrainingStep, Step
from sagemaker.workflow.pipeline_context import PipelineSession
from sagemaker.workflow.functions import Join  # Make sure to import
from sagemaker.s3 import S3Uploader
```


```python
from pathlib import Path
import os
import json
import tempfile
import shutil
from botocore.exceptions import ClientError
from typing import Optional, List, Dict
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
class XGBoostTrainingStepBuilder(StepBuilderBase):
    """XGBoost model training step builder that uses a config file for hyperparameters."""

    def __init__(
        self,
        config: XGBoostTrainingConfig,
        sagemaker_session: Optional[PipelineSession] = None,
        role: Optional[str] = None,
        notebook_root: Optional[Path] = None
    ):
        super().__init__(config, sagemaker_session, role, notebook_root)
        self.config: XGBoostTrainingConfig  # For type hinting

        if not isinstance(self.config.hyperparameters, XGBoostModelHyperparameters):
            raise ValueError("Config for XGBoostTrainingStepBuilder must include XGBoostModelHyperparameters.")
        
        self.validate_configuration()


    def validate_configuration(self) -> None:
        """Validate configuration requirements for XGBoost training"""
        required_attrs = [
            'training_entry_point', 'source_dir', 'training_instance_type',
            'training_instance_count', 'training_volume_size', 'framework_version',
            'py_version', 'input_path', 'output_path'
        ]
        
        missing_attrs = [attr for attr in required_attrs if not getattr(self.config, attr, None)]
        if missing_attrs:
            raise ValueError(f"XGBoostTrainingConfig missing required attributes: {', '.join(missing_attrs)}")

    def _prepare_hyperparameters_file(self) -> str:
        """
        Serializes the hyperparameters to JSON, uploads it as
        `<hyperparameters_s3_uri>/hyperparameters.json`, and
        returns that full S3 URI.
        """
        hyperparams_dict = self.config.hyperparameters.model_dump()
        local_dir = Path(tempfile.mkdtemp())
        local_file = local_dir / "hyperparameters.json"
        
        try:
            local_file.write_text(json.dumps(hyperparams_dict, indent=2))

            prefix = self.config.hyperparameters_s3_uri or ""
            prefix = prefix.rstrip("/")
            target_s3_uri = f"{prefix}/hyperparameters.json"

            s3_parts = target_s3_uri.replace('s3://', '').split('/', 1)
            bucket = s3_parts[0]
            key = s3_parts[1]
            
            s3_client = self.session.boto_session.client('s3')
            try:
                s3_client.head_object(Bucket=bucket, Key=key)
                logger.info(f"Found existing hyperparameters file at {target_s3_uri}, deleting it...")
                s3_client.delete_object(Bucket=bucket, Key=key)
                logger.info("Existing hyperparameters file deleted successfully")
            except ClientError as e: # <-- FIX: Catch the real ClientError
                if e.response['Error']['Code'] == '404':
                    logger.info(f"No existing hyperparameters file found at {target_s3_uri}")
                else:
                    logger.warning(f"Error checking/deleting existing file: {str(e)}")

            logger.info(f"Uploading hyperparameters from {local_file} to {target_s3_uri}")
            S3Uploader.upload(str(local_file), target_s3_uri, sagemaker_session=self.session)
            
            logger.info(f"Hyperparameters successfully uploaded to {target_s3_uri}")
            return target_s3_uri
            
        finally:
            shutil.rmtree(local_dir)


    def _create_xgboost_estimator(self) -> XGBoost:
        """Create SageMaker XGBoost Estimator with an empty hyperparameters dictionary."""
        
        # use secure-pypi
        env = {
             "CA_REPOSITORY_ARN": "arn:aws:codeartifact:us-west-2:149122183214:repository/amazon/secure-pypi"
        }

        logger.info(f"Use Secure-PyPI with CA_REPOSITORY_ARN = {env['CA_REPOSITORY_ARN']}")
        
        return XGBoost(
            entry_point=self.config.training_entry_point,
            source_dir=self.config.source_dir,
            role=self.role,
            instance_count=self.config.training_instance_count,
            instance_type=self.config.training_instance_type,
            framework_version=self.config.framework_version,
            py_version=self.config.py_version,
            # No hyperparameters are passed here directly
            hyperparameters={},
            sagemaker_session=self.session,
            output_path=self.config.output_path,
            environment=env
        )

    def create_step(self, dependencies: Optional[List[Step]] = None) -> TrainingStep:
        """
        Create XGBoost training step with data and config inputs.
        """
        # 1. Upload the hyperparameters to S3 and get the URI
        hparam_s3_uri = self._prepare_hyperparameters_file()
        
        # Define the S3 prefixes for each data channel using Join
        train_data_prefix = Join(on='/', values=[self.config.input_path, "train/"])
        val_data_prefix = Join(on='/', values=[self.config.input_path, "val/"])
        test_data_prefix = Join(on='/', values=[self.config.input_path, "test/"])

        # Log expressions
        logger.info(f"Train data path expression: {train_data_prefix.expr}")
        logger.info(f"Validation data path expression: {val_data_prefix.expr}")
        logger.info(f"Test data path expression: {test_data_prefix.expr}")

        # 2. Define the input channels
        inputs = {
            "train": TrainingInput(s3_data=train_data_prefix),
            "val": TrainingInput(s3_data=val_data_prefix),
            "test": TrainingInput(s3_data=test_data_prefix),
            # Channel for the hyperparameter file
            "config": TrainingInput(s3_data=hparam_s3_uri)
        }

        logger.info(f"Training inputs configured: {inputs}")

        # 3. Create the estimator (without hyperparameters)
        estimator = self._create_xgboost_estimator()
        
        step_name = self._get_step_name('XGBoostTraining')
        
        # 4. Create the TrainingStep
        return TrainingStep(
            name=step_name,
            estimator=estimator,
            inputs=inputs,
            depends_on=dependencies or []
        )

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