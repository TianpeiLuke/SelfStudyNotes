---
tags:
  - code
  - code_snippet
  - bash/output
keywords: 
topics: 
language: bash
date of note: 2024-04-26
---

## Code Snippet Summary

>[!important]
>Save *output* of command to a file and save *the error message* to another file


## Code

The error message is written to *stderr*, use **`2>` to redirect it**. For example:

```bash
foo > stdout.txt 2> stderr.txt
```

If we want to **save to the same file**

```bash
foo > allout.txt 2>&1
```



-----------
##  Recommended Notes

- 

- Stack Overflow
	- [How to redirect and append both standard output and standard error to a file with Bash](https://stackoverflow.com/questions/876239/how-to-redirect-and-append-both-standard-output-and-standard-error-to-a-file-wit)
	- [Redirect all output to file in Bash [duplicate]](https://stackoverflow.com/questions/6674327/redirect-all-output-to-file-in-bash)