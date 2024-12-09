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
>	- **Hessenberg QR step**:
>		- Compute the **QR factorization** of *Hessenberg matrix* $H_{k-1}$ $$U_{k}\,R_{k} = H_{k-1}$$
>		- Apply $U_{k}$ to *column* of $R_{k}$ to obtain new *unitary similar* **upper Hessenberg matrix** $H_{k}$ $$H_{k} = R_{k}\,U_{k}$$

^71e8e1


- [[Hessenberg QR Factorization via Given Transformation]]
- [[Hessenberg Reduction via Householder Transformation]]
- [[Schur Triangularization and Schur Form]]

![[eigenvalue_unsymmetric.png]]


### A Hessenberg QR Step via Givens Rotation

>[!info]
>We describe how to achieve the step at iteration $k$
>- Compute the **QR factorization** of *Hessenberg matrix* $H_{k-1}$ $$U_{k}\,R_{k} = H_{k-1}$$
>- Apply $U_{k}$ to **column** of $R_{k}$ to obtain new *unitary similar* **Hessenberg matrix** $H_{k}$ $$H_{k} = R_{k}\,U_{k}$$

![[Givens Rotations and Jacobi Rotations#^05b457]]

![[Givens Rotations and Jacobi Rotations#^24aabc]]

>[!important] Definition
>The **Hessenberg QR iteration step**  is described as follow:
>- *Require*: $H\in \mathbb{R}^{n\times n}$ is an *upper Hessenberg matrix*
>- **Hessenberg QR factorization**  i.e. $$QR = H$$
>	- For $k=1\,{,}\ldots{,}\,n-1$: 
>		- Compute the **Givens rotation** of *Hessenberg matrix* $H$ $$(c_{k}, s_{k}) = \text{Givens}(H_{k,k}, H_{k+1,k})$$
>		- Apply **Givens rotation** to *the $k$-th, and $(k+1)$-th rows* of $H$ $$H_{\{ k:k+1 \}, \{ k:n \}} \leftarrow \left[ \begin{array}{cc}c_{k} & s_{k} \\-s_{k} & c_{k} \end{array} \right]^{T}\,H_{\{ k:k+1 \}, \{ k:n \}} $$
>- **Right-multiply Givens rotations**
>	- For $k=1\,{,}\ldots{,}\,n-1$: 
>		- Apply **Givens rotation** to *the $k$-th, and $(k+1)$-th columns* of $H$ $$H_{\{1:k+1  \}, \{ k:k+1 \}} \leftarrow H_{\{1:k+1  \}, \{ k:k+1 \}}\,\left[ \begin{array}{cc}c_{k} & s_{k} \\-s_{k} & c_{k} \end{array} \right]$$
>- *Return* $H$ overwritten by the *upper Hessenberg matrix* $$H_{+} = RQ$$ with $Q = G_{1}\,{}\ldots{}\,G_{n-1}$. 

- [[Hessenberg QR Factorization via Given Transformation]]
- [[Givens Rotations and Jacobi Rotations]]

>[!info]
>$Q = G_{1}\,{}\ldots{}\,G_{n-1}$  is also *upper Hessenberg*. Thus $$H_{+} = RQ$$ is the *product of two upper Hessenberg matrix*, thus it is an *upper Hessenberg matrix*.


>[!important]
>Each **Hessenberg QR step** takes about $$6n^2$$ flops.

- [[Algorithm Big-O Notations and Rate of Growth]]
- [[Algorithm RAM Model and Complexity Analysis]]


### Hessenberg Reduction

>[!info]
>The steps to compute $$H_{0} = U_{0}^{*}\,A\,U_{0}$$ requires about $$\frac{10n^3}{3}$$ flops.

- [[Hessenberg Reduction via Householder Transformation]]


### Shifted QR Iteration


- [[Shift Strategy for Faster QR Iterations]]


### Put it Together

- [[QR Iteration Practical for General Eigenvalue Problem]]





## Explanation

>[!info]
>Since a **Hessenberg matrix** $H$ is *almost upper triangular* with only difference being the 1st off-diagonal entries, the **QR factorization** of $H$ in each step only requires $$3n^2$$ flops.
>

>[!quote]
>A straightforward **generalization** of the **power method** can be used to compute higher  dimensional invariant subspaces.
>
>-- [[Matrix Computations by Golub]] pp 367

- [[Power Iteration and Inverse Iteration for General Eigenvalue Problem]]

>[!info]
>Note that $$T_{k} = R_{k}U_{k} = U_{k}^{*}U_{k}R_{k}U_{k} = U_{k}^{*}(U_{k}R_{k})U_{k} = U_{k}^{*}\,T_{k-1}\,U_{k}$$ so $T_{k}  \stackrel{U}{\sim} T_{k-1}$.
>
>By induction, $$T_{k} = \left(U_{0}\,{}\ldots{}\,U_{k}\right)^{*}\,A\,\left(U_{0}\,{}\ldots{}\,U_{k}\right).$$
>
>It can be shown that $T_{k}$ will converge to the **Schur form** $$T_{k} \to T = D+N$$

>[!info]
>The **Hessenberg QR iteration** with **shift** is the *standard QR iteration* in practice.







-----------
##  Recommended Notes and References




- [[Hessenberg Reduction via Householder Transformation]]
- [[Hessenberg Matrix]]

- [[Power Iteration and Inverse Iteration for General Eigenvalue Problem]]
- [[Schur Triangularization and Schur Form]]


- [[QR Factorization of Matrix]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Hermitian or Symmetric Matrix]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 377 - 380, 385 - 392