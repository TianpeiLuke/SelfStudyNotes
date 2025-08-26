---
tags:
  - code
  - code_snippet
  - bash/find
keywords: 
topics: 
language: 
date of note: 2025-07-12
---

## Code Snippet Summary

>[!important]


## Code

```bash
find . -type d -name "__pycache__" -exec rm -rf {} +
find . -name "*.pyc" -delete
find . -name "*.pyo" -delete
find . -name "*.bak" -delete
find . -name "*~" -delete
find . -name ".DS_Store" -delete
find . -name ".ipynb_checkpoints" -exec rm -rf {} +
find . -name "._*" -delete
```


```bash
find . -name "*.pyc" -delete 2>/dev/null || true
```

```bash
find . -name "__pycache__" -type d -exec rm -rf {} + 2>/dev/null || true
```

```bash
find . -name ".pytest_cache" -o -name "__pycache__" -type d
```

```bash
find . -name ".pytest_cache" -type d
```




-----------
##  Recommended Notes

- [[Find and Remove Files Except for Symlink]]
- [[Find and Replace a Keyword]]
- [[Find and Replace text within file]]