---
tags:
  - concept
  - math/linear_algebra
keywords:
  - positive_semidefinite_matrix
  - positive_definite_matrix
topics:
  - linear_algebra
name: Positive Semidefinite Transformation
date of note: 2024-07-03
---

## Concept Definition

>[!important]
>**Name**: Positive Semidefinite Transformation

>[!important] Definition
>A *Hermitian matrix* $A \in \mathbb{C}^{n \times n}$ is **positive definite** if 
>$$
>x^{*}\,A\,x > 0, \quad \forall \text{ nonzero } x \in \mathbb{C}^{n}
>$$
>We denote it as
>$$
>A \succ 0.
>$$

>[!important] Definition
>A *Hermitian matrix* $A \in \mathbb{C}^{n \times n}$ is **positive semidefinite** if 
>$$
>x^{*}\,A\,x \ge 0, \quad \forall x \in \mathbb{C}^{n}
>$$
>We denote it as 
>$$
>A \succeq 0.
>$$

- [[Self-Adjoint Linear Map]]

>[!important] Definition
>The **space** of *all positive semidefinite matrices*
>$$
>\mathcal{S}_{+} = \left\{A \in \mathbb{C}^{n\times n}: A = A^{*},\;\; x^{*}\,A\,x \ge 0, \quad \forall x \in \mathbb{C}^{n}  \right\} 
>$$
>
>The **space** of *all positive definite matrices*
>$$
>\mathcal{S}_{++} = \left\{A \in \mathbb{C}^{n\times n}: A = A^{*},\;\; x^{*}\,A\,x > 0, \quad \forall \text{ nonzero }x \in \mathbb{C}^{n}  \right\} 
>$$


## Explanation

>[!info]
>For Hermitian matrix $A$, then for all $x\in \mathbb{C}^n$,
>$$
>x^{*}\,A\,x \in \mathbb{R}
>$$


## Positive Semidefinite Operator

- [[Positive Semidefinite Operator]]



-----------
##  Recommended Notes and References

- [[Matrix]]

- [[Adjoint of Linear Map]]
- [[Unitary and Orthogonal Transformation]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]


- [[Gaussian Random Vector]]


- [[Matrix Analysis by Horn]] pp 429
- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Computations by Golub]]
- [[Matrix CookBook by Petersen]] pp 50