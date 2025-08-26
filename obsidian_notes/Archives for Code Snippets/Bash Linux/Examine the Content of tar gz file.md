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

### List contents without extracting

```bash
# 1. List contents without extracting
echo "Listing contents of the tar.gz file:"
tar -tvf code.tar.gz
```

###  List only directories

```bash
# 2. List only directories
echo -e "\nListing only directories:"
tar -tvf code.tar.gz | grep ^d
```

### Count number of files

```bash
# 3. Count number of files
echo -e "\nTotal number of files:"
tar -tvf code.tar.gz | wc -l
```

- [[Count Number of Files in tar gz file]]
### Show file sizes

```bash
# 4. Show file sizes
echo -e "\nShowing file sizes:"
tar -tvf code.tar.gz | awk '{print $3, $6}'
```

- [[Show File Size in tar gz file]]
### Search for specific files (e.g., python files)

```bash
# 5. Search for specific files (e.g., python files)
echo -e "\nFinding Python files:"
tar -tvf code.tar.gz | grep "\.py$"
```

- [[Find a File in tar gz file]]

### View Compressed Size

```python
# 6. View compressed size
echo -e "\nCompressed size:"
ls -lh code.tar.gz | awk '{print $5}'
```

### Check File Integrity

```bash
# 7. Check file integrity
echo -e "\nChecking file integrity:"
gzip -t code.tar.gz && echo "Archive is OK" || echo "Archive is corrupted"
```





-----------
##  Recommended Notes

- [[Compress folder into tar gz file and uncompress]]