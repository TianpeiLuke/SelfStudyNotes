---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - rayleigh_quotient
  - eigen_value
  - eigenvalue_problem
topics:
  - matrix_analysis
  - linear_algebra
name: Rayleigh Quotient for Eigenvalue Problem
date of note: 2024-08-21
---

## Concept Definition

>[!important]
>**Name**: Rayleigh Quotient for Eigenvalue Problem

>[!important] Definition
>Let $A\in M_{n}$ be a *Hermitian matrix*. 
>
>The **Rayleigh quotient** associated with $A$ is defined as
>$$R(A, x) := \frac{\left\langle  x\,,\, Ax   \right\rangle}{\left\langle  x\,,\,x    \right\rangle}, \quad \forall\,  0 \neq x\in \mathbb{C}^{n}$$

^2635f7

- [[Hermitian or Symmetric Matrix]]
- [[Sesquilinear Form]]


## Explanation

>[!info]
>The Rayleigh quotient is used in the **min-max theorem** to get exact values of all eigenvalues. It is also used in *eigenvalue algorithms* (such as [Rayleigh quotient iteration](https://en.wikipedia.org/wiki/Rayleigh_quotient_iteration "Rayleigh quotient iteration")) to obtain an eigenvalue approximation from an eigenvector approximation.


## Variational Characterization of Eigenvalue Problem

![[Variational Characterization of Eigenvalues of Hermitian Matrix#^50523d]]

- [[Variational Characterization of Eigenvalues of Hermitian Matrix]]

##  Min-Max Theorem

![[Courant-Fischer Minimax Theorem#^3d4e1f]]

- [[Courant-Fischer Minimax Theorem]]

## Principle Component Analysis

![[Principle Component Analysis#^d06ebc]]

- [[Principle Component Analysis]]



-----------
##  Recommended Notes and References

- [[Convex Optimization for Eigenvalue Problem]]


- [[Courant-Fischer Minimax Theorem]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Spectrum of Adjoint of Linear Operator]]
- [[Multilinear Function]]


- Wikipedia [Rayleigh_quotient](https://en.wikipedia.org/wiki/Rayleigh_quotient)
- [[Matrix Analysis by Horn]] pp 44
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 100
- [[Matrix Computations by Golub]]
- [[Numerical Linear Algebra by Trefethen]] pp 203 - 204
- [[Convex Optimization by Boyd]]