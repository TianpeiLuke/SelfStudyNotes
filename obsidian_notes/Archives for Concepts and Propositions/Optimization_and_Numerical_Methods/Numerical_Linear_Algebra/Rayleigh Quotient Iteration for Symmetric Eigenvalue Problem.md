---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - rayleigh_quotient
  - rayleigh_quotient_iteration
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Rayleigh Quotient Iteration for Symmetric Eigenvalue Problem
date of note: 2024-10-01
---

## Concept Definition

>[!important]
>**Name**: Rayleigh Quotient Iteration for Symmetric Eigenvalue Problem

![[Rayleigh Quotient for Eigenvalue Problem#^2635f7]]


![[Power Iteration and Inverse Iteration for General Eigenvalue Problem#^9b3cc4]]


![[rayleigh_quotient_power_inverse.png]]

>[!important] Definition
>Let $A\in \mathbb{R}^{n\times n}$ be **symmetric**. Consider the *eigenvalue problem* $$Ax = \lambda x.$$
>
>The **Rayleigh quotient iteration** that approximates both *eigenvalue* and corresponding *eigenvector* as follow
>- *Require*: $A\in \mathbb{R}^{n\times n}$ **symmetric**
>- *Require*: initial $x_{0}\neq 0 \in \mathbb{R}^{n}$with **unit norm** $\lVert x_{0} \rVert_{2} = 1$
>- For $k=0\,{,}\ldots{,}\,$ until convergence:
>	- Approximate **eigenvalue** using **Rayleigh Quotient** $$\lambda_{k} = R(A, x_{k}) = \left\langle x_{k} , Ax_{k} \right\rangle$$
>	- Approximate corresponding **eigenvector** by solving resolvant equation $$\left( A - \lambda_{k} I\right)z = x_{k}$$ with *solution* $$z_{k+1} = \left( A - \lambda_{k} I\right)^{-1}\,x_{k}$$
>	- Normalize $$x_{k+1} = \frac{z_{k+1}}{\lVert z_{k+1} \rVert }$$


- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Power Iteration and Inverse Iteration for General Eigenvalue Problem]]

## Explanation





-----------
##  Recommended Notes and References



- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Variational Characterization of Eigenvalues of Hermitian Matrix]]
- [[Courant-Fischer Minimax Theorem for Eigenvalue Problem]]


- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Hermitian or Symmetric Matrix]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 453
- [[Numerical Linear Algebra by Trefethen]] pp 207 - 209