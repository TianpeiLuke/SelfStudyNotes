---
tags:
  - code
  - code_snippet
  - python/aws_python_sdk
  - aws/sagemaker
  - model/prediction
  - model/batch_inference
keywords: 
topics: 
language: python
date of note: 2025-05-13
---

## Code Snippet Summary

>[!important]
>Create Batch Inference job in SageMaker using `Transformer`

- [[Batch Transform using Endpoint from SageMaker]]

## Code

```python
from sagemaker.transformer import Transformer
```

- `Transformer`
	- [reference](https://sagemaker.readthedocs.io/en/stable/api/inference/transformer.html#transformer)
	- A class for handling creating and interacting with Amazon SageMaker transform jobs.

### Session and Role

```python
import sagemaker

session = sagemaker.Session()
```

```python
# This object represents the IAM role that we are assigned.
role = sagemaker.get_execution_role()
```

### Input and Output

```python
batch_input_data = f"s3://{bucket}/{input_prefix}"
batch_out_data = f"s3://{bucket}/{output_prefix}"
```


### Model Class

![[SageMaker SDK Deploy PytorchModel to Endpoint#^a93825]]

- [[SageMaker SDK Deploy PytorchModel to Endpoint]]

### Transformer Job

#### Single Line

```python
transformer = Transformer(
    model_name=pytorch_model.name,                # Use the endpoint's model name
    instance_count=1,
    instance_type="ml.m5.xlarge",
    output_path=batch_out_data,             # Replace with your S3 bucket
    strategy="SingleRecord",
    assemble_with="Line",
    accept="text/csv",                       # Match output_fn
    env={},                                  # Optional environment variables
    max_payload=1,                           # Optional: override payload size 1= 1 MB
    sagemaker_session=session,
)
```


### Start the Job

```python
# === Input file ===
# Ensure this input file exists in your S3 bucket (e.g., CSV file)
transformer.transform(
    data=batch_input_data,
    content_type="text/csv",                # Match input_fn logic
    split_type="Line",                      # Important for CSV
    input_filter=input_filter,            # Optional: you can filter columns; In this example, Keep columns 0, 2, 3; "$[0,2,3]"
    #join_source="Input",                    # If you want original data in output
    wait=True                               # Block until done
)
```

- `Transformer.transform`
	- [reference](https://sagemaker.readthedocs.io/en/stable/api/inference/transformer.html#sagemaker.transformer.Transformer.transform)
	- **`split_type`**
		- the record delimiter for the input object (default: ‘None’). 
		- Valid values: `None`, `Line`, `RecordIO`, and `TFRecord`.
	- **`input_filter`**
		- A JSONPath to select a portion of the input to pass to the algorithm container for inference. 
		- If you omit the field, it gets the value ‘$’, representing the entire input. 
		- For *CSV* data, each row is taken as a *JSON array*, so only index-based JSONPaths can be applied, e.g. $[0], $[1:]. 
		- CSV data should follow the [RFC format](https://tools.ietf.org/html/rfc4180). 
		- See [Supported JSONPath Operators](https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform-data-processing.html#data-processing-operators) for a table of supported JSONPath operators. 
		- For more information, see the SageMaker API documentation for [CreateTransformJob](https://docs.aws.amazon.com/sagemaker/latest/dg/API_CreateTransformJob.html). Some examples: “\$[1:]”, “\$.features” (default: None).
	- **join_source** ([_str_](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)") _or_ [_PipelineVariable_](https://sagemaker.readthedocs.io/en/stable/workflows/pipelines/sagemaker.workflow.pipelines.html#sagemaker.workflow.entities.PipelineVariable "sagemaker.workflow.entities.PipelineVariable")) 
		- The source of data to be joined to the transform output. It can be set to ‘Input’ meaning the entire input record will be joined to the inference result. 
		- You can use OutputFilter to select the useful portion before uploading to S3. (default: None). 
		- Valid values: `Input`, `None`.

#### Join with Input

- [reference](https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform-data-processing.html#batch-transform-data-processing-example-all)

>[!info]
>- If you're using the [Amazon SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable) to combine the input data with the inferences in the output file, specify the `assemble_with` and `accept` parameters when initializing the transformer object. 
>
>- When you use the transform call, specify `Input` for the `join_source` parameter, and specify the `split_type` and `content_type` parameters as well. 
>	- The `split_type` parameter must have the same value as `assemble_with`, and the `content_type` parameter must have the same value as `accept`. 
>- For more information about the parameters and their accepted values, see the [Transformer](https://sagemaker.readthedocs.io/en/stable/api/inference/transformer.html#sagemaker.transformer.Transformer) page in the _Amazon SageMaker AI Python SDK_.

```python'
sm_transformer = sagemaker.transformer.Transformer(…, assemble_with="Line", accept="text/csv")

sm_transformer.transform(…, join_source="Input", split_type="Line", content_type="text/csv")
```

>[!info]
>If you're using the AWS SDK for Python (Boto 3), join all input data with the inference by adding the following code to your [`CreateTransformJob`](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_CreateTransformJob.html) request. 
>
>
>- The values for `Accept` and `ContentType` must match, and the values for `AssembleWith` and `SplitType` must also match.

```python
{
    "DataProcessing": {
        "JoinSource": "Input"
    },
    "TransformOutput": {
        "Accept": "text/csv",
        "AssembleWith": "Line"
    },
    "TransformInput": {
        "ContentType": "text/csv",
        "SplitType": "Line"
    }
}
```

>[!info]
>For JSON or JSON Lines input files, the results are in the `SageMakerOutput` key in the input JSON file. 
>- For example, if the input is a JSON file that contains the key-value pair `{"key":1}`, the data transform result might be `{"label":1}`.
>- SageMaker AI stores both in the input file in the `SageMakerInput` key.

```python
{
    "key":1,
    "SageMakerOutput":{"label":1}
}
```

>[!info]
>The joined result for JSON must be a key-value pair object. 
>- If the input isn't a key-value pair object, SageMaker AI creates a new JSON file. 
>- In the new JSON file, the input data is stored in the `SageMakerInput` key and the results are stored as the `SageMakerOutput` value.





-----------
##  Recommended Notes

- [[SageMaker SDK Training with Pytorch Container]]
- [[SageMaker SDK Deploy PytorchModel to Endpoint]]

- Doc
	-  [Supported JSONPath Operators](https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform-data-processing.html#data-processing-operators)
	- 