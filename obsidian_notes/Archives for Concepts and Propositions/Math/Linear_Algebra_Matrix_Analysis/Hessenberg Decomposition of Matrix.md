---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - hessenberg_decomposition
topics:
  - matrix_analysis
  - numerical_linear_algebra
name: Hessenberg Decomposition of Matrix
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Hessenberg Decomposition of Matrix

### Hessenberg Decomposition

>[!important] Proposition
>Let $A\in M_{n}$. 
>
>There exists an **unitary matrix** $U\in \mathcal{U}(n)$ such that $$A = U\,H\,U^{*}$$ where $H$ is a **Hessenberg matrix**.

- [[Hessenberg Matrix]]

![[Krylov Subspace and Krylov Matrix#^e38b83]]

### QR Factorization

>[!important] Theorem
>Let $A\in \mathbb{R}^{n\times n}$ and $Q = [q_{1}\,{,}\ldots{,}\,q_{n}]\in \mathcal{O}(n)$ be **orthogonal matrix**.
>
>Then $$Q^{T}AQ = H$$ is an **unreduced upper Hessenberg matrix** *if and only if*  $$Q^{T}K(A, q_{1}, n) = R$$ is **nonsingular** and **upper triangular**.

^40c613

- [[Triangular Matrix and Block Triangular Matrix]]
- [[Krylov Subspace and Krylov Matrix]]
- [[QR Factorization of Matrix]]

### Implicit Q Theorem

>[!info]
>Hessenberg decomposition is **not unique** in general. 
>
>But it is **unique** if the **first columns is specified**.

>[!important] Implicit Q Theorem
>Let $A\in \mathbb{R}^{n\times n}$
>
>Suppose $Q = [q_{1}\,{,}\ldots{,}\,q_{n}], V= [v_{1}\,{,}\ldots{,}\,v_{n}]\in \mathcal{O}(n)$ are *orthogonal matrices* with property that $$Q^{T}A Q = H, \quad V^{T}AV= G$$ are both **upper Hessenberg**.
>
>Let $k$ denote the **smallest integer** such that $H_{k,k-1} =0$ with convention that $k=n$ if $H$ is *unreduced*.
>- If $q_{1} = v_{1}$, then $$q_{i} = \pm v_{i}, \;\;\text{ and }\;\; |H_{i,i-1}| = |G_{i,i-1}|, \quad i=1\,{,}\ldots{,}\,k-2$$
>- Moreover, if $k < n$, then $$G_{k+1, k} = 0.$$


## Explanation





## Hessenberg Reduction via Householder Transformation

- [[Hessenberg Reduction via Householder Transformation]]

## Symmetric Case

- [[Tridiagonal Decomposition of Symmetric Matrix]]
- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]


-----------
##  Recommended Notes and References


- [[Unitary Similarity and Unitary Diagonalizable]]
- [[QR Factorization of Matrix]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Hermitian or Symmetric Matrix]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

- [[Tridiagonal System of Equations]]
- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]

- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 378 - 381