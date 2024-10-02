---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
  - math/differential_equation
  - numerical_methods/numerical_differential_equations
  - math/differential_geometry
keywords:
  - symplectic_matrix
topics:
  - linear_algebra
  - matrix_analysis
  - differential_equation
  - numerical_linear_algebra
  - numerical_differential_equation
  - differential_geometry
name: Symplectic Matrix
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  Symplectic Matrix

![[Self-Adjoint Linear Map#^29c1d7]]

![[Hermitian or Symmetric Matrix#^9ff922]]

![[Hamiltonian Matrix#^6ddb7d]]

- [[Hamiltonian Matrix]] ^678224
- [[Inner Product Space]]

>[!important] Definition
>A matrix $S\in \mathbb{R}^{2n\times 2n}$ is  **symplectic** if 
>$$
> S^{T}\,J\,S = J \quad \iff \quad JS = (S^{-1})^{T}J
>$$
>where 
>$$J = \left[ \begin{array}{cc}0 & I_{n} \\ -I_{n} &0\end{array} \right] $$ is the **permutation matrix**.

^050719

- [[Permutation Matrix and Reversal Matrix]]
- [[Skew-Hermitian and Skew-Symmetric Matrix]]

## Explanation

>[!info]
>For block **symplectic matrix** 
>$$
>S = \left[ \begin{array}{cc}S_{11} & S_{12}\\ S_{21} & S_{22}\end{array} \right] 
>$$
>we have 
>$$
>S_{11}^{T}\,S_{21}, \quad S_{22}^{T}\,S_{12}
>$$
>are both **symmetric**. Moreover,
>$$
>S_{11}^T\,S_{22} = I_{n} + S_{21}^{T}\,S_{12} 
>$$

## Hamiltonian Matrix

- [[Hamiltonian Matrix]]
- [[Hamiltonian Function in Mechanic]]

## Hamiltonian System of Equations


- [[Hamiltonian Systems of Differential Equations]]
- [[Hamiltonian Monte Carlo]]

## Sympletic Group





-----------
##  Recommended Notes and References




- [[Hamiltonian Matrix]]
- [[Hamiltonian Function in Mechanic]]
- [[Hamiltonian Systems of Differential Equations]]

- [[Linear Map]]
- [[Matrix]]

- [[Inner Product Space]]
- [[Vector Space over a Field]]


- [[Matrix Computations by Golub]] pp 29
- [[Introduction to Smooth Manifolds by Lee]]
- Wikipedia [Symplectic_matrix](https://en.wikipedia.org/wiki/Symplectic_matrix)