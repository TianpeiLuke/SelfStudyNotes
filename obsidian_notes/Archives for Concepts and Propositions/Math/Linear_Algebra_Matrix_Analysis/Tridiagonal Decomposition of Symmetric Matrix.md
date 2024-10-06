---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - tridiagonal_decomposition
topics:
  - matrix_analysis
  - numerical_linear_algebra
name: Tridiagonal Decomposition of Symmetric Matrix
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Tridiagonal Decomposition of Symmetric Matrix

### Tridiagonal Decomposition

>[!important] Proposition
>Let $A\in M_{n}$ be a **Hermitian matrix**. 
>
>There exists an **unitary matrix** $U\in \mathcal{U}(n)$ such that $$A = U\,T\,U^{*}$$ where $T$ is a **symmetric** and **tridiagonal matrix**.

^616da0

- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]

### QR Factorization

![[Krylov Subspace and Krylov Matrix#^e38b83]]


>[!important] Theorem
>Let $A\in \mathbb{R}^{n\times n}$ be **symmetric matrix**, $Q=[q_{1}\,{,}\ldots{,}\,q_{n}]\in \mathcal{Q}(n)$ be *orthogonal matrix* and $$Q^{T}AQ = T$$ is the **tridiagonal decomposition** of $A$. 
>
>Then $$Q^{T}K(A, q_{1}, n) = R$$ is **upper triangular**.
>- If $R$ is *nonsingular*, then $T$ is **unreduced.**
>- If $R$ is *singular* and $k$ is smallest interger such that $R_{kk}=0$, then $k$ is also the **smalest index** such that $T_{k,k-1}=0$

^d21ddc

- [[Hermitian or Symmetric Matrix]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Krylov Subspace and Krylov Matrix]]
- [[QR Factorization of Matrix]]

### Implicit Q Theorem

>[!info]
>Tridiagonal decomposition is **unique** if the **first columns is specified**.

>[!important] Implicit Q Theorem
>Let $A\in \mathbb{R}^{n\times n}$ be **symmetric** matrix.
>
>Suppose $Q = [q_{1}\,{,}\ldots{,}\,q_{n}], V= [v_{1}\,{,}\ldots{,}\,v_{n}]\in \mathcal{O}(n)$ are *orthogonal matrices* with property that $$Q^{T}A Q = T, \quad V^{T}AV= S$$ are both **tridiagonal matrices**.
>
>Let $k$ denote the **smallest integer** such that $T_{k,k-1} =0$ with convention that $k=n$ if $T$ is *unreduced*.
>- If $q_{1} = v_{1}$, then $$q_{i} = \pm v_{i}, \;\;\text{ and }\;\; |T_{i,i-1}| = |S_{i,i-1}|, \quad i=1\,{,}\ldots{,}\,k-2$$
>- Moreover, if $k < n$, then $$S_{k+1, k} = 0.$$


## Explanation

>[!info]
>Compare with the following:

![[Hessenberg Decomposition of Matrix#^40c613]]

- [[Hessenberg Decomposition of Matrix]]


>[!info]
>**Tridiagonal decomposition** is the intermediate steps to converge to **symmetric Schur form** or the **diagonal matrix of eigenvalues**.
>$$
>T^{(1)} \to T^{(2)} \,{\to}\ldots{\to}\, \Lambda
>$$
>where the off-diagonal terms in both *lower and upper triangular part* of $T$ *converges to zero*.
>$$
>H^{(k)}_{\{ i+1:n \},i} = H^{(k)}_{i,\{ i+1:n \}}  \to 0.
>$$

^8a0810

## Tridiagonal Decomposition via Householder Transformation

- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]



-----------
##  Recommended Notes and References


- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]

- [[Unitary Similarity and Unitary Diagonalizable]]
- [[QR Factorization of Matrix]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Hermitian or Symmetric Matrix]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

- [[Tridiagonal System of Equations]]
- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]

- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 458 - 460
- [[Convex Optimization by Boyd]] pp 326