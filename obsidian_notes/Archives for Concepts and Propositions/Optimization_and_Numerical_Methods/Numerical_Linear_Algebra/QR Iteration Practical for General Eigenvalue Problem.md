---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - qr_iteration_eigenvalue_problem
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: QR Iteration Practical for General Eigenvalue Problem
date of note: 2024-10-02
---

## Concept Definition

>[!important]
>**Name**: QR Iteration Practical for General Eigenvalue Problem

### Hessenberg Reduction

![[Hessenberg Reduction via Householder Transformation#^44a0a9]]

- [[Hessenberg Reduction via Householder Transformation]]

### QR Iteration with Hessenberg Matrix

![[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem#^71e8e1]]

- [[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem]]



### Practical QR Iteration

>[!important] Definition
>Consider the *eigenvalue problem* $$Ax = \lambda x$$ where $A\in \mathbb{C}^{n\times n}$ and $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$ are eigenvalues of $A$.
>
>The **pratical QR iteration** algorithm *approximates* the **real Schur form** $$Q^{T}AQ = T$$ by producing a sequence of *unitarily similar Hessenberg matrices* $\{H_{k}\}_{k\ge 1}$ as follow:
>- *Require*: $A\in \mathbb{C}^{n\times n}$
>- *Require*: $\text{tol} >0$
>- Initialize with **Hessenberg reduction** $$H_{0} = U_{0}^{*}\,A\,U_{0}$$
>- For $k=1\,{,}\ldots{,}\,$ until convergence:
>	- **Partition Hessenberg Matrix**:
>		- Set to zero for all entries in $H_{k-1}$ that satisfies the condition $$|H_{i,i-1}^{(k-1)}| \le \text{tol}\cdot \left(|H_{i,i}^{(k-1)}| + |H_{i-1, i-1}^{(k-1)}|\right)$$
>		- Identify the **unreduced part** of $H_{k-1}$ by finding the *largest* $q>0$ and *smallest* $p >0$ such that $$H_{k-1} = \left[ \begin{array}{ccc}H_{\{ 1:p \}, \{ 1:p \}}^{(k-1)} & H_{\{ 1:p \}, \{ p+1:n-q\}}^{(k-1)} &  H_{\{ 1:p \}, \{ n-q+1:n\}}^{(k-1)} \\[5pt] 0 & H_{\{ p+1:n-q \}, \{ p+1:n-q\}}^{(k-1)} &  H_{\{ p+1:n-q \}, \{ n-q+1:n\}}^{(k-1)} \\[5pt] 0 & 0 & H_{\{ n-q+1:n \}, \{ n-q+1:n\}}^{(k-1)} \end{array} \right] $$ where 
>			- $H_{\{ n-q+1:n \}, \{ n-q+1:n\}}^{(k-1)}\in \mathbb{R}^{q\times q}$ is *quasi-upper-triangular*.
>			- $H_{\{ p+1:n-q \}, \{ p+1:n-q\}}^{(k-1)}\in \mathbb{R}^{(n-p-q) \times (n-p-q)}$ is the **unreduced** part
>	- If $q < n$,  
>		- **Hessenberg QR step** with **double implicit shift** on $H_{\{ p+1:n-q \}, \{ p+1:n-q\}}^{(k-1)}$ $$H_{\{ p+1:n-q \}, \{ p+1:n-q\}}^{(k)} = Z^{T}\,H_{\{ p+1:n-q \}, \{ p+1:n-q\}}^{(k-1)}\,Z$$
>			- $Z$ is the product of two Householder transformations
>		- Update orthogonal transformation $$Q_{k} = Q_{k-1}\,\text{diag}(I_{p}, Z, I_{q})$$
>		- Update other **off-diagonal blocks**
>			- $$H_{\{ 1:p \}, \{ p+1:n-q \}}^{(k)} = H_{\{ 1:p \}, \{ p+1:n-q \}}^{(k-1)}Z$$
>			- $$H_{\{ p+1:n-q \}, \{ n-q+1:n\}}^{(k)} = Z^{T}H_{\{ p+1:n-q \}, \{ n-q+1:n\}}^{(k-1)}$$
>- *Return* $T$ which overwrites $H$
>	- Note that to obtain **real Schur form** we may need to *upper triangularize* all $2 \times 2$ *diagonal blocks* in $H$ with *real eigenvalues*.

- [[Schur Triangularization and Schur Form]]
- [[Shift Strategy for Faster QR Iterations]]


## Explanation

>[!info]
>The **Hessenberg QR iteration** with **shift** is the *standard QR iteration* in practice.
>- We use the **double-implicit-shift strategy**
>- In the process, we monitor the Hessenberg matrix and to reduce the **off-diagonal term** to zero if it is *below tolerance threshold* 
>- Only apply QR iteration on the **unreduced diagonal blocks**


## Symmetric Case

- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]
- [[Symmetric QR Iteration for Tridiagonal Decomposition]]



-----------
##  Recommended Notes and References



- [[Shift Strategy for Faster QR Iterations]]
- [[Hessenberg QR Factorization via Given Transformation]]
- [[Hessenberg Reduction via Householder Transformation]]
- [[Hessenberg Matrix]]
- [[QR Iteration for General Eigenvalue Problem]]
- [[QR Factorization of Matrix]]

- [[Symmetric QR Iteration for Tridiagonal Decomposition]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Hermitian or Symmetric Matrix]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Schur Triangularization and Schur Form]]


- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 391
- [[Numerical Linear Algebra by Trefethen]] pp 212, 219 - 224