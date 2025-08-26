---
tags:
  - code
  - code_snippet
  - bash/tar
keywords: 
topics: 
language: bash
date of note: 2025-07-15
---

## Code Snippet Summary

>[!important]
>Read the content of `.tar.gz` file




## Code

### Show file sizes

```bash
# 4. Show file sizes
echo -e "\nShowing file sizes:"
tar -tvf code.tar.gz | awk '{print $3, $6}'
```







-----------
##  Recommended Notes

- [[Count Number of Files in tar gz file]]
- [[Examine the Content of tar gz file]]
- [[Compress folder into tar gz file and uncompress]]