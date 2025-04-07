---
tags:
  - code
  - code_snippet
  - langchain
  - langgraph
  - aws/bedrock
keywords: 
topics: 
language: python
date of note: 2025-04-06
---

## Code Snippet Summary

>[!important]
>Create a chatbot in LangChain using BedRock service


## Code

```python
import boto3
from botocore.config import Config
```


### Setup

```python
# Set bedrock configs
bedrock_config = Config(
    connect_timeout=120, read_timeout=120, retries={"max_attempts": 0}
)
```

### Create BedRock Client

```python
# Create a bedrock runtime client
bedrock_rt = boto3.client(
    "bedrock-runtime", region_name=aws_region, config=bedrock_config
)
```

```python
# Create a bedrock client to check available models
bedrock = boto3.client("bedrock", region_name=aws_region, config=bedrock_config)
```


- [[Invoke Bedrock via Boto3 and AWS CDK]]

### Create a Bedrock Chat API model in LangChain

```python
from langchain_aws import ChatBedrockConverse
```


>[!quote]
> - AWS has recently released the Bedrock Converse API which provides a unified conversational interface for Bedrock models. This API does not yet support custom models. You can see a list of all [models that are supported here](https://docs.aws.amazon.com/bedrock/latest/userguide/conversation-inference.html). To improve reliability the ChatBedrock integration will switch to using the Bedrock Converse API as soon as it has feature parity with the existing Bedrock API. Until then a separate [ChatBedrockConverse](https://python.langchain.com/api_reference/aws/chat_models/langchain_aws.chat_models.bedrock_converse.ChatBedrockConverse.html) integration has been released.
> - We recommend using `ChatBedrockConverse` for users who do not need to use custom models. See the [docs](https://python.langchain.com/docs/integrations/chat/bedrock/#bedrock-converse-api) and [API reference](https://python.langchain.com/api_reference/aws/chat_models/langchain_aws.chat_models.bedrock_converse.ChatBedrockConverse.html) for more detail.
>   
>   
> -- [link](https://python.langchain.com/docs/integrations/providers/aws/)  

>[!info]
>```python
>from langchain_aws import ChatBedrock
>```

```python
model = ChatBedrockConverse(
    client=bedrock_rt, # runtime client for bedrock
    model="anthropic.claude-3-haiku-20240307-v1:0",
    temperature=0,
    max_tokens=None,
)
```

- [[LangGraph ReAct Example with OpenAI model]]




-----------
##  Recommended Notes

- `langchain_aws`
	- [LangChain AWS API](https://python.langchain.com/docs/integrations/providers/aws/)
	- The `LangChain` integrations related to [Amazon AWS](https://aws.amazon.com/) platform.
	- `pip install langchain-aws`


