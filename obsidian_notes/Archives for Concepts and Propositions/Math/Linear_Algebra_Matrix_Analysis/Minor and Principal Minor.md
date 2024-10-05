---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - principal_minor
  - minor
  - determinant
  - cofactor_matrix
  - leading_principal_minor
  - trailing_principal_minor
topics:
  - matrix_analysis
  - linear_algebra
name: Minor and Principal Minor
date of note: 2024-09-23
---

## Concept Definition

>[!important]
>**Name**: Minor and Principal Minor

![[Partition of Matrix and Block Matrix#^91291d]]

>[!important] Definition
>The *determinant* of $r\times r$ submatrix of $A$ is called a **minor**.
>
>If we wish to indicate the size of the submatrix, we call its determinant a **minor of size $r$**.

^35f53b

- [[Determinant of Linear Transformation]]

### Principal Minor

![[Principal Submatrix#^2c9003]]

![[Principal Submatrix#^f285eb]]

>[!important] Definition
>Let $A\in M_{n}$
>- The *determinant* of a *principal submatrix* is called a **principal minor**. $$\det\left(A[\alpha, \alpha]\right)$$
>- The *determinant* of a *leading principal submatrix* is called a **leading principal minor**. $$\det\left( A[1:r, 1:r]\right) := \det\left(A[\{ 1\,{,}\ldots{,}\,r \}, \{ 1 \,{,}\ldots{,}\,r \}]\right)$$
>- The *determinant* of a railing principal submatrix* is called a **trailing principal minor**. $$\det\left( A[r:n, r:n]\right) := \det\left(A[\{ r\,{,}\ldots{,}\,n \}, \{ r \,{,}\ldots{,}\,n \}]\right).$$

^ed00ef

- [[Principal Submatrix]]

### Cofactor

>[!important] Definition
>A **cofactor** is a *signed minor* of matrix $A$, i.e. $$\left(-1\right)^{i+j}\det \left(A[i^{c}, j^{c}]\right)$$
>We call the signed determinant of a $r\times r$ submatrix as the **cofactor of size $r$.**

^b43d82

- [[Laplace Expansion Theorem]]
- [[Adjugate of Matrix]]


## Explanation







-----------
##  Recommended Notes and References


- [[Jacobi Identity and Minors of the Inverse]]
- [[Partition of Matrix and Block Matrix]]
- [[Schur Complement and Inversion of Block Matrix]]
- [[Laplace Expansion Theorem]]


- [[Positive Semidefinite Transformation]]
- [[Determinant of Linear Transformation]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 17
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 100
- [[Matrix Computations by Golub]] pp 24
- [[Finite Dimensional Vector Spaces by Halmos]] pp 167
- [[Numerical Linear Algebra by Trefethen]] pp 154, 214