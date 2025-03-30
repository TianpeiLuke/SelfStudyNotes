---
tags:
  - code
  - code_snippet
  - python/aws_cdk
  - aws/bedrock
keywords: 
topics: 
language: python
date of note: 2025-03-27
---

## Code Snippet Summary

>[!important]
>Given prompt, invoke LLM model in AWS Bedrock via CDK


## Code

### Prompt Template

```python
prompt_template = """
You are an expert in analyzing buyer-seller messaging conversations. Your task is to determine if a dialogue is related to a "Delivered Not Received" (DNR) case.

A DNR case typically involves:
- Buyer claims they didn't receive the package
- Tracking shows delivered but buyer disputes receiving it
- Discussion about delivery location, tracking number, or delivery confirmation
- Mentions of missing package, lost delivery, or not finding the package

Please analyze the following dialogue and determine if it's a DNR case. Provide your reasoning and confidence level.

Dialogue (Note: each message begins with [bom] and ends with [eom]):
{dialogue}

Please provide your analysis in the following format:
1. Is this a DNR case? (Yes/No)
2. Confidence Level (High/Medium/Low)
3. Key Evidence: List specific quotes or elements from the dialogue that support your conclusion
4. Reasoning: Explain why you believe this is or isn't a DNR case
"""
```

### Invoke LLM endpoint in Bedrock

```python
import json
import boto3
from tqdm import tqdm
import time
from datetime import datetime
```

- create bedrock service instance

```python
bedrock = boto3.client(service_name='bedrock-runtime')
```

- prepare for the request body

```python
body = {
    "anthropic_version": "bedrock-2023-05-31",
	"max_tokens": 1024,
    "messages": [
        {
            "role": "user",
            "content": prompt_template.format(dialogue=dialogue)
        }
    ]
}
```

- Call Model
	- [[Bedrock Model Ids]]

```python
 # Call the model
response = bedrock.invoke_model(
        modelId='anthropic.claude-3-sonnet-20240229-v1:0',
        body=json.dumps(body)
    )
```

- Get Response and Parse the text field

```python
# Parse response
response_body = json.loads(response.get('body').read())
result = response_body.get('content', [{}])[0].get('text', '')  
```



### Put it Together

```python
def analyze_dialogue_with_claude(dialogue):
    """
    Analyze dialogue using Claude via AWS Bedrock
    """
    # Initialize Bedrock client
    bedrock = boto3.client(service_name='bedrock-runtime')
    
    # Prepare request body
    body = {
        "anthropic_version": "bedrock-2023-05-31",
        "max_tokens": 1024,
        "messages": [
            {
                "role": "user",
                "content": prompt_template.format(dialogue=dialogue)
            }
        ]
    }
    
    try:
        # Start timing
        start_time = time.time()
        
        # Call the model
        response = bedrock.invoke_model(
            modelId='anthropic.claude-3-sonnet-20240229-v1:0',
            body=json.dumps(body)
        )
        
        # Parse response
        response_body = json.loads(response.get('body').read())
        result = response_body.get('content', [{}])[0].get('text', '')
        
        # End timing
        end_time = time.time()
        latency = end_time - start_time
        
        return result, latency
        
    except Exception as e:
        return f"Error: {str(e)}", None
```




-----------
##  Recommended Notes

- [[Amazon Bedrock Guide 01 Set up]]
- [[Amazon Bedrock Guide 02 Single Prompt Inference]]
- [[Amazon Bedrock Training Guide]]