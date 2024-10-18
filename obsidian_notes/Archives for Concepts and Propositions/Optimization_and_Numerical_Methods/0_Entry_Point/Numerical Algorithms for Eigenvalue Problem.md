---
tags:
  - entry_point
  - concept
  - numerical_methods/numerical_linear_algebra
keywords: 
topics:
  - numerical_linear_algebra
name: 
date of note: 2024-10-04
---

## Concept Definition

### Eigenvalue Problem

- [[Eigenspace and Spectrum for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Characteristic Polynomial for Linear Map]]
- [[Algebraic and Geometric Multiplicity of Linear Map]]

- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Variational Characterization of Eigenvalues of Hermitian Matrix]]
- [[Courant-Fischer Minimax Theorem for Eigenvalue Problem]]

### Solving Eigenvalue Problem via Eigenvalue-Revealing Factorizations

>[!quote]
>Instead of ideas like these, the best general purpose eigenvalue algorithms are based on a different principle: the *computation* of an **eigenvalue-revealing factorization** of $A$, where the *eigenvalues* appear as *entries* of one of the *factors*. We saw three eigenvalue-revealing factorizations in the last lecture: 
>- **diagonalization**, 
>- **unitary diagonalization**, and 
>- **unitary triangularization (Schur factorization)**. 
>  
>In practice, eigenvalues are usually computed by constructing one of these factorizations. Conceptually, what must be done to achieve this is to *apply a sequence of transformations* to $A$ to **introduce zeros** in the necessary places, just as in the algorithms we have considered in the preceding lectures of this book. Thus we see that finding eigenvalues ends up rather similar in flavor to solving systems of equations or least squares problems. 
>- The algorithms of *numerical linear algebra* are mainly built upon one technique used over and over again: **putting zeros into matrices**.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 191


>[!important]
>The **eigenvalue-revealing factorizations** are factorizations of a matrix that reduces it to a form in which *the eigenvalues are explicitly displayed*.
>- The **diagonalization** $$A = S\Lambda S^{-1}$$ *if and only if* $A$ is **nondefective**;
>- The **unitary diagonalization** $$A = U\Lambda U^{*}$$  *if and only if* $A$ is **normal**;
>- The **unitary tridiagonalization** $$A = U T U^{*}$$  for all $A$
>  
>In general, it will be the **Schur factorization / decomposition.**  

- [[Derogatory Matrix and Defective Matrix]]
- [[Jordan Canonical Form]]
- [[Schur Triangularization and Schur Form]]
- [[Unitary Similarity and Unitary Diagonalizable]]

#### Non-Hermitian Case

