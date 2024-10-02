---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - qr_iteration_eigenvalue_problem
  - qr_factorization
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: QR Iteration to solve Eigenvalue Problem of General Matrix
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: QR Iteration to solve Eigenvalue Problem of General Matrix

>[!important] Definition
>Consider the *eigenvalue problem* $$Ax = \lambda x$$ where $A\in \mathbb{C}^{n\times n}$ and $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$ are eigenvalues of $A$ with $$|\lambda_{1}| > |\lambda_{2}| \,{\ge}\ldots{\ge}\,|\lambda_{n}|.$$
>- By *Schur decomposition*, there exists unitary matrix $U$ so that $$T = U^{*}\,A\,U$$ where $T= D + N$ is an *upper triangular matrix* with *eigenvalue diagonal terms* $D = \text{diag}(\lambda_{1}\,{,}\ldots{,}\,\lambda_{n}).$
>
>The **QR iteration** algorithm *approximates* the **eigenvalues** $D$ by producing a sequence of *unitarily similar matrices* $\{T_{k}\}_{k\ge 1}$ as follow:
>- *Require*: $A\in \mathbb{C}^{n\times n}$
>- *Require*: initial unitary matrix $U_{0}\in \mathcal{U}(n)$
>- Initialize with $T_{0}$ that is *unitarily similar to* $A$ $$T_{0} = U_{0}^{*}\,A\,U_{0}$$
>- For $k=1\,{,}\ldots{,}\,$ until convergence:
>	- Compute the **QR factorization** of $T_{k-1}$ $$U_{k}\,R_{k} = T_{k-1}$$
>	- Apply $U_{k}$ to **column** of $R_{k}$ to obtain new unitary similar matrix $T_{k}$ $$T_{k} = R_{k}\,U_{k}$$

^a864d4

- [[QR Factorization of Matrix]]
- [[Schur Triangularization and Schur Form]]


## Explanation

>[!quote]
>A straightforward **generalization** of the **power method** can be used to compute higher  dimensional invariant subspaces.
>
>-- [[Matrix Computations by Golub]] pp 367

- [[Power Iteration and Inverse Iteration to solve Eigenvalue Problem]]

>[!info]
>Note that $$T_{k} = R_{k}U_{k} = U_{k}^{*}U_{k}R_{k}U_{k} = U_{k}^{*}(U_{k}R_{k})U_{k} = U_{k}^{*}\,T_{k-1}\,U_{k}$$ so $T_{k}  \stackrel{U}{\sim} T_{k-1}$.
>
>By induction, $$T_{k} = \left(U_{0}\,{}\ldots{}\,U_{k}\right)^{*}\,A\,\left(U_{0}\,{}\ldots{}\,U_{k}\right).$$
>
>It can be shown that $T_{k}$ will converge to the **Schur form** $$T_{k} \to T = D+N$$

## Hessenburg QR Iteration


- [[Hessenberg Reduction via Householder Transformation]]
- [[Hessenburg QR Iteration to solve Eigenvalue Problem]]




-----------
##  Recommended Notes and References


- [[Hessenberg Reduction via Householder Transformation]]
- [[Power Iteration and Inverse Iteration to solve Eigenvalue Problem]]
- [[Schur Triangularization and Schur Form]]


- [[Linear Span over a Set of Vectors]]
- [[Orthogonal Complement of Hilbert Spaces]]
- [[QR Factorization of Matrix]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Hermitian or Symmetric Matrix]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 454 - 456