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

```text
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
```

```python
question = ...
dialogue = ...


print(prompt_template.format(question=question, dialogue=dialogue))
```

### Invoke BedRock  Runtime

- [[Invoke Bedrock with Exponential Backoff]]


-----------
##  Recommended Notes


- [[Prompt Engineering for LLM]]