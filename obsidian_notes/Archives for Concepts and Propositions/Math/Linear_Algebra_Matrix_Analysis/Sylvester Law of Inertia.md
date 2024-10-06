---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - sylvester_law_of_inertia
topics:
  - matrix_analysis
  - linear_algebra
name: Sylvester Law of Inertia
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Sylvester Law of Inertia

![[Inertia of Self-Adjoint Map#^8866a8]]

![[Congruence Relation between Matrices#^b79387]]

![[Inertia of Self-Adjoint Map#^9067ee]]

![[Inertia of Self-Adjoint Map#^2f1958]]

>[!important] Theorem (Sylvester Law of Inertia)
>Let $A\in \mathbb{C}^{n\times n}$ be **Hermitian** and $X\in \mathbb{R}^{n\times n}$ be **nonsingular**.
>
>Then $A$ and $X^{*}AX$ have the **same inertia.**

^90743f

- [[Inertia of Self-Adjoint Map]]
- [[Congruence Relation between Matrices]]

>[!important] Sylvester Law of Inertia
>Let $A, B\in \mathbb{C}^{n\times n}$ be **Hermitian**.
>
>$A$ and $B$ are **$*$-congruent** *if and only if* they have the **same inertia**, that is, *if and only if* they have the **same number of positive and negative eigenvalues.**
>$$
>B = SAS^{*}\;\; \equiv\;\; A \sim B \;\; \iff \;\; I(A) = I(B)
>$$

^901bbd

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Hermitian or Symmetric Matrix]]

## Explanation





-----------
##  Recommended Notes and References




- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


- [[Infinitesimal Generator of Stochastic Differential Equation]]
- [[Martingale via Solution of SDE and Backward Equation]]
- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]


- [[Matrix Analysis by Horn]] pp 282 - 289
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 103
- [[Matrix Computations by Golub]] pp 448