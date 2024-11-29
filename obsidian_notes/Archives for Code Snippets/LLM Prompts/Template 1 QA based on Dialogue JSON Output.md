---
tags:
  - code
  - code_snippet
  - large_language_models
  - prompt
keywords: 
topics: 
language: python
date of note: 2024-04-09
---

## Code Snippet Summary

>[!important]
>You are given a dialogue in between `<dialogue>` and `</dialogue>`. 
>1. Please answer the question between `<question>` and `</question>`. 
>2. Provide answer in the following JSON format
>   ```json
>{
 >Decision: "Yes"/"No"/"Not clear",
 >Reason: 
>}
>   ```
> 3. Do not copy input in response.


## Code

Use the following prompt

```python

prompt_template = '''


Human: You are given a dialogue between BUYER and SELLER in the bottom. Complete the following tasks
1. Please answer the following question. 
2. Provide Answer in following JSON format.

{{
 Decision: "Yes"/"No"/"Not clear",
 Reason: 
}}

3. Do not copy the input in response.


<question>
{question}
</question>

<dialogue>
{dialogue}
</dialogue>

Assistant:


'''
```

```python
question = ...
dialogue = ...


print(prompt_template.format(question=question, dialogue=dialogue))
```

### Invoke BedRock  Runtime

```python
import boto3
import json

bedrock = boto3.client(service_name='bedrock-runtime')

modelId = 'anthropic.claude-v2'
accept = 'application/json'
contentType = 'application/json'


body = json.dumps({
    "prompt": prompt_template.format(question=question, dialogue=dialogue),
    "max_tokens_to_sample": 2000,
    "temperature": 0.1,
    "top_p": 0.9,
})

response = bedrock.invoke_model(body=body, modelId=modelId, accept=accept, contentType=contentType)

response_body = json.loads(response.get('body').read())
# text
print(response_body.get('completion'))
```




-----------
##  Recommended Notes


- [[Prompt Engineering for LLM]]