---
tags:
  - code
  - code_snippet
  - linux/find
  - bash/find
keywords: 
topics: 
language: bash
date of note: 2024-06-30
---

## Code Snippet Summary

>[!important]
>- Find all files with given suffix *except for* the **symlink**
>- Remove these files



## Code

>[!info]
>- Find `*.jpg*` files *except for* symlink
>- Save the filename into a `txt` file
>- Find `*.png*` files *except for* symlink
>- *Append* the filename into a `txt` file

```bash
find *.jpg -type f > 0_filenames.txt
find *.png -type f >> 0_filenames.txt

mkdir 0_filenames
mv 0_filenames.txt 0_filenames

find *.jpg -type f -delete
find *.png -type f -delete
```


>[!info]
>Remove `*.jpg*` files except for symlink

```bash
find *.jpg -type f -delete
```






-----------
##  Recommended Notes

- `find` command [official page](https://man7.org/linux/man-pages/man1/find.1.html)
- [How to Use the find Command in Linux](https://www.howtogeek.com/771399/how-to-use-the-find-command-in-linux/)


- Stack Overflow [linux remove files in a directory except symlinks? [closed]](https://stackoverflow.com/questions/17345111/linux-remove-files-in-a-directory-except-symlinks)
- Stack Overflow [How to append output to the end of a text file](https://stackoverflow.com/questions/6207573/how-to-append-output-to-the-end-of-a-text-file)
- Stack Overflow [How to concatenate string variables in Bash](https://stackoverflow.com/questions/4181703/how-to-concatenate-string-variables-in-bash)