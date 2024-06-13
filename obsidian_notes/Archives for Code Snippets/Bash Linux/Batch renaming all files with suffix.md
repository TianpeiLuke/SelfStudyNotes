---
tags:
  - code
  - code_snippet
  - linux/rename
keywords: 
topics: 
language: linux
date of note: 2024-04-04
---

## Code Snippet Summary

>[!important]
>- add a **prefix string** `'prefix_str'`  to *all files* with *given suffix* `'.suffix'`


## Code

```bash
rename 's/^/prefix_str/' *.suffix
```

- `rename` command: rename files [reference](https://man7.org/linux/man-pages/man1/rename.1.html)
	- `rename [options] expression replacement file...`: 
		- **rename** will rename the specified files by replacing the first occurrence of _expression_ in their name by _replacement_.
	- **`-s`**, **`--symlink`**: Do not rename a symlink but **change where it points**.


>[!example]
>Change digits in filename to be of equal length.
>
> ```bash
> rename foo foo00 foo?
> rename foo foo0 foo??
> ```
> In this command, we can change *`foo1, ..., foo9, foo10, ..., foo278`* into *`foo001, ..., foo009, foo010, ..., foo278`*



-----------
##  Recommended Notes

- `rename` command: rename files [reference](https://man7.org/linux/man-pages/man1/rename.1.html)
- Stack Overflow: [Rename Files and Directories (Add Prefix)](https://stackoverflow.com/questions/4787413/rename-files-and-directories-add-prefix)