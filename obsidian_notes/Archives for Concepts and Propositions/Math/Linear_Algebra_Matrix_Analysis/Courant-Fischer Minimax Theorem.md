---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - courant_fischer_minimax_theorem
topics:
  - matrix_analysis
  - linear_algebra
name: Courant-Fischer Minimax Theorem
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Courant-Fischer Minimax Theorem

>[!important] Theorem
>If $A\in \mathbb{R}^{n\times n}$ is a **symmetric matrix**, then the **$k$-th largest eigenvalue** of $A$ is obtained as
>$$
>\lambda_{k}(A) = \max_{\text{dim}(S) = k}\;\min_{y\in S,\, y\neq 0} \frac{\left\langle  y\,,\, Ay   \right\rangle}{\left\langle  y\,,\,y    \right\rangle}, \quad k=1\,{,}\ldots{,}\,n.
>$$

- [[Hermitian or Symmetric Matrix]]
- [[Eigenvalue and Eigenvector for Linear Map]]




## Explanation

>[!info]
>The **eigenvalues** of a *symmetric matrix* have a **minimax** *characterization* that  revolves around the quadratic form $$\frac{x^T\,A\,x}{x^T\,x}$$

- [[Rayleigh Quotient for Eigenvalue Problem]]



-----------
##  Recommended Notes and References


- [[Minimax Theorem]]
- [[Rayleigh Quotient for Eigenvalue Problem]]


- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Principle Component Analysis]]
- [[Schur Triangularization and Schur Form]]



- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 441
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]]