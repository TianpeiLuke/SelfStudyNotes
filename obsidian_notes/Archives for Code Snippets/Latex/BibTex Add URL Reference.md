---
tags:
  - code
  - code_snippet
  - latex/bibtex
keywords: 
topics: 
language: latex
date of note: 2024-04-12
---

## Code Snippet Summary

>[!important]
>Create reference on Website URL


## Code

```latex
\usepackage{url} 
% or
\usepackage{hyperref}
```


```latex
@misc{name,
  author = {Name},
  title = {{Title}},
  howpublished = "\url{URLs}",
  year = {2024}, 
  note = "[Online; accessed YYYY-mm-dd]"
}
```

Depends what BibTeX style you're using.

- `howpublished={\url{http://my.url.com/}}`: 
- `note={\url{http://...}}`
- `url={http://...}`


-----------
##  Recommended Notes

- Stack Exchange  [How to add a URL to a LaTeX bibtex file?](https://tex.stackexchange.com/questions/35977/how-to-add-a-url-to-a-latex-bibtex-file)