---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - ldu_factorization_symmetric
  - symmetric_matrix
topics:
  - matrix_analysis
  - numerical_linear_algebra
name: LDU Factorization of Symmetric Matrix
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: LDL^T Factorization of Symmetric Matrix

![[LU Factorization of Matrix#^62518f]]

>[!important] Proposition ($LDL^{T}$ Factorization)
>Let $A\in M_{n}$ be a **Hermitian matrix** and all of its **leading principal submatrices** are nonsingular $$\det \left( A[1:k, 1:k] \right) \neq 0, \quad k=1\,{,}\ldots{,}\,n-1.$$
>
>Then there exists a **unit lower triangular matrix** $L$ and a **diagonal matrix** $$D = \text{diag}(d_{1}\,{,}\ldots{,}\,d_{n})$$ such that $$A = L\,D\,L^{T}.$$
>
>And the factorization is **unique**.

^951558

- [[Hermitian or Symmetric Matrix]]
- [[LU Factorization of Matrix]]





## Explanation





-----------
##  Recommended Notes and References


- [[Hermitian or Symmetric Matrix]]
- [[LU Factorization of Matrix]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Matrix]]
- [[Orthogonal Group]]
- [[Unitary Group]]
- [[Gaussian Elimination for Solving Linear System]]


- [[Numerical Linear Algebra by Trefethen]] pp 
- [[Matrix Computations by Golub]] pp 156 - 159
- [[Matrix Analysis by Horn]] pp 218 - 221