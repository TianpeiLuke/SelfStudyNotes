---
tags:
  - code
  - code_snippet
  - python/os
keywords: 
topics: 
language: python
date of note: 2024-04-15
---

## Code Snippet Summary

>[!important]
>List all filenames under a directory and sort them according to the time of their creation.


## Code

```python
import os

mypath = "/mydir/"

files = [f for f in os.listdir(mypath) if os.path.isfile(os.path.join(mypath, f))]

files.sort(key=lambda x: os.path.getmtime(os.path.join(mypath,x)))
```

- `os.path.getmtime()`: 



-----------
##  Recommended Notes

- [[Return list of all filenames under a directory]]
- [How do you get a directory listing sorted by creation date in python?](https://stackoverflow.com/questions/168409/how-do-you-get-a-directory-listing-sorted-by-creation-date-in-python)
