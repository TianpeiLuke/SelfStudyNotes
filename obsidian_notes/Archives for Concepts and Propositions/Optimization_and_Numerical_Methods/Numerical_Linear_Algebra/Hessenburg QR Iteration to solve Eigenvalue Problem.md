---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - qr_iteration_eigenvalue_problem
  - qr_factorization
  - hessenberg_matrix
  - hessenberg_qr
  - hessengberg_qr_eigenvalue_problem
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Hessenburg QR Iteration to solve Eigenvalue Problem
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Hessenburg QR Iteration to solve Eigenvalue Problem

>[!important] Definition
>Consider the *eigenvalue problem* $$Ax = \lambda x$$ where $A\in \mathbb{C}^{n\times n}$ and $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$ are eigenvalues of $A$ with $$|\lambda_{1}| > |\lambda_{2}| \,{\ge}\ldots{\ge}\,|\lambda_{n}|.$$
>- By *Schur decomposition*, there exists unitary matrix $U$ so that $$T = U^{*}\,A\,U$$ where $T= D + N$ is an *upper triangular matrix* with *eigenvalue diagonal terms* $D = \text{diag}(\lambda_{1}\,{,}\ldots{,}\,\lambda_{n}).$
>
>The **Hessenberg QR iteration** algorithm *approximates* the **eigenvalues** $D$ by producing a sequence of *unitarily similar Hessenberg matrices* $\{H_{k}\}_{k\ge 1}$ as follow:
>- *Require*: $A\in \mathbb{C}^{n\times n}$
>- Initialize with **Hessenberg reduction** $$H_{0} = U_{0}^{*}\,A\,U_{0}$$
>- For $k=1\,{,}\ldots{,}\,$ until convergence:
>	- Compute the **QR factorization** of *Hessenberg matrix* $H_{k-1}$ $$U_{k}\,R_{k} = H_{k-1}$$
>	- Apply $U_{k}$ to **column** of $R_{k}$ to obtain new *unitary similar* **Hessenberg matrix** $H_{k}$ $$H_{k} = R_{k}\,U_{k}$$


- [[Hessenberg QR Factorization via Given Transformation]]
- [[Hessenberg Decomposition of Matrix]]
- [[Schur Triangularization and Schur Form]]

### Shifted QR Iteration

>[!important] Definition
>The **shifted Hessenberg QR iteration** algorithm *approximates* the **eigenvalues** $D$ of $A$ by producing a sequence of *unitarily similar Hessenberg matrices* $\{H_{k}\}_{k\ge 1}$ as follow:
>- *Require*: $A\in \mathbb{C}^{n\times n}$
>- *Require*: **shift parameter** $\mu\in \mathbb{R}$
>- Initialize with **Hessenberg reduction** $$H_{0} = U_{0}^{*}\,A\,U_{0}$$
>- For $k=1\,{,}\ldots{,}\,$ until convergence:
>	- Compute the **QR factorization** of *Hessenberg matrix* $H_{k-1}$ **shifted by** $\mu$  $$U_{k}\,R_{k} = H_{k-1} -\mu I$$
>	- Apply $U_{k}$ to **column** of $R_{k}$ with **additional shifting** to obtain new *unitary similar* **Hessenberg matrix** $H_{k}$ $$H_{k} = R_{k}\,U_{k} + \mu I$$

### Francis QR Step




## Explanation

>[!quote]
>A straightforward **generalization** of the **power method** can be used to compute higher  dimensional invariant subspaces.
>
>-- [[Matrix Computations by Golub]] pp 367

- [[Power Iteration to solve Eigenvalue Problem of General Matrix]]

>[!info]
>Note that $$T_{k} = R_{k}U_{k} = U_{k}^{*}U_{k}R_{k}U_{k} = U_{k}^{*}(U_{k}R_{k})U_{k} = U_{k}^{*}\,T_{k-1}\,U_{k}$$ so $T_{k}  \stackrel{U}{\sim} T_{k-1}$.
>
>By induction, $$T_{k} = \left(U_{0}\,{}\ldots{}\,U_{k}\right)^{*}\,A\,\left(U_{0}\,{}\ldots{}\,U_{k}\right).$$
>
>It can be shown that $T_{k}$ will converge to the **Schur form** $$T_{k} \to T = D+N$$

## Hessenburg QR Iteration







-----------
##  Recommended Notes and References




- [[Hessenberg Decomposition of Matrix]]
- [[Hessenberg Matrix]]

- [[Power Iteration to solve Eigenvalue Problem of General Matrix]]
- [[Schur Triangularization and Schur Form]]




- [[Linear Span over a Set of Vectors]]
- [[Orthogonal Complement of Hilbert Spaces]]
- [[QR Factorization of Matrix]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Hermitian or Symmetric Matrix]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 385 - 392