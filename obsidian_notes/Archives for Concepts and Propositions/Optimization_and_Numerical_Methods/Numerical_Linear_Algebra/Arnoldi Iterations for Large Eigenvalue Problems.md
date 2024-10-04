---
tags:
  - concept
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - arnoldi_iteration_eigenvalue
  - krylov_subspace
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Arnoldi Iterations for Large Eigenvalue Problems
date of note: 2024-09-29
---

## Concept Definition

>[!important]
>**Name**: Arnoldi Iterations for Large Eigenvalue Problems

### Projection into Krylov Space

![[Krylov Subspace and Krylov Matrix#^27eea3]]

![[Krylov Subspace and Krylov Matrix#^e38b83]]

![[Nilpotent Linear Transformation and Matrix#^ee0cec]]

![[Hessenberg Decomposition of Matrix#^40c613]]

- [[Krylov Subspace and Krylov Matrix]]
- [[Nilpotent Linear Transformation and Matrix]]
- [[Hessenberg Decomposition of Matrix]]


## Explanation

### Gram-Schmidt and Arnoldi Process

>[!quote]
>For computing the QR factorization $$A = QR$$ of a matrix $A$, we have discussed two methods in this book: 
>- **Householder reflections**, which *triangularize* $A$ by a succession of orthogonal operations, 
>- and **Gram—Schmidt orthogonalization**, which *orthogonalizes* $A$ by a succession of triangular operations. 
>  
>Though *Householder reflections* lead to a more *nearly orthogonal matrix* $Q$ in the presence of rounding errors, the *Gram—Schmidt process* has the advantage that it can be **stopped part-way**, leaving one with a **reduced QR factorization** of the first $n$ columns of $A$. 
>
>The problem of computing a **Hessenberg reduction** $$A = QHQ^{*}$$ of a matrix $A$ is exactly analogous. There are two standard methods: 
>- **Householder reflections** (applied now on **two sides** of $A$ rather than *one*) 
>- and the **Arnoldi iteration**. 
>  
>Thus *Arnoldi* is the **analogue** of *Gram-Schmidt* for similarity transformations to **Hessenberg form** rather than *QR factorization*. Like Gram-Schmidt, it has the advantage that it can be **stopped part-way**, leaving one with a *partial reduction* to Hessenberg form that is exploited in various manners to form iterative algorithms for eigenvalues or systems of equations.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 251

- [[Hessenberg Decomposition of Matrix]]

|                              | $A = QR$ <br>**QR Factorization**                                      | $A= QHQ^{*}$ <br>**Henssenberg Factorization**                                                |
| ---------------------------- | ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Orthogonal Structuring       | **Householder Transformation**<br><br>[[Householder QR Factorization]] | **Householder Transformation**<br><br>[[Hessenberg Reduction via Householder Transformation]] |
| Structured Orthogonalization | **Gram-Schmidt process**<br><br>[[Gram-Schmidt Orthogonalization]]     | **Arnoldi process**<br><br>[[Arnoldi Iterations for Large Eigenvalue Problems]]               |

- [[Householder Transformation and Householder Reflection]]
- [[Modified Gram-Schmidt Algorithm for QR Factorization]]




-----------
##  Recommended Notes and References


- [[Hessenberg Reduction via Householder Transformation]]

- [[System of Linear Equations or Linear System]]



- [[Conjugate Gradient Algorithm Linear]]
- [[Lanczos Tridiagonalization for Large Symmetric Eigenvalue Problem]]
- [[Lanczos Iteration Practical for Large Symmetric Eigenvalue Problem]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Power Iteration and Inverse Iteration for General Eigenvalue Problem]]


- [[Matrix Analysis by Horn]]
- [[Numerical Linear Algebra by Trefethen]] pp 303
- [[Matrix Computations by Golub]] pp 579 - 583