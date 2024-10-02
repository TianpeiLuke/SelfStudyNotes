---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
keywords:
  - hessenberg_qr
  - shift_strategy_qr
topics:
  - numerical_linear_algebra
name: Shift Strategy for Faster Hessenberg QR Iterations
date of note: 2024-10-02
---

## Concept Definition

>[!important]
>**Name**: Shift Strategy for Faster Hessenberg QR Iterations

![[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem#^71e8e1]]

>[!info]
>We can improve the *rate of convergence* for *Hessenberg QR iteration* with **shifts.** 

>[!important] Definition
>The **shifted Hessenberg QR iteration** algorithm *approximates* the **eigenvalues** $D$ of $A$ by producing a sequence of *unitarily similar Hessenberg matrices* $\{H_{k}\}_{k\ge 1}$ as follow:
>- *Require*: $A\in \mathbb{C}^{n\times n}$
>- *Require*: **shift parameter** $\mu\in \mathbb{R}$
>- Initialize with **Hessenberg reduction** $$H_{0} = U_{0}^{*}\,A\,U_{0}$$
>- For $k=1\,{,}\ldots{,}\,$ until convergence:
>	- Compute the **QR factorization** of *Hessenberg matrix* $H_{k-1}$ **shifted by** $\mu$  $$U_{k}\,R_{k} = H_{k-1} -\mu I$$
>	- Apply $U_{k}$ to **column** of $R_{k}$ with **additional shifting** to obtain new *unitary similar* **Hessenberg matrix** $H_{k}$ $$H_{k} = R_{k}\,U_{k} + \mu I$$

- [[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem]]


### Francis QR Step

## Explanation





-----------
##  Recommended Notes and References


- [[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem]]
- [[QR Iteration for General Eigenvalue Problem]]
- [[Schur Triangularization and Schur Form]]
- [[Jordan Canonical Form]]
- [[QR Factorization of Matrix]]


- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Matrix]]


- [[Matrix Computations by Golub]] pp 385 - 391