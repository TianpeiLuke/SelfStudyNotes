---
tags:
  - code
  - code_snippet
  - regular_expression
keywords: 
topics: 
language: regular expression
date of note: 2024-04-09
---

## Code Snippet Summary

>[!important]
>- Identify punctuation (`,.?!:;`) on the left of target sub-string
>- Identify non-zero spaces on the right of the target sub-string
>- Do not include identified patterns surround the target.


## Code


```
(?<=[.,!?:;])(?=[^\s])
```




-----------
##  Recommended Notes

