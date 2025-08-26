---
tags:
  - code
  - code_snippet
  - bash/tar
  - linux/tar
  - bash
keywords: 
topics: 
language: bash
date of note: 2025-07-15
---

## Code Snippet Summary

>[!important]
>Read the content of `.tar.gz` file




## Code

### Count number of files

```bash
# 3. Count number of files
echo -e "\nTotal number of files:"
tar -tvf code.tar.gz | wc -l
```

### Show file sizes

```bash
# 4. Show file sizes
echo -e "\nShowing file sizes:"
tar -tvf code.tar.gz | awk '{print $3, $6}'
```

### Search for specific files (e.g., python files)


```bash
# 5. Search for specific files (e.g., python files)
echo -e "\nFinding Python files:"
tar -tvf code.tar.gz | grep "\.py$"

# 6. View compressed size
echo -e "\nCompressed size:"
ls -lh code.tar.gz | awk '{print $5}'

# 7. Check file integrity
echo -e "\nChecking file integrity:"
gzip -t code.tar.gz && echo "Archive is OK" || echo "Archive is corrupted"
```





-----------
##  Recommended Notes

- [[Examine the Content of tar gz file]]
- [[Compress folder into tar gz file and uncompress]]