![[Schur Triangularization and Schur Form#^b40ca5]]

- [[Schur Triangularization and Schur Form]]

![[Hessenberg Decomposition of Matrix#^884435]]

- [[Hessenberg Matrix]]
- [[Hessenberg Decomposition of Matrix]]

![[Hessenberg Decomposition of Matrix#^6c0758]]

#### Hermitian Case

![[Spectral Theorem of Self-Adjoint Map and Eigen decomposition#^e5de5d]]

- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

![[Tridiagonal Decomposition of Symmetric Matrix#^616da0]]

- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]
- [[Tridiagonal Decomposition of Symmetric Matrix]]

![[Tridiagonal Decomposition of Symmetric Matrix#^8a0810]]


## Explanation

### Shortcoming of Direct Approaches

#### Root Finding for Characteristic Polynomial

>[!quote]
>Perhaps the first method one might think of would be to *compute the coefficients* of the **characteristic polynomial** and use a **rootfinder** to *extract its roots*. Unfortunately, as mentioned in Lecture 15, this strategy is a bad one, because **polynomial rootfinding** is an **ill-conditioned problem** in general, even when the underlying eigenvalue problem is well-conditioned. (In fact, polynomial rootfinding is by no means a mainstream topic in scientific computing precisely because it is so rarely the best way to solve applied problems.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 190

- [[Characteristic Polynomial for Linear Map]]
- [[Companion Matrix of Polynomial]]

>[!quote]
>This theorem implies that even if we could work in exact arithmetic, there could be *no computer program that would produce* **the exact roots** of an *arbitrary polynomial* in a finite number of steps. It follows that the same conclusion applies to the more general problem of computing eigenvalues of matrices.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 192

#### Power Iterations

>[!quote]
>Another idea would be to take advantage of the fact that the sequence
>$$
>\frac{x}{\lVert x \rVert_{2}}, \;\frac{Ax}{\lVert Ax \rVert_{2}} \,{,}\ldots{,}\,\frac{A^{k} x}{\lVert A^{k}x \rVert_{2}} \,{,}\ldots{,}\,
>$$
>*converges*, under certain assumptions, to an **eigenvector** *corresponding to the* **largest eigenvalue** of $A$ in absolute value. This method for finding an eigenvector is called **power iteration**. Unfortunately, although power iteration is famous, it is by no means an effective tool for general use. Except for special matrices, it is **very slow**.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 191


![[rayleigh_quotient_power_inverse.png]]

- [[Krylov Subspace and Krylov Matrix]]
- [[Power Iteration and Inverse Iteration for General Eigenvalue Problem]]
- [[Rayleigh Quotient Iteration for Symmetric Eigenvalue Problem]]

### Iterative Solver for Eigenvalue Problem

>[!quote]
>Methods like **Householder reflections** and **Gaussian elimination** would solve *linear systems* of equations **exactly** in a **finite number of steps** if they could be implemented in *exact arithmetic*. By contrast,  
>- **Any eigenvalue solver must be iterative**.  
>
>The goal of an eigenvalue solver is to produce sequences of numbers that *converge rapidly towards eigenvalues*. In this respect eigenvalue computations are more *representative of scientific computing* than *solutions of linear systems of equations*.
>
>The need to iterate may seem discouraging at first, but the algorithms available in this field **converge extraordinarily quickly**. In most cases it is possible to compute sequences of numbers that *double or triple the numbers of digits of accuracy at every step*.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 192 - 193


- [[Power Iteration and Inverse Iteration for General Eigenvalue Problem]]
- [[Rayleigh Quotient Iteration for Symmetric Eigenvalue Problem]]
- [[QR Iteration for General Eigenvalue Problem]]
- [[Iterative Methods to approximate Solution of Large-Scale Linear System]]

### Two Phases of Eigenvalue Computation

>[!info]
>The Schur factorization of $A$ can be obtained by transforming $A$ via a *sequence of transformations* $$\underbrace{ Q_{j}^{*}\,{}\ldots{}\,Q_{1}^{*} }_{ Q^{*} }\;A\;\underbrace{ Q_{1}\,{}\ldots{}\,Q_{j} }_{ Q } \to T, \quad j\to \infty.$$

>[!quote]
>*Whether or not* $A$ is *hermitian*, the sequence (25.4) is usually split into **two phases**. 
>- In the **first phase**, a **direct method** is applied to produce an **upper Hessenberg matrix** $H$, that is, a matrix with *zeros below the first subdiagonal*. 
>- In the **second phase**, an **iteration** is applied to generate a **formally infinite sequence of Hessenberg matrices** that converge to a **triangular form**. Schematically, the process looks like this:

![[eigenvalue_unsymmetric.png]]

- [[Hessenberg Decomposition of Matrix]]
- [[Hessenberg Reduction via Householder Transformation]]
- [[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]
- [[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem]]
- [[Shift Strategy for Faster QR Iterations]]
- [[QR Iteration Practical for General Eigenvalue Problem]]

>[!quote]
>If $A$ is *hermitian*, the two-phase approach becomes even **faster**. 
>- The intermediate matrix is now a *hermitian Hessenberg matrix*, that is, **tridiagonal**. 
>- The final result is a *hermitian triangular matrix*, that is, **diagonal**, as mentioned above. Schematically:

![[eigenvalue_symmetric.png]]

- [[Tridiagonal Decomposition of Symmetric Matrix]]
- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]
- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[Shift Strategy for Faster Symmetric QR Iterations]]
- [[Symmetric QR Iteration for Symmetric Eigenvalue Problem]]

>[!quote]
>In this hermitian case we shall see that *if only eigenvalues* are required (not eigenvectors), then **each step of Phase 2** can be carried out with **only $O(m)$ flops**, bringing the *total work* estimate for Phase 2 to $O(m^2)$ **flops**. Thus, for hermitian eigenvalue problems, we are in the paradoxical situation that the "infinite" part of the algorithm is in practice not merely as fast as the "finite" part, but an *order of magnitude faster*.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 194

### Krylov Space Methods

- [[Krylov Subspace and Krylov Matrix]]
- [[Krylov Subspace Methods]]
- [[GMRES as Regression on Krylov Space]]
- [[Conjugate Gradient Algorithm Linear]]
- [[Conjugate Gradient Algorithm Lanczos]]
- [[Conjugate Gradient Normal Equation Residual and CGNR]]
- [[Conjugate Gradient Algorithm Convergence Analysis]]
- [[Conjugate Gradient Algorithm Nonlinear Convergence Analysis]]



-----------
##  Recommended Notes and References



- [[Numerical Linear Algebra by Trefethen]] pp 190 - 195, 179 - 285
- [[Matrix Computations by Golub]] pp 347 - 485,  545 - 596