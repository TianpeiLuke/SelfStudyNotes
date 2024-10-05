---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - tridiagonal_decomposition
topics:
  - numerical_linear_algebra
name: Tridiagonal Reduction of Symmetric Matrix via Householder Transformation
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Tridiagonal Reduction of Symmetric Matrix via Householder Transformation

![[Householder Transformation and Householder Reflection#^082feb]]

>[!important] Definition
>Let $A\in \mathbb{R}^{n\times n}$ be a **symmetric matrix**.
>
>The following **Householder tridiagonalization** algorithm overwrites $A$ with $$T = Q^{T}AQ$$ where $$Q = P_{1}\,{}\ldots{}\,P_{n-2}$$ is the product of Householder transformation:
>- *Require*: $A\in \mathbb{R}^{n\times n}$  symmetric
>- For $k=1\,{,}\ldots{,}\,n-2$:
>	- Compute the **houeholder vector** $$(\beta^{(k)}, v^{(k)}) = \text{Householder}(A_{\{ k+1:n \}, k})$$
>	- Compute $p$ and $w$ for Householder transformation on the trailing principal submatrix  
>		- $$p^{(k)} = \beta^{(k)}\,A_{\{ k+1:n \}, \{ k+1:n \}}\,v^{(k)}$$
>		- $$w^{(k)} = p^{(k)} - \frac{1}{2} \beta^{(k)}\left((p^{(k)})^{T}v^{(k)}\right)v^{(k)}$$
>	- Convert $(k+1,k)$ and $(k, k+1)$ entry to be the off-diagonal norm as the result of Householder transformation 
>		- $$A_{k+1,k} \leftarrow \lVert A_{\{ k+1:n \}, k} \rVert_{2} $$
>		- $$A_{k, k+1} \leftarrow A_{k+1,k}$$
>	- Apply the **Householder transformation** in both rows and columns to the *trailing principal submatrix* via **rank-2 update** $$A_{\{ k+1:n \}, \{ k+1:n \}} \leftarrow A_{\{ k+1:n \}, \{ k+1:n \}} - v^{(k)}(w^{(k)})^{T} - w^{(k)}\,(v^{(k)})^{T}$$
>- *Return* the tridiagonal matrix $T$ which overwrites $A$.
>	- the matrix $Q$ can be stored in factored form $P_{k}$ in off-diagonal portion of $A$

^7e7a23



>[!important]
>This algorithm requires  $$\frac{4}{3}n^3$$ flops.

## Explanation

### Tridiagonal Reduction for Submatrix using Lanczos Process

- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]

|                              | $A = QR$ <br>**QR Factorization**                                      | $A= QTQ^{*}$ <br>**Tridiagonal Factorization**                                                                     |
| ---------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Orthogonal Structuring       | **Householder Transformation**<br><br>[[Householder QR Factorization]] | **Householder Transformation**<br><br>[[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]] |
| Structured Orthogonalization | **Gram-Schmidt process**<br><br>[[Gram-Schmidt Orthogonalization]]     | **Lanczos process**<br><br>[[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]                         |





-----------
##  Recommended Notes and References


- [[Tridiagonal Decomposition of Symmetric Matrix]]
- [[Power Iteration and Inverse Iteration for General Eigenvalue Problem]]
- [[Householder Transformation and Householder Reflection]]

- [[Linear Span over a Set of Vectors]]
- [[Orthogonal Complement of Hilbert Spaces]]
- [[QR Factorization of Matrix]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Hermitian or Symmetric Matrix]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

- [[Tridiagonal System of Equations]]
- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]

- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 458 - 460