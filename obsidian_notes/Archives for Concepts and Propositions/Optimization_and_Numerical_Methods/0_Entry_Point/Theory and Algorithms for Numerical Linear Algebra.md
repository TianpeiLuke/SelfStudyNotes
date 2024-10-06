---
tags:
  - entry_point
  - concept
  - numerical_methods/numerical_linear_algebra
keywords: 
topics:
  - linear_algebra
  - matrix_analysis
  - numerical_linear_algebra
name: 
date of note: 2024-05-12
---

## Concept Definition

### Linear Algebra and Matrix Analysis

- [[Concepts and Theorems in Finite Dimensional Vector Space]]
- [[Concepts and Theorems for Matrix Theory]]
- [[Singular Value Decomposition of Linear Map]]
- [[Low Rank Approximation of Matrix and Eckhart-Young Theorem]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Singular Value Decomposition and Pseudoinverse]]

### General Linear Systems

#### Solution of Linear System

- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]

#### Triangular System

- [[Triangular System of Equations]]
- [[Forward Substitution of Lower Triangular System]]
- [[Back Substitution of Upper Triangular System]]

#### Elementary Operations

- [[Elementary Row and Column Operations]]
- [[Reduced Row Echelon Form]]

#### LU Factorization and Gaussian Elimination

- [[Gaussian Elimination for General Linear System]]
- [[LU Factorization of Matrix]]
- [[PLU Factorization with Pivoting]]
- [[Gaussian Elimination with Partial Pivoting]]
- [[Gaussian Elimination with Complete Pivoting]]
- [[LPU Factorization of Nonsingular Matrix]]
- [[LPDU Factorization of Nonsingular Matrix]]
- [[Stability Analysis of Gaussian Elimination]]


### Special Linear Systems

#### Symmetric or Hermitian System 

- [[Hermitian or Symmetric Matrix]]
- [[LDU Factorization of Symmetric Matrix]]
- [[LDU Factorization with Symmetric Pivoting]]
- [[Triangular Equivalence of Matrices]]

#### Symmetric or Hermitian Positive Definite System 

- [[Positive Semidefinite Transformation]]
- [[QR Factorization of Matrix]]
- [[Square Root of Positive Semidefinite Transformation and Absolute Value]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]

#### Banded System of Equations

- [[Banded System of Equations]]
- [[Banded System of Equations]]
- [[Band Triangular System of Equations]]
- [[Band Forward Substitution and Band Back Substitution]]
- [[Band Gaussian Elimination and Band LU Factorization]]
- [[Band Gaussian Elimination and Band LU Factorization]]
- [[Band Gaussian Elimination with Pivoting]]
- [[Hessenberg LU Factorization of Matrix]]
- [[Hessenberg Reduction via Householder Transformation]]
- [[Band Cholesky Factorization of Hermitian Positive Semidefinite Matrices]]

#### Tridiagonal System of Equations

- [[Tridiagonal System of Equations]]
- [[Tridiagonal Decomposition of Symmetric Matrix]]
- [[Tridiagonal Eigenvalue Problem]]



#### Toeplitz and Circulant System

- [[Toeplitz System of Equations]]
- [[Circulant Matrix and Circulant Permutation Operation]]
- [[Discrete Fourier Transform]]
- [[Fast Fourier Transform]]


### Orthogonalization and QR Factorization

- [[Householder Transformation and Householder Reflection]]
- [[Givens Rotations and Jacobi Rotations]]
- [[Gram-Schmidt Orthogonalization]]

- [[QR Factorization of Matrix]]
- [[Householder QR Factorization]]
- [[Block Householder QR Factorization]]
- [[Modified Gram-Schmidt Algorithm for QR Factorization]]

- [[Bidiagonal Factorization with Householder Transformation]]


### Least Square Problems

- [[Least Square Estimation]]
- [[Algorithms for Least Square Estimation Problem]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Least Square Estimation with QR Factorization]]
- [[Least Square Estimation via Singular Value Decomposition]]

- [[Krylov Subspace Methods]]
- [[GMRES as Regression on Krylov Space]]
- [[Conjugate Gradient Normal Equation Residual and CGNER]]

###  Eigenvalue Problem

- [[Eigenspace and Spectrum for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Schur Triangularization and Schur Form]]

- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Courant-Fischer Minimax Theorem for Eigenvalue Problem]]


### Iterative Algorithms to solve Eigenvalue Problems

- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Principle of Biorthogonality]]
- [[Biorthogonalization Methods]]

- [[Numerical Algorithms for Eigenvalue Problem]]

#### General Case without Symmetric, Small Scale

>[!info]
>For general $A\in \mathbb{C}^{n\times n}$, $$A \stackrel{U}{\sim} T = D+ N$$ 

- [[Schur Triangularization and Schur Form]]
- [[Jordan Canonical Form]]
- [[Power Iteration and Inverse Iteration for General Eigenvalue Problem]]

>[!info]
>The most common approach is to reduce an *unsymmetric matrix* $A$ to a *Hessenberg matrix* $H$, and then perform *QR iterations*

