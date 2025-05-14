---
tags:
  - code
  - code_snippet
  - aws/pytorch_estimator
  - aws/sagemaker
  - model/prediction
  - model/deploy_production
  - python/aws_python_sdk
keywords: 
topics: 
language: python
date of note: 2025-05-13
---

## Code Snippet Summary

>[!important]
>- Create model class `PytorchModel`
>- Deploy endpoint

- [[Pytorch Estimator Inference for RnR BSM]]
- [[SageMaker SDK Deploy BYO Model to Endpoint]]

## Code

### Session and Role


```python
import sagemaker

session = sagemaker.Session()
```

```python
# This object represents the IAM role that we are assigned.
role = sagemaker.get_execution_role()
```



### Model Data in S3

```python
model_path = f"s3://{bucket}/{prefix}/"
training_job = 'pytorch-training-YYYY-MM-DD-HH-mm-SS-ID' 
```

```python
model_data = os.path.join(model_path, training_job, "output", "model.tar.gz")
```

- `model.tar.gz` is the output compressed file of folder `/opt/ml/model` in the container

### PytorchModel Class

```python
from sagemaker.pytorch import PyTorchModel
```

```python
pytorch_model = PyTorchModel(
    model_data=model_data,
    role=role,
    entry_point='inference.py',
    framework_version="2.1.0",       # Match your training framework
    py_version="py310",              # Python version
    source_dir=source_dir,           # Folder containing inference.py
    sagemaker_session=session
)
```

^a93825

- `source_dir`
	- the local directory where the inference script `inference.py` is stored
	- `inference.py` the entry point script which should be the root in `source_dir`

- `PytorchModel`
	- [reference](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html#pytorch-model)
	- An PyTorch SageMaker `Model` that can be deployed to a SageMaker `Endpoint`.

### Deploy PytorchModel Endpoint

#### Optional: Define the Serializer and Deserializer

```python
from sagemaker.serializers import CSVSerializer, JSONSerializer, StringSerializer
from sagemaker.deserializers import CSVDeserializer, JSONDeserializer, StringDeserializer
```

#### Deploy

```python
endpoint_name = "endpoint_name" 
```

```python
predictor = pytorch_model.deploy(
    initial_instance_count=1,
    instance_type="ml.m5.4xlarge",
    endpoint_name=endpoint_name,
    serializer=StringSerializer(),  # <--- ADD THIS BACK
    deserializer=StringDeserializer(), #CSVDeserializer() #JSONDeserializer(), # <--- Add back if your output_fn produces JSON
)
```

- `sagemaker.pytorch.model.PyTorchPredictor`
	- [reference](https://sagemaker.readthedocs.io/en/stable/frameworks/pytorch/sagemaker.pytorch.html#pytorch-predictor)
	- A Predictor for inference against PyTorch Endpoints.
	- `deploy()`
		- [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html#sagemaker.estimator.Framework.deploy)


#### Optional

```python
# Set content-type and accept headers
predictor.content_type = "text/csv"          # <-- request format
predictor.accept = "text/csv"   #"application/json"        # <-- response format
```


### Delete Endpoint

```python
predictor.delete_endpoint(delete_endpoint_config=True)
```

- `sagemaker.estimator.Estimator.delete_endpoint`
	- [reference](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html#sagemaker.estimator.Estimator.delete_endpoint)


## BYO Model Endpoint 

- [[SageMaker SDK Deploy BYO Model to Endpoint]]



-----------
##  Recommended Notes

- [[Pytorch Estimator Training for RnR BSM]]
- [[Batch Transform using Endpoint from SageMaker]]