---
tags:
  - code
  - code_snippet
  - aws/pytorch_estimator
  - aws/sagemaker
keywords: 
topics: 
language: python
date of note: 2025-04-18
---

## Code Snippet Summary

>[!important]
>Using endpoint to run batch inference in AWS SageMaker

## Code

```python
from sagemaker.pytorch.model import PyTorchModel
from sagemaker.transformer import Transformer
```

### Launch Endpoint

![[Pytorch Estimator Inference for RnR BSM#^0aed2c]]

- [[Pytorch Estimator Inference for RnR BSM]]

#### Get Model Name

```python
model_name = pytorch_model.name
```

### Batch Input and Output

```python
batch_input_data = "s3://buyer-seller-messaging-reversal/batch_inference/input/2025-03-28/rnr_bsm_shiptrack_2023_2025.csv"

batch_out_data = "s3://buyer-seller-messaging-reversal/batch_inference/output/2025-03-28/"
```

### Input Filter

- Choose the input fields or the index position of these fields
- Assume `input_columns` as the input column list
- `full_field_list` as the accepted inference data list

```python
field_positions = {field: input_columns.index(field) for field in full_field_list if field in input_columns}
```

```python
input_filter = "$[" + ",".join(str(i) for i in field_positions.values()) + "]"
```

### Create Transformer Profile

```python
transformer = Transformer(
    model_name=pytorch_model.name,                # Use the endpoint's model name
    instance_count=1,
    instance_type="ml.m5.xlarge",
    output_path=batch_out_data,             # Replace with your S3 bucket
    strategy="SingleRecord",                # or "MultiRecord" if your model supports batch input
    assemble_with="Line",
    accept="application/json",              # Match output_fn
    env={},                                  # Optional environment variables
    max_payload=1,                           # Optional: override payload size, 1= 1 MB
    sagemaker_session=session,
)
```

### Batch Transform Job 

```python
transformer.transform(
    data=batch_input_data,
    content_type="text/csv",                # Match input_fn logic
    split_type="Line",                      # Important for CSV
    input_filter=input_filter,            # Optional: you can filter columns; In this example, Keep columns 0, 2, 3; "$[0,2,3]"
    #output_filter="scores",
    #join_source="Input",                    # If you want original data in output
    wait=True                               # Block until done
)
```



## End-to-End Pipeline

- [[An End-to-End Training Deployment Pipeline on AWS]]


-----------
##  Recommended Notes