- [[QR Iteration for General Eigenvalue Problem]]
- [[Hessenberg QR Factorization via Given Transformation]]
- [[Hessenberg Decomposition of Matrix]]
- [[Hessenberg Reduction via Householder Transformation]]
- [[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem]]
- [[Shift Strategy for Faster QR Iterations]]
- [[QR Iteration Practical for General Eigenvalue Problem]]


#### Symmetric Case, Small Scale

>[!info]
>For Hermitian $A = A^{*}\in \mathbb{C}^{n\times n}$, $$A \stackrel{U}{\sim} D$$ or $$A \stackrel{U}{\sim} T$$ for *tridiagonal matrix*.

- [[Unitary Similarity and Unitary Diagonalizable]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Variational Characterization of Eigenvalues of Hermitian Matrix]] 

![[rayleigh_quotient_power_inverse.png]]

- [[Rayleigh Quotient Iteration for Symmetric Eigenvalue Problem]]

>[!info]
>Similar to unsymmetric case, the most common approach is to reduce a *symmetric matrix* $A$ to a *tridiagonal matrix* $T$, and then perform *QR iterations* to *diagonalize it*.

- [[Tridiagonal Eigenvalue Problem]]
- [[Tridiagonal Decomposition of Symmetric Matrix]]
- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]
- [[Shift Strategy for Faster Symmetric QR Iterations]]
- [[Symmetric QR Iteration for Symmetric Eigenvalue Problem]]

- [[Symmetric Schur Decomposition of 2-by-2 Matrix]]
- [[Jacobi Method for Symmetric Eigenvalue Problem]]

#### Symmetric Case, Large Scale

>[!info]
>For large scalar problem, we only the compute **top/bottom $k$ eigenvalues and eigenvectors.**

- [[Krylov Subspace and Krylov Matrix]]
- [[Convex Optimization for Eigenvalue Problem]]
- [[Ritz Pair for Linear Map with respect to Subspace]]

>[!info]
>**Lanczos process** is an iterative process that compute **tridiagonal decomposition** of *Hermitian matrix* using **modified Gram-Schmdit** process.
>- **Lanczos proces** is a stable version of **QR factorization** of *Krylov matrix* $$K(A, q_{1}, k)= Q_{k}R_{k}$$
>- The *eigenvalue* is **approximated** by the *eigenvalue of tridiagonal matrix* at the end of iteration.
>- **Lanczos process** reduce the complexity of the direct tridiagonalization via *Householder transformation*  [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]

- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[Ritz Pair for Linear Map with respect to Subspace]]
- [[Lanczos Iteration Practical with Reorthogonalization]]


#### General Case without Symmetric, Large Scale

>[!info]
>**Arnoldi process** is an iterative process that compute **Hessenberg decomposition** of *unsymmetric matrix* using **modified Gram-Schmdit** process.
>- **Arnoldi proces** is a stable version of **QR factorization** of *Krylov matrix* $$K(A, q_{1}, k)= Q_{k}R_{k}$$
>- The *eigenvalue* is **approximated** by the *eigenvalue of Hessenberg matrix* at the end of iteration.
>- **Arnoldi process** reduce the complexity of the direct Hessenberg reduction via *Householder transformation* [[Hessenberg Reduction via Householder Transformation]]

- [[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]
- [[Ritz Pair for Linear Map with respect to Subspace]]
- [[Jacobi-Davidson Algorithm to Sparse Eigenvalue Problem]]



### Iterative Algorithms to solve Large Sparse Linear System

- [[Sparse Linear System and Graph]]

#### General Case

- [[Classical Iterations to approximate Solution of Sparse Linear System]]
- [[Jacobi Iteration for Sparse Linear System]]
- [[Gauss-Seidel Iteration for Sparse Linear System]]
- [[Gauss-Seidel Iteration Convergence Analysis]]
- [[Successive Over-Relaxation for Sparse Linear System]]


- [[Biorthogonalization Methods]]
- [[GMRES as Regression on Krylov Space]]
- [[Conjugate Gradient Normal Equation Residual and CGNER]]

#### Symmetric Case

- [[Conjugate Gradient Algorithm Linear]]
- [[Conjugate Gradient Algorithm Convergence Analysis]]
- [[Conjugate Gradient Algorithm Lanczos]]
- [[Minimal Residuals Algorithm and MINRES]]



### Krylov Subspace Methods

![[krylov_subspace_methods_classification.png]]

- [[Krylov Subspace and Krylov Matrix]]
- [[Krylov Subspace Methods]]
- [[GMRES as Regression on Krylov Space]]
- [[Conjugate Gradient Algorithm Linear]]
- [[Conjugate Gradient Normal Equation Residual and CGNER]]
- [[Biconjugate Gradients Algorithm for Nonsymmetric System]]




## Explanation





-----------
##  Recommended Notes and References


- [[Matrix Computations by Golub]]
- [[Numerical Linear Algebra by Trefethen]]

- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix CookBook by Petersen]]
