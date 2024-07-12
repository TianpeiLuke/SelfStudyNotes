---
tags:
  - concept
  - math/linear_algebra
  - math/differential_geometry
keywords: 
topics: 
name: Laplace Expansion Theorem
date of note: 2024-07-10
---

## Concept Definition

>[!important]
>**Name**: Laplace Expansion Theorem

>[!important] Laplace Expansion by Minors along a Row or a Column
>The **determinant** may be defined inductively for $A = [a_{i,j}] \in \mathcal{L}(F^n)$ in the following way. 
>
>Assume that the determinant is defined over $\mathcal{L}(F^{n-1})$ and let $A_{i,j} \in \mathcal{L}(F^{n-1})$ denote the **submatrix** of $A \in \mathcal{L}(F^n)$ obtained by **deleting row** $i$ and **column** $j$ of $A$. 
>
>Then, for any $i, j \in \{ 1 \,{,}\ldots{,}\, n\}$, we have 
>$$
>\det(A) = \sum_{k=1}^{n}(-1)^{i + k} a_{i,k}\;\det(A_{i,k}) = \sum_{k=1}^{n}(-1)^{k + j} a_{k,j}\;\det(A_{k,j})
>$$
>The first sum is the **Laplace expansion by minors** *along row* $i$; the second sum is the **Laplace expansion by minors** *along column* $j$.

- [[Determinant of Linear Transformation]]
- [[Space of Bounded Linear Operators]]


>[!important] Laplace Expansion Theorem
>Let $A = [a_{i,j}] \in \mathcal{L}(F^n)$ and $k \in \{ 1 \,{,}\ldots{,}\,n \}$, and $\beta \subseteq \{ 1 \,{,}\ldots{,}\,n \}$ be any given *index set of cardinality* $k$.
>
>Then, 
>$$
>\det(A) = \sum_{\alpha} (-1)^{p(\alpha, \beta)} \det\left(A[\alpha, \beta]\right)\;\det\left(A[\alpha^c, \beta^c]\right)
>$$
>in which the sums are over *all index set* $\alpha \subseteq \{ 1 \,{,}\ldots{,}\, n\}$ of cardinality $k$, and $$p(\alpha, \beta) = \sum_{i\in \alpha}i + \sum_{j\in \beta}j.$$


## Explanation


## Interior Multiplication

>[!important]
>Consider $$A := \left[ \omega^i(X_{j}) \right] $$ for differential $1$-forms $\omega^i$ and vector fields $X_{j}$. 
>
>Then the **Laplace expansion by minors** is a special form of  **expansion of interior multiplication**
>$$
>\begin{align*}
>\det(A) &= \left(\omega^1 \,{\wedge}\ldots{\wedge}\, \omega^{n}\right)(X_{1} \,{,}\ldots{,}\, X_{j} \,{,}\ldots{,}\, X_{n}) \\
>&= (-1)^{j-1}\left(X_{j} \mathbin{\lrcorner } \left(\omega^1 \,{\wedge}\ldots{\wedge}\, \omega^{n}\right)\right) (X_{1} \,{,}\ldots{,}\, \widehat{X_{j}} \,{,}\ldots{,}\, X_{n})\\
>&= \sum_{k=1}^{n}(-1)^{k + j-2}\,\omega^{k}(X_{j})\;\left(\omega^1 \,{\wedge}\ldots{\wedge}\, \widehat{\omega^{k}} \,{\wedge}\ldots{\wedge}\, \omega^{n}\right)(X_{1} \,{,}\ldots{,}\, \widehat{X_{j}} \,{,}\ldots{,}\, X_{n})\\
>&= \sum_{k=1}^{n}(-1)^{k + j}\,\omega^{k}(X_{j})\;\left(\omega^1 \,{\wedge}\ldots{\wedge}\, \widehat{\omega^{k}} \,{\wedge}\ldots{\wedge}\, \omega^{n}\right)(X_{1} \,{,}\ldots{,}\, \widehat{X_{j}} \,{,}\ldots{,}\, X_{n})\\
>&=  \sum_{k=1}^{n}(-1)^{k + j}\,\omega^{k}(X_{j})\;\det \left(A_{k,j}\right).
>\end{align*}
>$$

- [[Coordinate Representation of Interior Multiplication]]
- [[Interior Multiplication]]
- [[Alternating Tensor]]


-----------
##  Recommended Notes and References


- [[Coordinate Representation of Interior Multiplication]]
- [[Interior Multiplication]]


- [[Determinant of Linear Transformation]]
- [[Matrix]]



- [[Matrix Analysis by Horn]] pp 8, 28