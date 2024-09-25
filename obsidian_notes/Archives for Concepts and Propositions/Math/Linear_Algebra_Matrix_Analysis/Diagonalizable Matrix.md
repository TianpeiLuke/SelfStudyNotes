---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - diagonalizable_matrix
  - similarity_relation_linear_map
topics:
  - matrix_analysis
  - linear_algebra
name: Diagonalizable Matrix
date of note: 2024-09-16
---

## Concept Definition

>[!important]
>**Name**: Diagonalizable Matrix

![[Similarity Relation between Linear Maps and Matrices#^5ebca6]]

>[!important] Definition
>If $A \in M_{n}$ is *similar* to a *diagonal matrix*, then $A$ is said to be **diagonalizable**.
>
>That is, $A$ is **diagonalizable** if there exists an non-singular matrix $S\in GL(n)$ such that $$A = S\,\Lambda\,S^{-1}$$ where $\Lambda := \text{diag}(\lambda_{1} \,{,}\ldots{,}\,\lambda_{n})$ is a diagonal matrix.

- [[General Linear Group]]

### Unitarily Diagonalizable 

![[Unitary Similarity and Unitary Diagonalizable#^be2b64]]

- [[Unitary Similarity and Unitary Diagonalizable]]

## Explanation



## Eigenvalues and Eigenvectors

### Independent Eigenvectors

>[!important] Theorem
>Let $A\in M_{n}$ is a $n\times n$ matrix. 
>
>Then $A$ is **similar** to a **block matrix** of the form
>$$
>\left[ 
>\begin{array}{cc}
> \Lambda & C \\[5pt] 
> 0 & D
>\end{array} 
>\right] 
>$$
>where $$\Lambda = \text{diag}\left(\lambda_{1} \,{,}\ldots{,}\,\lambda_{k}\right), \quad D\in M_{n-k},\quad 1\le k \le n$$
>
>*if and only if* there are $k$ **linearly independent** vectors in $\mathbb{C}^{n}$, each of which is an **eigenvector** of $A$.
>
>If $A$ is **similar** to a matrix of above form, then the **diagonal entries** of $\Lambda$ are **eigenvalues** of $A$.

- [[Eigenvalue and Eigenvector for Linear Map]]

>[!important] Corollary
>A matrix $A \in M_{n}$ is **diagonalizable** *if and only if* there are **$n$ linearly independent** vectors, each of which is an **eigenvector** of $A$.
>
>In other word, a matrix $A \in M_{n}$ is **diagonalizable** *if and only if* $A$ has **$n$ linearly independent eigenvectors**.


>[!important] Corollary
>If $x^{(1)}\,{,}\ldots{,}\,x^{(n)}$ are **linearly independent eigenvectors** of $A$, and if $$S = \left[ x^{(1)}\,{,}\ldots{,}\,x^{(n)} \right],$$ then $$S^{-1}\,A\,S$$ is a **diagonal matrix.**
>

>[!important] Corollary
>If a matrix $A \in M_{n}$ is **similar** to a diagonal matrix $\Lambda= \text{diag}(\lambda_{1}\,{,}\ldots{,}\,\lambda_{n})$, i.e. $$A \sim \text{diag}(\lambda_{1}\,{,}\ldots{,}\,\lambda_{n}),$$ then the diagonal entries of $\Lambda$, $\lambda_{i}$, are all **eigenvalues** of $A$. 

### Distinct Eigenvalues

![[Eigenspace and Spectrum for Linear Map#^3d4672]]

- [[Eigenspace and Spectrum for Linear Map]]

>[!important] Theorem
>If $A \in M_{n}$ has $n$ **distinct eigenvalues**, then $A$ is **diagonalizable**.


## Jordan Canonical Forms

- [[Jordan Canonical Form]]




-----------
##  Recommended Notes and References


- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Similarity Relation between Linear Maps and Matrices]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

- [[Diagonal Matrix and Block Diagonal Matrix]]



- [[Matrix Analysis by Horn]] pp 59 - 61
- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Computations by Golub]] pp 353 - 354