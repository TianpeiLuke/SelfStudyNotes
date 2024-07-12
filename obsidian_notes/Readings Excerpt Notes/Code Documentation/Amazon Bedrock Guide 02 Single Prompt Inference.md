---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/bedrock
  - large_language_models
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-29
name: Amazon Bedrock Documentation User Guide
version: 
year: 2024
---

# Use the API to invoke a model with a single prompt

>[!quote]
>Run inference on a model through the API by sending an [InvokeModel](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_runtime_InvokeModel.html) or [InvokeModelWithResponseStream](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_runtime_InvokeModelWithResponseStream.html) request. You can specify the media type for the request and response bodies in the `contentType` and `accept` fields. The default value for both fields is `application/json` if you don't specify a value.
>-- [link](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-invoke.html)


>[!quote]
> Specify the following fields, depending on the model that you use.
> 
> 1. `modelId` – Use either the model ID or its ARN. The method for finding the `modelId` or `modelArn` depends on the type of model you use.
>     
>     - **Base model** – Do one of the following.
>         
>         - To see a list of model IDs for all base models supported by Amazon Bedrock, see [Base model IDs (on-demand throughput)](https://docs.aws.amazon.com/bedrock/latest/userguide/model-ids.html#model-ids-arns) .
>             
>         - Send a [ListFoundationModels](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_ListFoundationModels.html) request and find the `modelId` or `modelArn` of the model to use in the response.
>             
>         - In the console, select a model in **Providers** and find the `modelId` in the **API request** example.
>             
>     - **Custom model** – Purchase Provisioned Throughput for the custom model (for more information, see [Provisioned Throughput](https://docs.aws.amazon.com/bedrock/latest/userguide/prov-throughput.html)) and find the model ID or ARN of the provisioned model.
>         
>     - **Provisioned model** – If you have created a Provisioned Throughput for a base or custom model, do one of the following.
>         
>         - Send a [ListProvisionedModelThroughputs](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_ListProvisionedModelThroughputs.html) request and find the `provisionedModelArn` or `provisionedModelName` of the model to use in the response.
>             
>         - In the console, select a model in **Provisioned Throughput** and find the model ARN or name in the **Model details** section.
>     
> 2. `body` – Each base model has its own inference parameters that you set in the `body` field. The inference parameters for a custom or provisioned model depends on the base model from which it was created. For more information, see [Inference parameters for foundation models](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters.html).


## Invoke model code examples

The following examples show how to run inference with the [InvokeModel](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_runtime_InvokeModel.html) API. For examples with different models, see the inference parameter reference for the desired model ([Inference parameters for foundation models](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters.html)).

```python
import boto3
import json
brt = boto3.client(service_name='bedrock-runtime')

body = json.dumps({
    "prompt": "\n\nHuman: explain black holes to 8th graders\n\nAssistant:",
    "max_tokens_to_sample": 300,
    "temperature": 0.1,
    "top_p": 0.9,
})

modelId = 'anthropic.claude-v2'
accept = 'application/json'
contentType = 'application/json'

response = brt.invoke_model(body=body, 
							modelId=modelId, 
							accept=accept,
							contentType=contentType)

response_body = json.loads(response.get('body').read())

# text
print(response_body.get('completion'))
```

- `service_name='bedrock-runtime'`: **Amazon Bedrock Runtime**: [bedrock-runtime  reference](https://docs.aws.amazon.com/cli/latest/reference/bedrock-runtime/) 
	- `invoke_model`: Invokes the specified Amazon Bedrock model to run inference using the input provided in the request body. You use InvokeModel to run inference for text models, image models, and embedding models. [reference](https://docs.aws.amazon.com/cli/latest/reference/bedrock-runtime/invoke-model.html)
	  
	- Input parameters: [reference](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_runtime_InvokeModel.html#API_runtime_InvokeModel_RequestSyntax)
		- **`accept`**: The desired MIME type of the *inference body* in the *response*. The default value is `application/json`.
		- **`contentType`**:The MIME type of the *input data* in the *request*. The default value is `application/json`.
		- **`modelId`**: Identifier of the model.
		  
		- **`body`**: Input data in the format specified in the content-type request header. To see the format and content of this field for different models, refer to [Inference parameters](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters.html).
		  
	- **Response**: If the action is successful, the service sends back an HTTP 200 response. [reference](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_runtime_InvokeModel.html#API_runtime_InvokeModel_ResponseElements) 
		- `contentType`: The MIME type of the inference result. It belong to the *HTTP headers*.

		- **`body`**: Inference response (the *HTTP body*.) from the model in the format specified in the content-type header field. To see the format and content of the request body for different models, refer to [Inference parameters](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters.html).


-----------
##  Recommended Notes

- Amazon Bedrock documentation [link](https://docs.aws.amazon.com/bedrock/)
	- [User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/index.html)
		- Amazon Bedrock API Setup [reference](https://docs.aws.amazon.com/bedrock/latest/userguide/api-setup.html)
		- Amazon Bedrock API Inference [reference](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-invoke.html)
	- [API Reference](https://docs.aws.amazon.com/bedrock/latest/APIReference/index.html) 
	  
- [Code examples for Amazon Bedrock using AWS SDKs](https://docs.aws.amazon.com/bedrock/latest/userguide/service_code_examples.html).
- Foundational Model Supported [reference](https://docs.aws.amazon.com/bedrock/latest/userguide/models-supported.html)
- Refer to the following references for AWS CLI commands and operations:
	- [Amazon Bedrock CLI commands](https://docs.aws.amazon.com/cli/latest/reference/bedrock)
	- [Amazon Bedrock Runtime CLI commands](https://docs.aws.amazon.com/cli/latest/reference/bedrock-runtime)
	- [Agents for Amazon Bedrock CLI commands](https://docs.aws.amazon.com/cli/latest/reference/bedrock-agent/)
    - [Agents for Amazon Bedrock Runtime CLI commands](https://docs.aws.amazon.com/cli/latest/reference/bedrock-agent-runtime/)





----------
##  Citations

- *code source*:
- *code package link*




