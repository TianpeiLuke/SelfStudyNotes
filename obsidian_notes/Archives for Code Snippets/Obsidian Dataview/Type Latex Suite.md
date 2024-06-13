---
tags:
  - code
  - code_snippet
  - obsidian/latex_suite
keywords: 
topics: 
language: obsidian/latex_suite
date of note: 2024-05-20
---

## Code Snippet Summary

>[!important] 
>Quick type Math Typing in Obsidian with **Latex Suite**


## Code

### [Auto-fraction](https://github.com/artisticat1/obsidian-latex-suite#auto-fraction)

>[!info]
>Lets you type "1/x" instead of "\frac{1}{x}".
> 
> For example, it makes the following expansions:
> 
> - `x/` → `\frac{x}{}`
> - `(a + b(c + d))/` → `\frac{a + b(c + d)}{}`
> 
> and moves the cursor inside the brackets.
> 
> Once done typing the denominator, **press Tab to exit the fraction**.

[![auto-fraction](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/auto-fraction.gif)](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/auto-fraction.gif)

### [Matrix shortcuts](https://github.com/artisticat1/obsidian-latex-suite#matrix-shortcuts)

>[!info]
> While inside a matrix, array, align, or cases environment,
> 
> - **Pressing Tab** will insert the "&" symbol
> - **Pressing Enter** will insert "\\" and move to a new line
> - **Pressing Shift + Enter** will move to the end of the next line (can be used to exit the matrix)

[![matrix shortcuts](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/matrix_shortcuts.gif)](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/matrix_shortcuts.gif)
### [Tabout](https://github.com/artisticat1/obsidian-latex-suite#tabout)

>[!info]
> - **Pressing Tab** while the cursor is **at the end of an equation** will **move** the cursor **outside **the $ symbols.
> - Otherwise, pressing Tab will advance the cursor to the **next closing bracket**: ), ], }, >, or |.

### [Preview inline math](https://github.com/artisticat1/obsidian-latex-suite#preview-inline-math)

>[!info]
> When the cursor is inside inline math, a popup window showing the rendered math will be displayed.

[![](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/inline_math_preview_1.png)](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/inline_math_preview_1.png)

[![](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/inline_math_preview_2.png)](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/inline_math_preview_2.png)

### [Color & highlight matching brackets](https://github.com/artisticat1/obsidian-latex-suite#color--highlight-matching-brackets)

>[!info]
> - **Matching brackets** are rendered in the same color, to help with readability.
> - When the cursor is **adjacent to a bracket**, that bracket and its pair will be highlighted.
> - When the cursor is **inside brackets**, the **enclosing brackets will be highlighted**.

[![color and highlight matching brackets demo](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/color_brackets.gif)](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/color_brackets.gif)

### [Visual snippets](https://github.com/artisticat1/obsidian-latex-suite#visual-snippets)

>[!info]
> Sometimes you want to annotate math, or cancel or cross out terms. Selecting some math with the cursor and typing
> 
> - "U" will *surround* it with "\underbrace".
> - "O" will *surround* it with "\overbrace".
> - "C" will surround it with "\cancel".
> - "K" will surround it with "\cancelto".
> - "B" will surround it with "\underset".

[![visual snippets](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/visual_snippets.gif)](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/visual_snippets.gif)

### [Auto-enlarge brackets](https://github.com/artisticat1/obsidian-latex-suite#auto-enlarge-brackets)

>[!info]
> When a snippet containing "\sum", "\int" or "\frac" is triggered, any enclosing brackets will be enlarged with "\left" and "\right".

[![auto-enlarge brackets](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/auto-enlarge_brackets.gif)](https://raw.githubusercontent.com/artisticat1/obsidian-latex-suite/main/gifs/auto-enlarge_brackets.gif)
### [Snippets](https://github.com/artisticat1/obsidian-latex-suite#snippets)

>[!info]
Snippets are formatted as follows:
> 
> ```ts
> {
>   trigger: string | RegExp,
>   replacement: string,
>   options: string,
>   priority?: number,
>   description?: string,
>   flags?: string,
> }
> ```
> 
> - `trigger` : The text that triggers this snippet.
>     - Triggers can also be regular expressions. [See here for more info.](https://github.com/artisticat1/obsidian-latex-suite/blob/main/DOCS.md#regex-snippets)
> - `replacement` : The text to replace the `trigger` with.
>     - Replacements can also be JavaScript functions. [See here for more info.](https://github.com/artisticat1/obsidian-latex-suite/blob/main/DOCS.md#function-snippets)
> - `options` : See below.
> - `priority` (optional): This snippet's priority. Snippets with higher priority are run first. Can be negative. Defaults to 0.
> - `description` (optional): A description for this snippet.
> - `flags` (optional): Flags for regex snippets.

#### [Options](https://github.com/artisticat1/obsidian-latex-suite#options)

>[!info]
> - `t` : Text mode. Only run this snippet outside math
> - `m` : **Math mode**. Only run this snippet inside math. Shorthand for both `M` and `n`
> - `M` : Block math mode. Only run this snippet inside a `$$ ... $$` block
> - `n` : Inline math mode. Only run this snippet inside a `$ ... $` block
> - `A` : **Auto**. Expand this snippet as soon as the trigger is typed. If omitted, the Tab key must be pressed to expand the snippet
> - `r` : [Regex](https://github.com/artisticat1/obsidian-latex-suite/blob/main/DOCS.md#regex-snippets). The `trigger` will be treated as a regular expression
> - `v` : [Visual](https://github.com/artisticat1/obsidian-latex-suite/blob/main/DOCS.md#visual-snippets). Only run this snippet on a selection. The trigger should be a single character
> - `w` : Word boundary. Only run this snippet when the trigger is preceded (and followed by) a word delimiter, such as `.`, `,`, or `-`.
> - `c` : Code mode. Only run this snippet inside a ` ``` ... ``` ` block
> 
> Insert **tabstops** for the cursor to jump to by writing "$0", "$1", etc. in the `replacement`.
> 
> For more details on writing snippets, including **regex** snippets and **function** snippets, [see the **documentation** here](https://github.com/artisticat1/obsidian-latex-suite/blob/main/DOCS.md). You can [view snippets written by others and share your own snippets here](https://github.com/artisticat1/obsidian-latex-suite/discussions/50).
> 



-----------
##  Recommended Notes


- Github [Readme](https://github.com/artisticat1/obsidian-latex-suite)
