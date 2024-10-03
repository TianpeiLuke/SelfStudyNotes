---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
keywords:
  - hessenberg_qr
  - shift_strategy_qr
topics:
  - numerical_linear_algebra
name: Shift Strategy for Faster QR Iterations
date of note: 2024-10-02
---

## Concept Definition

>[!important]
>**Name**: Shift Strategy for Faster QR Iterations

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

### Single-Shift Strategy

>[!info]
>Now let us consider varying $\mu$ from iteration to iteration incorporating **new information** about $\lambda(A)$ as the **subdiagonal entries converge to zero**.

>[!important] Definition
>The **single-shift QR iteration** choose the *last diagonal term* as the *heuristic* on *eigenvalue* $\mu$. Specifically,
>- For $k=1\,{,}\ldots{,}\,$:
>	- **Approximate** *eigenvalue* using the *last diagonal term*  $$\mu_{k} = H_{n,n}^{(k-1)}$$
>	- Compute the **QR factorization** for the shifted matrix $$U_{k} R_{k} = H^{(k-1)} - \mu_{k} I$$
>	- Apply $U_{k}$ to columns of $R_{k}$ to obtain *new matrix* $$H^{(k)} = R_{k}U_{k} + \mu_{k}I$$

### Double-Shift Strategy

>[!info]
>If the trailing principle submatrix $$H_{\{ n-1,n \}, \{ n-1,n \}}^{(k)} := \left[ \begin{array}{cc} h_{n-1, n-1}^{(k)} & h_{n-1, n}^{(k)} \\ h_{n, n-1}^{(k)} & h_{n,n}^{(k)}\end{array} \right] $$ has poor condition values, the estimate $$\mu_{k} = h_{n,n}^{(k)}$$ would be far from true eigenvalue.

>[!info]
>The **double-shift strategy** solve this by introducing two single-shift
>$$
>\begin{align*}
> U_{1}R_{1} &= H - a_{1}I\\[5pt]
> H_{1} &= R_{1}U_{1} + a_{1} I\\[5pt]
> U_{2}R_{2} &= H_{1} - a_{2}I\\[5pt]
> H_{2} &= R_{2}U_{2} + a_{2} I
>\end{align*}
>$$
>Unfortunately, *roundoff error* almost always prevents an exact return to the real field.
>
>We can also perfom explicit two-step
>$$
>\begin{align*}
> M &= H^2 - sH + tI\\[5pt]
> Q_{M} R &= M\\[5pt]
> H_{2} &= Q_{M}^T\,H\,Q_{M}
>\end{align*}
>$$
>But since the first of these steps requires $O(n^3)$ flops, this is not a practical course of action.

### Double-Implicit-Shift Strategy










## Explanation


- [[Shift Strategy for Faster Symmetric QR Iterations]]


-----------
##  Recommended Notes and References


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