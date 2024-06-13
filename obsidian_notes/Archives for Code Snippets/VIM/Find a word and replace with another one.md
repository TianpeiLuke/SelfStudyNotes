---
tags:
  - code
  - code_snippet
  - vim/find_replace
keywords: 
topics: 
language: vim
date of note: 2024-04-17
---

## Code Snippet Summary

>[!important]
>**Find** all keywords `word1` and **replace** them with `word2`


## Code

- The general form of the **substitute** command is as follows:

```vi
:[range]s/{pattern}/{string}/[flags] [count]
```

- The command **searches each line** in `[range]` for a `{pattern}`, and **replaces** it with a `{string}`. `[count]` is a *positive integer* that multiplies the command.

- If no `[range]` and `[count]` are given, only the pattern found in the *current line* is replaced. The current line is the line where the cursor is placed.

### Find first occurrence and Replace

>[!example]
For example, to search for the **first occurrence** of the string ‘foo’ in the current line and **replace** it with ‘bar’, you would use:
> 
> ```vi
> :s/foo/bar/
> ```
> 

### Find All occurrence and Replace

>[!example]
To replace **all** occurrences of the search pattern in the current line, **add the `g` flag**:
> 
> ```vi
> :s/foo/bar/g
> ```
> 

### Search and Replace in Entire File

>[!example]
> If you want to *search and replace* the pattern in the **entire file**, use the **percentage character `%` as a range**. This character indicates a range from the first to the last line of the file:
> 
> ```vi
> :%s/foo/bar/g
> ```
> 

### Delete All occurrence of a keyword in Entire File

>[!example]
> If the `{string}` part is *omitted*, it is considered as an *empty string*, and the matched pattern is **deleted**. The following command **deletes all instances** of the string ‘foo’ in the current line:
> 
> ```vi
> :s/foo//g
> ```
> 

Instead of the slash character (`/`), you can use any other non-alphanumeric single-byte character except as a delimiter. This option is useful when you have the ‘/’ character in the search pattern or the replacement string.


-----------
##  Recommended Notes

- [[VIM Cheat Sheet]]

- [Find and Replace in Vim / Vi](https://linuxize.com/post/vim-find-replace/)
- Stack Overflow
	- [Find and replace strings in vim on multiple lines](https://stackoverflow.com/questions/19994922/find-and-replace-strings-in-vim-on-multiple-lines)