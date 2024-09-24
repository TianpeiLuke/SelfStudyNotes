---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - matrix_partition
  - block_matrix
topics:
  - matrix_analysis
  - linear_algebra
name: Partition of Matrix and Block Matrix
date of note: 2024-09-23
---

## Concept Definition

>[!important]
>**Name**: Partition of Matrix and Block Matrix

>[!important] Definition
>A **partition** of a matrix is a *decomposition* of the matrix into **submatrices** such that each entry of the original matrix is in *one and only one* of the submatrices.
>
>In particular, let $\alpha_{1} \,{,}\ldots{,}\,\alpha_{t}$ constitute a *partition* of $\{ 1\,{,}\ldots{,}\,m \}$, and $\beta_{1} \,{,}\ldots{,}\, \beta_{s}$ constitute a *partition* of $\{ 1\,{,}\ldots{,}\,n \}$. Then $$A[\alpha_{i}, \beta_{j}], \quad i=1\,{,}\ldots{,}\,t, j=1\,{,}\ldots{,} s,$$ form a **partition** of matrix $A\in M_{m,n}(F)$.
>
>Here, we denote by $$A[\alpha, \beta], \text{ or }A_{\alpha, \beta}$$ the submatrix of entries that lie in the *rows* of $A$ indexed by $\alpha$, and *columns* indexed by $\beta$.

^91291d

- [[Partition of Set]]

>[!important] Definition
>Let $A\in M_{m,n}$ and 
>$$\bigcup_{i=1}^{t}\alpha_{i} = \{ 1\,{,}\ldots{,}\,m \}; \quad \bigcup_{j=1}^{s}\beta_{j} = \{ 1\,{,}\ldots{,}\,n \}$$ with $\alpha_{i}\cap \alpha_{j} =\emptyset$, $\beta_{i}\cap \beta_{j} =\emptyset.$
>
>Then the *partition of matrix* $A[\alpha_{i}, \beta_{j}], i,j$ forms a **block matrix**
>$$
>A = \left[ \begin{array}{cccc}A_{\alpha_{1}, \beta_{1}} & A_{\alpha_{1}, \beta_{2}} & \cdots & A_{\alpha_{1}, \beta_{s}} \\[5pt] A_{\alpha_{2}, \beta_{1}} & A_{\alpha_{2}, \beta_{2}} & \cdots & A_{\alpha_{2}, \beta_{s}} \\[5pt] \cdots & \cdots & \cdots & \cdots \\[5pt] A_{\alpha_{t}, \beta_{1}} & A_{\alpha_{t}, \beta_{2}} & \cdots & A_{\alpha_{t}, \beta_{s}}\end{array} \right]. 
>$$
>- Each submatrix $$A_{i,j} := A[\alpha_{i}, \beta_{j}]$$ is called a **block**.




## Explanation


### Principle Submatrix

![[Principal Submatrix#^2c9003]]

![[Principal Submatrix#^f285eb]]

- [[Principal Submatrix]]

### Minor and Principle Minor

![[Minor and Principal Minor#^35f53b]]

![[Minor and Principal Minor#^ed00ef]]

- [[Minor and Principal Minor]]

## Inverse of Block Matrix

![[Schur Complement and Inversion of Block Matrix#^0d76ad]]

- [[Schur Complement and Inversion of Block Matrix]]



-----------
##  Recommended Notes and References



- [[Marginal and Conditional Distribution of Gaussian]]
- [[Schur Complement and Inversion of Block Matrix]]
- [[Laplace Expansion Theorem]]


- [[Positive Semidefinite Transformation]]
- [[Determinant of Linear Transformation]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 17
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 
- [[Matrix Computations by Golub]] pp 
- [[Finite Dimensional Vector Spaces by Halmos]] pp 