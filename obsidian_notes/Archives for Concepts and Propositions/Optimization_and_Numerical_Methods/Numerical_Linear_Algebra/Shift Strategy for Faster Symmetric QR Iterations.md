---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
keywords:
  - hessenberg_qr
  - shift_strategy_qr
topics:
  - numerical_linear_algebra
name: Shift Strategy for Faster Symmetric QR Iterations
date of note: 2024-10-02
---

## Concept Definition

>[!important]
>**Name**: Shift Strategy for Faster Symmetric QR Iterations


>[!info]
>We can improve the *rate of convergence* for *symmetric QR iteration* with **shifts.** 

>[!important] Definition
>The **shifted symmetric QR iteration** algorithm *approximates* the **eigenvalues** $D$ of $A$ by producing a sequence of *unitarily similar Tridiagonal matrices* $\{T_{k}\}_{k\ge 1}$ as follow:
>- *Require*: $A\in \mathbb{C}^{n\times n}$
>- *Require*: **shift parameter** $\mu\in \mathbb{R}$
>- Initialize with **Hessenberg reduction** $$T_{0} = U_{0}^{*}\,A\,U_{0}$$
>- For $k=1\,{,}\ldots{,}\,$ until convergence:
>	- Compute the **QR factorization** of *tridiagonal matrix* $T_{k-1}$ **shifted by** $\mu$  $$U_{k}\,R_{k} = T_{k-1} -\mu I$$
>	- Apply $U_{k}$ to **column** of $R_{k}$ with **additional shifting** to obtain new *unitary similar* **tridiagonal matrix** $T_{k}$ $$T_{k} = R_{k}\,U_{k} + \mu I$$

- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]
- [[Symmetric QR Iteration for Symmetric Eigenvalue Problem]]

### Wilkinson Shift






## Explanation


- [[Shift Strategy for Faster QR Iterations]]


-----------
##  Recommended Notes and References




- [[Symmetric QR Iteration for Symmetric Eigenvalue Problem]]
- [[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem]]
- [[QR Iteration for General Eigenvalue Problem]]
- [[Schur Triangularization and Schur Form]]
- [[Jordan Canonical Form]]
- [[QR Factorization of Matrix]]

- [[QR Iteration Practical for General Eigenvalue Problem]]
- [[Symmetric QR Iteration for Symmetric Eigenvalue Problem]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Matrix]]


- [[Matrix Computations by Golub]] pp 385 - 391
- [[Numerical Linear Algebra by Trefethen]] pp 212, 219 - 224