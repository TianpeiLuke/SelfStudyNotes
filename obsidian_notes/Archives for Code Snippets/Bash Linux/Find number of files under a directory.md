---
tags:
  - code
  - code_snippet
  - bash
  - linux/ls
keywords: 
topics: 
language: linux
date of note: 2024-04-10
---

## Code Snippet Summary

>[!important]
>Count number of files under a given directory whose filename follows a pattern


## Code

```bash
ls -1q pattern | wc -l
```

- `ls -1q` will give you *one line per file*, even if they contain whitespace or special characters such as newlines.

- The output is piped to `wc -l`, which *counts the number of lines*.


### Count number of all files

```bash
ls folder | wc -l
```



-----------
##  Recommended Notes

- Stack Overflow [Is there a bash command which counts files?](https://stackoverflow.com/questions/11307257/is-there-a-bash-command-which-counts-files)