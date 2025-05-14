---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - aws/pytorch_estimator
  - model/training
  - python/aws_python_sdk
keywords: 
topics: 
language: python
date of note: 2025-05-13
---

## Code Snippet Summary

>[!important]
>- Launch the training job in SageMaker
>- Use Pytorch prebuilt container

- [[SageMaker SDK Training with BYO Container]]

## Code

```python
from sagemaker.pytorch import PyTorch
```

- `Pytorch`
	- prebuilt container

### Session and Role


```python
import sagemaker

session = sagemaker.Session()
```

```python
# This object represents the IAM role that we are assigned.
role = sagemaker.get_execution_role()
```


### Hyperparameter
#### Hyperparameter

```python
config = {...
         }
```

#### Stringtify the Hyperparameter

- `Pytorch Estimator` only takes hyperparameter in **string** format
- need to convert *bool*, *int*, *float*, *list*, *dict* fields into *str*

```python
import json

def serialize_config(config):
    safe_config = {}
    for k, v in config.items():
        if isinstance(v, (list, dict, bool)):
            safe_config[k] = json.dumps(v)
        else:
            safe_config[k] = str(v)
    return safe_config
```

```python
hyperparameters = serialize_config(config)
```

### Source Code

```
source_dir/
  |-- train.py
  |-- inference.py
  |-- requirements.txt
  |-- package/
  |-----| -- ...
```

- SageMaker compress this folder and save to `/opt/ml/code`
- The relative path within the folder is unchanged
- Need to specify all necessary packages version in `requirements.txt`
	- **Important**: keep the package version as precise as possible to allow duplication without breaking down

```python
entry_point = 'train.py'
source_dir = # local folder path
```

### Folder Structure within the Container

![[pytorch_container_folder_structure.drawio.png]]

- `/opt/ml/input`
	- `/opt/ml/input/data`: including training, validation, test data
		- `/opt/ml/input/data/train`
		- `/opt/ml/input/data/test`
		- `/opt/ml/input/data/val`
	- `/opt/ml/input/config`
		- `hyperparameter.json` is the hyperparameter passed to trainer
- `/opt/ml/model`: 
	- Save *model weights* and *artifacts* under `/opt/ml/model` path, which will be compressed and save to S3 with name `model.tar.gz`
- `/opt/ml/output`
	- Save *output data* and *figures* under `/opt/ml/output` path, which will be compressed and save to S3 with name `output.tar.gz
- Only `model.tar.gz` is needed for model inference

### Input / Output S3 Location

```python
s3_folder_root = f"s3://{bucket}/train_test_val/{cur_date}/"
output_path = f"s3://{bucket}/models/{cur_date}/"
checkpoint_path = f"s3://{bucket}/checkpointing/{cur_date}/"
```

```python
inputs = {
    "train": os.path.join(s3_folder_root, "train", "train.parquet"),
    "val": os.path.join(s3_folder_root, "val", "val.parquet"),
    "test": os.path.join(s3_folder_root, "test", "test.parquet")
}
```


### Training 

```python
from sagemaker.pytorch import PyTorch
```

#### Pytorch Framework Version and Python Version

```python
# This uses the latest PyTorch version from SageMaker prebuilt images (e.g., PyTorch 2.1)
framework_version = "2.1.0"
py_version = "py310"
```

#### Build Estimator

```python
estimator = PyTorch(
    entry_point=entry_point,  # train.py
    source_dir=source_dir,    # folder containing train, package, requirements.txt etc.
    role=role,
    instance_count=1,
    instance_type=instance_type,
    framework_version=framework_version,
    py_version=py_version,
    volume_size=500,
    max_run=4 * 24 * 60 * 60,
    output_path=output_path,
    checkpoint_s3_uri=checkpoint_path,
    sagemaker_session=session,
    hyperparameters=hyperparameters,
    #profiler_config=profiler_config,  # Enable Profiler
    metric_definitions=[
        {'Name': 'Train Loss', 'Regex': 'train_loss=([0-9\\.]+)'},
        {'Name': 'Validation Loss', 'Regex': 'val_loss=([0-9\\.]+)'},
        {'Name': 'Validation F1 Score', 'Regex': 'val/f1_score=([0-9\\.]+)'},
        {'Name': 'Validation AUC ROC', 'Regex': 'val/auroc=([0-9\\.]+)'},
    ]
)
```

### Start Training Job

```python
estimator.fit(inputs)
```



## Deploy Endpoint

- [[SageMaker SDK Deploy PytorchModel to Endpoint]]




-----------
##  Recommended Notes

- [[Pytorch Estimator Training for RnR BSM]]