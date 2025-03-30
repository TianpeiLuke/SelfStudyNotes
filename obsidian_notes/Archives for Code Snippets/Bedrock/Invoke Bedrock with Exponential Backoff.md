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
>- If the Throttling happens, reduce the frequency for the call using **exponential backoff**

- [[Exponential Back-off]]

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

- [[Invoke Bedrock via Boto3 and AWS CDK]]

### Exponential Back-off

```python
def exponential_backoff(attempt, max_delay=32):
    """
    Calculate exponential backoff time with jitter
    """
    delay = min(max_delay, (2 ** attempt) + random.uniform(0, 1))
    return delay
```

### Detect Throttling

```python
attempt = 0
while attempt < max_retries:
    try:
        start_time = time.time()
            
        #response = invoke_model
            
        #response_body = parse
            
        end_time = time.time()
        latency = end_time - start_time
            
        return result, latency
    except ClientError as e:
        if e.response['Error']['Code'] == 'ThrottlingException':
            attempt += 1
            if attempt == max_retries:
                print(f"Max retries ({max_retries}) reached. Failing.")
                return f"Error: Max retries reached - {str(e)}", None
                
            delay = exponential_backoff(attempt)
            print(f"Rate limit reached. Waiting {delay:.2f} seconds before retry {attempt}/{max_retries}")
            time.sleep(delay)
        else:
            return f"Error: {str(e)}", None
                
    except Exception as e:
        return f"Error: {str(e)}", None
```

- [[Invoke Bedrock via Boto3 and AWS CDK]]

### Put it Together

```python
from botocore.exceptions import ClientError
import random

def exponential_backoff(attempt, max_delay=32):
    """
    Calculate exponential backoff time with jitter
    """
    delay = min(max_delay, (2 ** attempt) + random.uniform(0, 1))
    return delay

def analyze_dialogue_with_claude(dialogue, max_retries=5):
    """
    Analyze dialogue using Claude via AWS Bedrock with retry logic
    """
    bedrock = boto3.client(service_name='bedrock-runtime')
    
    
    body = {
        "anthropic_version": "bedrock-2023-05-31",
        "max_tokens": 2048,
        "messages": [
            {
                "role": "user",
                "content": prompt_template.format(dialogue=dialogue)
            }
        ]
    }
    
    attempt = 0
    while attempt < max_retries:
        try:
            start_time = time.time()
            
            response = bedrock.invoke_model(
                modelId='anthropic.claude-3-sonnet-20240229-v1:0',
                body=json.dumps(body)
            )
            
            response_body = json.loads(response.get('body').read())
            result = response_body.get('content', [{}])[0].get('text', '')
            
            end_time = time.time()
            latency = end_time - start_time
            
            return result, latency

        except ClientError as e:
            if e.response['Error']['Code'] == 'ThrottlingException':
                attempt += 1
                if attempt == max_retries:
                    print(f"Max retries ({max_retries}) reached. Failing.")
                    return f"Error: Max retries reached - {str(e)}", None
                
                delay = exponential_backoff(attempt)
                print(f"Rate limit reached. Waiting {delay:.2f} seconds before retry {attempt}/{max_retries}")
                time.sleep(delay)
            else:
                return f"Error: {str(e)}", None
                
        except Exception as e:
            return f"Error: {str(e)}", None
```




-----------
##  Recommended Notes

- [[Amazon Bedrock Guide 01 Set up]]
- [[Amazon Bedrock Guide 02 Single Prompt Inference]]
- [[Amazon Bedrock Training Guide]]