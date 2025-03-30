---
tags:
  - code
  - code_snippet
  - prompt
  - large_language_models
  - python/aws_cdk
keywords: 
topics: 
language: python
date of note: 2025-03-27
---

## Code Snippet Summary

>[!important]
>Prompt for DNR detection based on dialogue


## Code

```text
"""
You are an expert in analyzing buyer-seller messaging conversations. Your task is to determine if a dialogue is related to a "Delivered Not Received" (DNR) case.

A DNR case typically involves:
- Buyer claims they didn't receive the package
- Tracking shows delivered but buyer disputes receiving it
- Discussion about delivery location, tracking number, or delivery confirmation
- Mentions of missing package, lost delivery, or not finding the package

Please analyze the following dialogue and determine if it's a DNR case. Provide your classification and confidence score.

Dialogue:
{dialogue}

Please respond in the following format:
1. Classification: [DNR / Not DNR]
2. Confidence: [A number between 0 and 100, where 0 is completely uncertain and 100 is absolutely certain]
3. Key Evidence: List specific quotes or elements from the dialogue that support your conclusion
4. Reasoning: [Brief explanation for your classification]
"""
```





-----------
##  Recommended Notes

