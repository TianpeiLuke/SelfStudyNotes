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
>**Name**: $LDL^T$ Factorization of Symmetric Matrix

![[LU Factorization of Matrix#^62518f]]

>[!important] Proposition ($LDL^{T}$ Factorization)
>Let $A\in M_{n}$ be a **Hermitian matrix** and all of its **leading principal submatrices** are nonsingular $$\det \left( A[1:k, 1:k] \right) \neq 0, \quad k=1\,{,}\ldots{,}\,n-1.$$
>
>Then there exists a **unit lower triangular matrix** $L$ and a **diagonal matrix** $$D = \text{diag}(d_{1}\,{,}\ldots{,}\,d_{n})$$ such that $$A = L\,D\,L^{*}.$$
>
>And the factorization is **unique**.

^951558

- [[Hermitian or Symmetric Matrix]]
- [[LU Factorization of Matrix]]

>[!important] Definition
>Let $A\in \mathbb{R}^{n\times n}$ be *symmetric matrix* with *all nonsingular leading principal submatrices*.
>
>Then the **$LDL^{T}$ factorization** of $A$ is given by $$A = L\,D\,L^{T}.$$


### Algorithms

![[Gaussian Elimination for Solving Linear System#^057350]]

- [[Gaussian Elimination for Solving Linear System]]






## Explanation

>[!info] Proof
>The *LU factorization* of $A$ is $$A = L\,U$$ Then $$L^{-1}\,A\,L^{-T} = U\,L^{-T}.$$
>
>Note that the RHS is an *upper triangular matrix* as it is the *product of two upper triangular matrices.*
>
>Also the LHS is a *symmetric matrix* since $A$ is symmetric.
>
>Thus $U\,L^{-T}$ is both **symmetric and upper triangular**. Thus it is a **diagonal matrix** $D$ i.e. $$D = U\,L^{-T} \implies D\,L^{T} = U$$ Thus $$A = L\,U = L\,D\,L^{T}$$ By *uniqueness* of *LU factorization* based on conditions in theorem, this factorization is unique. 
>
>This is the end of the proof.

>[!info]
>Using $LDL^{T}$ factorization to solve the **symmetric system of equations** such as the **normal equation** or the **scant equation**, we can solve it in three steps
>$$
>Lz = b, \quad Dy = z, \quad L^{T}x = y
>$$

- [[System of Linear Equations or Linear System]]
- [[Forward Substitution of Lower Triangular System]]
- [[Back Substitution of Upper Triangular System]]



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