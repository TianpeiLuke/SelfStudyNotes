---
tags:
  - code
  - code_snippet
  - vim/search
keywords: 
topics: 
language: vim
date of note: 2024-04-17
---

## Code Snippet Summary

>[!important]
>Use VIM command to search for a given keyword


## Code

like this:

```
/\<word\>
```

`\<` means beginning of a word, and `\>` means the end of a word,


>[!quote]
>VIM provides a shortcut for this. If you already have _word_ on screen and you want to find other instances of it, you can put the cursor on the word and press `'*'` to search forward in the file or `'#'` to search backwards.
>[link](https://stackoverflow.com/questions/458915/searching-word-in-vim)

>[!quote]
>If you are working in Ubuntu,follow the steps:
> 
> 1. Press `/` and type word to search
> 2. To search in forward press 'SHIFT' key with `*` key
> 3. To search in backward press 'SHIFT' key with `#` key



-----------
##  Recommended Notes

- [[VIM Cheat Sheet]]

- [https://www.warp.dev/terminus/searching-in-vim](https://www.warp.dev/terminus/searching-in-vim)
- Stack Overflow:
	- [Searching word in vim?](https://stackoverflow.com/questions/458915/searching-word-in-vim)