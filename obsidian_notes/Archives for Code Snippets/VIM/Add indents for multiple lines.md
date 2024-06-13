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



## Indentation Command in VIM


>[!info]
> In the commands below, "re-indent" means "indent lines according to your [indentation settings](http://vim.wikia.com/wiki/VimTip83)." [`shiftwidth`](http://vimdoc.sourceforge.net/htmldoc/options.html#%27shiftwidth%27) is the primary variable that controls indentation.


### General Commands

- Direct indent
```
>>   Indent line by shiftwidth spaces
<<   De-indent line by shiftwidth spaces
5>>  Indent 5 lines
5==  Re-indent 5 lines
```

- for braced and bracketed block

```plain
>%   Increase indent of a braced or bracketed block (place cursor on brace first)
=%   Reindent a braced or bracketed block (cursor on brace)
<\%  Decrease indent of a braced or bracketed block (cursor on brace)
]p   Paste text, aligning indentation with surroundings
```

- Re-Indent with block
```
=i{  Re-indent the 'inner block', i.e. the contents of the block
=a{  Re-indent 'a block', i.e. block and containing braces
=2a{ Re-indent '2 blocks', i.e. this block and containing block
```

- Increase indent of block
```
>i{  Increase inner block indent
<i{  Decrease inner block indent
```

>[!info]
>You can replace `{` with `}` or `B`, e.g. `=iB` is a valid block indent command. Take a look at ["Indent a Code Block"](http://vim.wikia.com/wiki/Indent_a_code_block) for a nice example to try these commands out on.

- Also, remember that

```
.    Repeat last command
```

### Re-indenting complete files

- Another common situation is requiring *indentation to be **fixed** throughout a source file*:

```
gg=G  Re-indent entire buffer
```

- And below are some of the simple and elegant commands used to indent lines quickly in Vim or gVim.

```plain
==    To indent the current line
=G    To indent the all the lines below the current line
n==   To indent `n` lines below the current line
=%    To indent a block of code, go to one of the braces and use command
```

### Visual Mode

```
Vjj> Visually mark and then indent three lines
```

### Insert Mode

- These commands apply to the current line:

```
CTRL-t   insert indent at start of line
CTRL-d   remove indent at start of line
0 CTRL-d remove all indentation from line
```




-----------
##  Recommended Notes

 - [Vim documentation](http://vimdoc.sourceforge.net/) and 
 - [Vim wiki](http://vim.wikia.com/)

- Stack Overflow:
	- [Indenting a bunch of lines in Vim](https://stackoverflow.com/questions/2332340/indenting-a-bunch-of-lines-in-vim)
	- [Indent several lines with VIM?](https://unix.stackexchange.com/questions/16939/indent-several-lines-with-vim)
	- [Indent multiple lines quickly in vi](https://stackoverflow.com/questions/235839/indent-multiple-lines-quickly-in-vi)
	- [Indenting source code](http://vim.wikia.com/wiki/VimTip83)