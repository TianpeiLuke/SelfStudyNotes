---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
  - math/differential_equation
  - numerical_methods/numerical_differential_equations
  - math/differential_geometry
keywords:
  - hamiltonian_matrix
topics:
  - linear_algebra
  - matrix_analysis
  - differential_equation
  - numerical_linear_algebra
  - numerical_differential_equation
  - differential_geometry
name: Skew-Hamiltonian Matrix
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  Skew-Hamiltonian Matrix

![[Hamiltonian Matrix#^14b90d]]

- [[Hamiltonian Matrix]]

>[!important] Definition
>A matrix $N\in \mathbb{R}^{2n\times 2n}$ is  **skew-Hamiltonian** if it has the form
>$$
>N := \left[ \begin{array}{cc}A & G \\[5pt] F & A^{T} \end{array} \right] 
>$$
>where $A, F,G\in \mathbb{R}^{n\times n}$, and $F,G$ are both *skew-symmetric*.

^b17e61

- [[Skew-Hermitian and Skew-Symmetric Matrix]]
- [[Inner Product Space]]

>[!important] Proposition
>A matrix $N\in \mathbb{R}^{2n\times 2n}$ is  **skew-Hamiltonian** *if and only if* $M$ satisfies the following equation
>$$
> J\,N\,J^{T} = N^{T} \quad \iff J\,N = -(J\,N)^{T}
>$$
>where 
>$$J = \left[ \begin{array}{cc}0 & I_{n} \\ -I_{n} &0\end{array} \right] $$ is a **permutation matrix**.

^6ddb7d

- [[Permutation Matrix and Reversal Matrix]]
- [[Skew-Hermitian and Skew-Symmetric Matrix]]

## Explanation






-----------
##  Recommended Notes and References


- [[Hamiltonian Matrix]]
- [[Symplectic Matrix]]
- [[Linear Map]]
- [[Matrix]]

- [[Inner Product Space]]
- [[Vector Space over a Field]]

- [[Hamiltonian Function in Mechanic and Variational Calculus]]
- [[Hamiltonian Systems of Differential Equations]]



- [[Matrix Computations by Golub]] pp 29, 420
- [[Introduction to Smooth Manifolds by Lee]]
- Wikipedia [Hamiltonian_matrix](https://en.wikipedia.org/wiki/Hamiltonian_matrix)