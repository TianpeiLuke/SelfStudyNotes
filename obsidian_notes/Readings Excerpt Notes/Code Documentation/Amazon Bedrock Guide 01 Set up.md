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

# Set up the Amazon Bedrock API

>[!quote]
>This section describes how to set up your environment to make Amazon Bedrock API calls and provides examples of common use-cases. You can access the **Amazon Bedrock API** using the **AWS Command Line Interface (AWS CLI)**, an AWS SDK, or a **SageMaker Notebook**.
>-- [link](https://docs.aws.amazon.com/bedrock/latest/userguide/api-setup.html)


## Amazon Bedrock endpoints

To connect programmatically to an AWS service, you use an endpoint. Refer to the [Amazon Bedrock endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/bedrock.html) chapter in the AWS General Reference for information about the endpoints that you can use for Amazon Bedrock.

Amazon Bedrock provides the following service endpoints.

- `bedrock` – Contains control plane APIs for managing, training, and deploying models. For more information, see [Amazon Bedrock Actions](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_Operations_Amazon_Bedrock.html) and [Amazon Bedrock Data Types](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_Types_Amazon_Bedrock.html).
    
- `bedrock-runtime` – Contains data plane APIs for making inference requests for models hosted in Amazon Bedrock. For more information, see [Amazon Bedrock Runtime Actions](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_Operations_Amazon_Bedrock_Runtime.html) and [Amazon Bedrock Runtime Data Types](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_Types_Amazon_Bedrock_Runtime.html).
    
- `bedrock-agent` – Contains control plane APIs for creating and managing agents and knowledge bases. For more information, see [Agents for Amazon Bedrock Actions](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_Operations_Agents_for_Amazon_Bedrock.html) and [Agents for Amazon Bedrock Data Types](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_Types_Agents_for_Amazon_Bedrock.html).
    
- `bedrock-agent-runtime` – Contains data plane APIs for invoking agents and querying knowledge bases. For more information, see [Agents for Amazon Bedrock Runtime Actions](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_Operations_Agents_for_Amazon_Bedrock_Runtime.html) and [Agents for Amazon Bedrock Runtime Data Types](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_Types_Amazon_Bedrock_Runtime.html).


## Setting up an AWS SDK

| SDK documentation                                                   | Code examples                                                                                                | Amazon Bedrock prefix                                                                              | Amazon Bedrock runtime prefix                                                                                      | Agents for Amazon Bedrock prefix                                                                               | Agents for Amazon Bedrock runtime prefix                                                                                       |
| ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| [AWS SDK for C++](https://docs.aws.amazon.com/sdk-for-cpp)          | [AWS SDK for C++ code examples](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/cpp)               | [bedrock](https://sdk.amazonaws.com/cpp/api/LATEST/aws-cpp-sdk-bedrock/html/annotated.html)        | [bedrock-runtime](https://sdk.amazonaws.com/cpp/api/LATEST/aws-cpp-sdk-bedrock-runtime/html/annotated.html)        | [bedrock-agent](https://sdk.amazonaws.com/cpp/api/LATEST/aws-cpp-sdk-bedrock-agent/html/annotated.html)        | [bedrock-agent-runtime](https://sdk.amazonaws.com/cpp/api/LATEST/aws-cpp-sdk-bedrock-agent-runtime/html/annotated.html)        |
| [AWS SDK for Python (Boto3)](https://docs.aws.amazon.com/pythonsdk) | [AWS SDK for Python (Boto3) code examples](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python) | [bedrock](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/bedrock.html) | [bedrock-runtime](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/bedrock-runtime.html) | [bedrock-agent](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/bedrock-agent.html) | [bedrock-agent-runtime](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/bedrock-agent-runtime.html) |

### Test the Runtime setup

Add the following code to your notebook and run the code.

```python
import boto3
import json
bedrock = boto3.client(service_name='bedrock-runtime')

body = json.dumps({
    "prompt": "\n\nHuman:explain black holes to 8th graders\n\nAssistant:",
    "max_tokens_to_sample": 300,
    "temperature": 0.1,
    "top_p": 0.9,
})

modelId = 'anthropic.claude-v2'
accept = 'application/json'
contentType = 'application/json'

response = bedrock.invoke_model(body=body, modelId=modelId, accept=accept, contentType=contentType)

response_body = json.loads(response.get('body').read())
# text
print(response_body.get('completion'))
```

### Test the Amazon Bedrock setup

Add the following code to your notebook and run the code.

```python
import boto3
bedrock = boto3.client(service_name='bedrock')

bedrock.get_foundation_model(modelIdentifier='anthropic.claude-v2')
```





-----------
##  Recommended Notes

- Amazon Bedrock documentation [link](https://docs.aws.amazon.com/bedrock/)
	- [User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/index.html)
		- Amazon Bedrock API Setup [reference](https://docs.aws.amazon.com/bedrock/latest/userguide/api-setup.html)
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




