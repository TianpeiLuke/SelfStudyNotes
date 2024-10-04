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

![[Variational Characterization of Eigenvalues of Hermitian Matrix#^50523d]]

- [[Variational Characterization of Eigenvalues of Hermitian Matrix]]

>[!important] Theorem
>Let $A\in M_{n}$ be a **Hermitian matrix**, and $S \subset \mathbb{C}^{n}$ be a finite-dimensional linear subspace. Let **eigenvalues** of $A$ be ordered as $$\lambda_{min} = \lambda_{n} \,{\le}\ldots{\le}\,\lambda_{1} = \lambda_{max}.$$
>
>Then the **$k$-th largest eigenvalue** of $A$ is obtained as
>$$
>\lambda_{k}(A) = \max_{\text{dim}(S) = k}\;\min_{0\neq x\in S} \frac{\left\langle x , Ax \right\rangle}{\left\langle  x,x    \right\rangle}, \quad k=1\,{,}\ldots{,}\,n.
>$$
>and 
>$$
>\lambda_{k}(A) = \min_{\text{dim}(S) = n - k + 1}\;\max_{0\neq x\in S} \frac{\left\langle x , Ax \right\rangle}{\left\langle  x,x    \right\rangle}, \quad k=1\,{,}\ldots{,}\,n.
>$$

^3d4e1f

- [[Hermitian or Symmetric Matrix]]
- [[Eigenvalue and Eigenvector for Linear Map]]



## Explanation

>[!info]
>The **eigenvalues** of a *symmetric matrix* have a **minimax** *characterization* that  revolves around the quadratic form $$\frac{x^T\,A\,x}{x^T\,x}$$

- [[Rayleigh Quotient for Eigenvalue Problem]]

## Variational Characterization of Eigenvalue of Hermitian Matrix

- [[Variational Characterization of Eigenvalues of Hermitian Matrix]]



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
- [[Saddle Point of Lagrangian Function]]


- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Matrix Analysis by Horn]] pp 235 - 238
- [[Finite Dimensional Vector Spaces by Halmos]] pp 181
- [[Matrix Computations by Golub]] pp 441
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]]