---
tags:
  - code
  - code_snippet
  - latex/bibtex
keywords: 
topics: 
language: latex
date of note: 2024-04-17
---

## Code Snippet Summary

>[!important]
>Use American Psychology Associations (APA) citations style


## Code

### Use `apacite` package

```latex
\documentclass{article}
\usepackage{apacite}
```

...

```latex
\bibliographystyle{apacite}
\bibliography{mybib.bib}
```

### Use `natbib` package

```latex
\usepackage{natbib} #Loads cite commands

\bibliographystyle{apa} #Tells Latex your bibliography style
\bibliography{BIBFILE} #Replace BIBFILE with the name of your bibliography file
```


- To cite things in text, you can use `\cite{citekey}` for `Author (YEAR)` output, and `\citep{citekey}` for `(Author, YEAR)`.

- Latex should format the authors based on the APA manual. If not, there is the `apacite` package, but I am not too sure how that works on a standard article class document or report class for this matter.



-----------
##  Recommended Notes

- [apacite package](http://ctan.org/tex-archive/biblio/bibtex/contrib/apacite/) and 
- [apa document class](http://www.ctan.org/tex-archive/macros/latex/contrib/apa)

- Tex Stack Exchange
	- [APA citations and bibliographies](https://tex.stackexchange.com/questions/485951/apa-citations-and-bibliographies)
	- [How do I use APA-style citations with BibTeX? [duplicate]](https://tex.stackexchange.com/questions/35809/how-do-i-use-apa-style-citations-with-bibtex)
	- [How to APA 6th in LaTex?](https://tex.stackexchange.com/questions/2628/how-to-apa-6th-in-latex)
