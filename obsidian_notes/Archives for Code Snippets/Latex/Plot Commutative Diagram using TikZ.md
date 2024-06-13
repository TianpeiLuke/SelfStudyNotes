---
tags:
  - code
  - code_snippet
  - latex/figures
keywords: 
topics: 
language: latex
date of note: 2024-04-07
---

## Code Snippet Summary


>[!important]
>Plot commutative diagram using **tikz-cd** package


## Code

```latex
\usepackage{tikz-cd}
```

```latex
\[
  \begin{tikzcd}
     M  \arrow{r}{\pi}  & N   \arrow[l, bend left,  "\sigma"] 
  \end{tikzcd}
\] 
```

![[tikz-fig1.png]]


```latex
\[
  \begin{tikzcd}
     M  \arrow[swap]{d}{\pi} \arrow[dr, "F \circ \pi"]  & \\
     N   \arrow[r, swap,  "F"]  & P.
  \end{tikzcd}
\] 
```

![[tikz-fig2.png]]


```latex
\[
  \begin{tikzcd}
     M  \arrow[swap]{d}{\pi} \arrow[dr, "F"]  & \\
     N   \arrow[r, swap, dashed,  "\widetilde{F}"]  & P.
  \end{tikzcd}
\] 
```

![[tikz-fig3.png]]


```latex
\[
  \begin{tikzcd}
     & M  \arrow[swap]{dl}{\pi_1} \arrow[dr, "\pi_2"]  & \\
     N_1   \arrow[rr, swap, dashed,  "F"]  & & N_2.
  \end{tikzcd}
\] 
```

![[tikz-fig4.png]]

-----------
##  Recommended Notes

- **tikz-cd** – Create commutative diagrams with **TikZ**:  [ctan.org](https://ctan.org/pkg/tikz-cd?lang=en)
	- [https://ctan.org/tex-archive/graphics/pgf/contrib/tikz-cd](https://ctan.org/tex-archive/graphics/pgf/contrib/tikz-cd?lang=en)
- Tex Stack Exchange: 
	- [How to draw commutative diagrams?](https://tex.stackexchange.com/questions/115783/how-to-draw-commutative-diagrams)
	- [How to make a commutative diagram using {tikz-cd}? (duplicate)](https://tex.stackexchange.com/questions/402572/how-to-make-a-commutative-diagram-using-tikz-cd)
	- [Arrows inside a commutative diagram using tikzcd](https://tex.stackexchange.com/questions/495457/arrows-inside-a-commutative-diagram-using-tikzcd)
	- [TikZ-cd Diagrams Side-by-Side](https://tex.stackexchange.com/questions/570141/tikz-cd-diagrams-side-by-side)
