---
tags:
  - code
  - code_snippet
  - bash/sed
  - bash/awk
keywords: 
topics: 
language: bash
date of note: 2024-04-26
---

## Code Snippet Summary

>[!important]
>We need to **find and replace** **all occurrence** of a piece of text `original` with `new`  within a given file `file`


## Code

```bash
sed -i 's/original/new/g' file.txt
```

- `sed` = Stream EDitor
- `-i` = **in-place** (i.e. save back to the original file)
- The command string:
    - `s` = **the substitute command**
    - `original` = a regular expression describing the word to replace (or just the word itself)
    - `new` = the text to replace it with
    - `g` = global (i.e. replace all and not just the first occurrence)
- `file.txt` = the file name

- Similar to VIM command in [[Find a word and replace with another one]]

### Use `awk`

```bash
awk '{sub(/original/,"new")}1' file.txt > temp.txt && mv temp.txt file.txt
```

- AWK, being a text processing utility, is quite appropriate for such task. 
- It can do simple replacements and much more advanced ones based on [regular expressions](https://en.wikipedia.org/wiki/Regular_expression). It provides two functions: `sub()` and `gsub()`. 
	- The first one only replaces only *the first occurrence*, 
	- while the second - replaces occurrences *in whole string*.


-----------
##  Recommended Notes

- Ask Ubuntu:
	- [Find and replace text within a file using commands](https://askubuntu.com/questions/20414/find-and-replace-text-within-a-file-using-commands)