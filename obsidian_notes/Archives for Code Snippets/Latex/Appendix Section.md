---
tags:
  - code
  - code_snippet
  - latex/appendix
keywords: 
topics: 
language: latex
date of note: 2024-04-17
---

## Code Snippet Summary

>[!important]
>Add a section with **Appendix Section** Header



## Code

The `title` option and the `appendices` environment of the `appendix` package can do that:

```latex
\documentclass{article}

\usepackage[title]{appendix}

\begin{document}

\section{title 1}
\section{title 2}

\begin{appendices}
\section{Some Notation}

\section{Some More Notation}
\end{appendices}

\end{document}
```



-----------
##  Recommended Notes

- TEX Stack Exchange 
	- [Appendix Section Title](https://tex.stackexchange.com/questions/226481/appendix-section-title)