---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - aws/pytorch_estimator
  - python/aws_cdk
keywords: 
topics: 
language: python
date of note: 2025-04-15
---

## Code Snippet Summary

>[!important]
>- Launch endpoint
>- Execute the inference script using prebuit container in **Pytorch Estimator**


## Code

```python
import os
import json
import pandas as pd
```



## Launch Endpoint

```python
model_path = "s3://buyer-seller-messaging-reversal/models/2025-04-15/"
training_job = 'pytorch-training-2025-04-17-01-17-15-278'

model_data = os.path.join(model_path, training_job, "output", "model.tar.gz")
```

### Pytorch Model Predictor

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

^0aed2c

- Inference script
	- [[Inference Script for RnR BSM]]
- [[Pytorch Estimator Training for RnR BSM]]

### Create Endpoint

```python
from sagemaker.serializers import CSVSerializer, JSONSerializer
from sagemaker.deserializers import CSVDeserializer, JSONDeserializer
```

```python
endpoint_name = "bsm-rnr-model-2025-04-15-01"
```

```python
predictor = pytorch_model.deploy(
    initial_instance_count=1,
    instance_type="ml.m5.xlarge",
    endpoint_name=endpoint_name,
    serializer=CSVSerializer(),      # <--- ADD THIS BACK
    deserializer=JSONDeserializer(), # <--- Add back if your output_fn produces JSON
)
```

```python
# Set content-type and accept headers
predictor.accept = "application/json"        # <-- response format
```

### Invoke Endpoint

```python
csv_line = sample_test.to_csv(index=False, header=False, encoding='utf-8').strip()
```

```python
response = predictor.predict(csv_line)
print("Prediction response (JSON):", response)
```

### Delete Endpoint

```python
predictor.delete_endpoint(delete_endpoint_config=True)
```



-----------
##  Recommended Notes

- [[SageMaker BYO Container - Pytorch Lightning Training]]
