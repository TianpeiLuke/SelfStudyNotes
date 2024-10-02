---
tags:
  - concept
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords: 
topics: 
name: 
date of note: 2024-09-29
---

## Concept Definition

>[!important]
>**Name**: 



## Explanation

>[!quote]
>For computing the QR factorization $A = QR$ of a matrix $A$, we have discussed two methods in this book: **Householder reflections**, which *triangularize* $A$ by a succession of orthogonal operations, and **Gram—Schmidt orthogonalization**, which *orthogonalizes* $A$ by a succession of triangular operations. Though *Householder reflections* lead to a more *nearly orthogonal matrix* $Q$ in the presence of rounding errors, the *Gram—Schmidt process* has the advantage that it can be **stopped part-way**, leaving one with a **reduced QR factorization** of the first $n$ columns of $A$. The problem of computing a **Hessenberg reduction** $A = QHQ^{*}$ of a matrix $A$ is exactly analogous. There are two standard methods: **Householder reflections** (applied now on **two sides** of $A$ rather than *one*) and the **Arnoldi iteration**. Thus *Arnoldi* is the **analogue** of *Gram-Schmidt* for similarity transformations to **Hessenberg form** rather than *QR factorization*. Like Gram-Schmidt, it has the advantage that it can be **stopped part-way**, leaving one with a *partial reduction* to Hessenberg form that is exploited in various manners to form iterative algorithms for eigenvalues or systems of equations.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 251

- [[Hessenberg Reduction via Householder Transformation]]

-----------
##  Recommended Notes and References


- [[Krylov Subspace]]
- [[System of Linear Equations or Linear System]]

- [[Conjugate Gradient Algorithm Linear]]
- [[Lanczos Iteration to solve Eigenvalue Problem]]


- [[Matrix Analysis by Horn]]
- [[Numerical Linear Algebra by Trefethen]] pp 303
- [[Matrix Computations by Golub]] pp 579 - 583