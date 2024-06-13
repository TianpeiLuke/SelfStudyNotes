---
tags:
  - code
  - code_snippet
  - vim/indent
keywords: 
topics: 
language: vim
date of note: 2024-04-18
---

## Code Snippet Summary

>[!important]
>Add same length of indents to multiple lines in vim


## Code

- **Remove the first 2 characters of every line:**

```
:%normal 2x
```

### Substitute a pattern with empty 

- **Remove first 2 characters of every line, only if they're spaces:**

```
:%s/^  /
```

### With indentation

- **Move indentation to left for every line:**

```
:%normal <<
```

- If what you're really doing is changing indentation, you can use the `<` command to decrease it, or the `>` command to increase it. Set `shiftwidth` to control how far it shifts, e.g.

-----------
##  Recommended Notes

- [[VIM Cheat Sheet]]

- Stack Overflow:
	- [vim: delete the first 2 spaces for multiple lines](https://stackoverflow.com/questions/6961705/vim-delete-the-first-2-spaces-for-multiple-lines)