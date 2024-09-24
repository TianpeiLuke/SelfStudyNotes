---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - principal_submatrix
  - leading_principal_submatrix
  - trailing_principal_submatrix
topics:
  - matrix_analysis
  - linear_algebra
name: Principal Submatrix
date of note: 2024-09-23
---

## Concept Definition

>[!important]
>**Name**: Principal Submatrix

![[Partition of Matrix and Block Matrix#^91291d]]

### Principal Submatrix

>[!important] Definition
>Let $A\in M_{m,n}(F)$, and $\alpha \subset \{ 1\,{,}\ldots{,}\,m \}$, $\alpha \subset \{1\,{,}\ldots{,}\,n  \}$ be an index set.
>
>Then the **priniciple submatrix** of $A$ is a submatrix of $A$ with *same row and column indices* $$A[\alpha] := A[\alpha, \alpha] \text{ or } A_{\alpha, \alpha}$$

^2c9003

>[!important] Definition
>Let $A\in M_{m,n}(F)$.
>
>- The *principal submatrix* of $A$ with index $\alpha = \{ 1\,{,}\ldots{,}\, k\}$ is called the **leading principal submatrix.** i.e. $$A[1:k, 1:k],\;\; A[\{1\,{,}\ldots{,}\,k\}, \{1\,{,}\ldots{,}\,k\}]$$
>- The *principal submatrix* of $A$ with index $\alpha = \{ k\,{,}\ldots{,}\, n\}$ is called the **trailing principal submatrix.**  i.e. $$A[k:n, k:n],\;\; A[\{k\,{,}\ldots{,}\,n\}, \{k\,{,}\ldots{,}\,n\}]$$

^f285eb

>[!important] Definition
>We can also indicate a submatrix via **deletion**. 
>- Denote $$\alpha^{c} = \{ 1\,{,}\ldots{,}\,m \} \setminus \alpha; \quad \beta^{c} = \{ 1\,{,}\ldots{,}\,n \} \setminus \beta.$$
>- Then $$A[\alpha^c, \beta^c]$$ is the submatrix obtained by **deleting** rows indexed by $\alpha$, and columns indexed by $\beta$.

### Minor


- [[Minor and Principal Minor]]





## Explanation

>[!info]
>For $A\in M_{n}$, there are $$n \choose k$$ **principal submatrices** of size $k$.





-----------
##  Recommended Notes and References


- [[Partition of Matrix and Block Matrix]]
- [[Schur Complement and Inversion of Block Matrix]]

- [[Positive Semidefinite Transformation]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 17
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 100
- [[Matrix Computations by Golub]] pp 24
- [[Finite Dimensional Vector Spaces by Halmos]] pp 167