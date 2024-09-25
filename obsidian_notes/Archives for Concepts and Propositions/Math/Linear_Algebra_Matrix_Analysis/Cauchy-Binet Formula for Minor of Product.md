---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - cauchy_binet_formula
topics:
  - matrix_analysis
  - linear_algebra
name: Cauchy-Binet Formula for Minor of Product
date of note: 2024-09-23
---

## Concept Definition

>[!important]
>**Name**: Cauchy-Binet Formula for Minor of Product

>[!important] Theorem (Cauchy-Binet Formula)
>Let $A\in M_{m,k}(F)$, and $B\in M_{k,n}(F)$, let $$C = A\,B.$$
>Furthermore, let 
>- $1 \le r \le \min\left\{ m, k, n \right\}$, and 
>- $\alpha \subseteq \left\{ 1\,{,}\ldots{,}\,m \right\},$ and
>- $\beta \subseteq \left\{ 1\,{,}\ldots{,}\,n \right\}$ be **subsets of indices.**
>- And both $\alpha$ and $\beta$ has the **cardinality** $r$, i.e. $$\left\lvert \alpha \right\rvert = \lvert \beta \rvert = r.$$
>
>Then an expression of **the $(\alpha,\beta)$ minor** of $C$ is 
>$$
>\det\left( C[\alpha, \beta] \right) = \sum_{\gamma}\,\det\left( A[\alpha, \gamma] \right)\,\det\left( B[\gamma, \beta] \right)
>$$
>where the sum is over *all index sets* $\gamma \subseteq \left\{ 1\,{,}\ldots{,}\, k\right\}$ with **cardinality** $r$.

- [[Partition of Matrix and Block Matrix]]
- [[Determinant of Linear Transformation]]


## Explanation

>[!info]
>This useful formula can be remembered because of its similarity in appearance to the *formula for matrix multiplication*. This is no accident, since it is equivalent to **multiplicativity of the compound matrix**.
>$$
>C_{r}(AB) = C_{r}(A)\,C_{r}(B)
>$$
>where the $(\alpha,\beta)$ entry of the **compound matrix** is
>$$
>C_{r}(A)_{\alpha, \beta} = \det\left( A[\alpha, \beta] \right) 
>$$
>and $C_{r}(A)$ is of shape $${m \choose r} \times {n \choose r}$$



-----------
##  Recommended Notes and References


- [[Laplace Expansion Theorem]]
- [[Minor and Principal Minor]]


- [[Conformal Partitions of Matrices]]
- [[Principal Submatrix]]
- [[Partition of Matrix and Block Matrix]]
- [[Matrix]]

- [[Matrix Analysis by Horn]] pp 28