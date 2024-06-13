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
>- match non-zero spaces *immediately after* the **beginning of string**.
>- match non-zero spaces *immediately before* **the end of string**. 


## Code

- match non-zero spaces or tabs immediately after the start of string
```
(^\s+)
```

- match non-zero spaces or tabs immediately before the end of string
```
(\s+$)
```




-----------
##  Recommended Notes

