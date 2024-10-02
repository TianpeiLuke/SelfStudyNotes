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
name: Hamiltonian Matrix
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  Hamiltonian Matrix

>[!important] Definition
>A matrix $M\in \mathbb{R}^{2n\times 2n}$ is  **Hamiltonian** if it has the form
>$$
>M := \left[ \begin{array}{cc}A & G \\[5pt] F & -A^{T} \end{array} \right] 
>$$
>where $A, F,G\in \mathbb{R}^{n\times n}$, and $F,G$ are both *symmetric*.

^14b90d

- [[Hermitian or Symmetric Matrix]]
- [[Inner Product Space]]

>[!important] Proposition
>A matrix $M\in \mathbb{R}^{2n\times 2n}$ is  **Hamiltonian** *if and only if* $M$ satisfies the following equation
>$$
> J\,M\,J^{T} = -M^{T} \quad \iff \quad J\,M = (J\,M)^{T}
>$$
>where 
>$$J = \left[ \begin{array}{cc}0 & I_{n} \\ -I_{n} &0\end{array} \right] $$ is a **permutation matrix**.

^6ddb7d

- [[Permutation Matrix and Reversal Matrix]]
- [[Skew-Hermitian and Skew-Symmetric Matrix]]

## Explanation

>[!info]
>$M$ is **Hamiltonian** if and only if $$JM$$ is **symmetric** where $J$ is the *skew-symmetric permtuation matrix*.


## Lie Algebra

>[!info]
>The *space of all Hamiltonian matrices*, denoted as $$\text{sp}(2n),$$  is a **Lie algebra**.
>- $$\text{dim}(\text{sp}(2n))= 2n^2 + n.$$
>- The corresponding **Lie group** is a **sympletic group.** $$\text{Sp}(2n)$$

- [[Lie Group and Lie Algebra]]


## Hamiltonian Mechanics

- [[Hamiltonian Function in Mechanic]]
- [[Hamiltonian Systems of Differential Equations]]

## Sympletic Matrix

![[Symplectic Matrix#^050719]]

- [[Symplectic Matrix]]

## Skew-Hamiltonian matrix

![[Skew-Hamiltonian Matrix#^b17e61]]

![[Skew-Hamiltonian Matrix#^6ddb7d]]

- [[Skew-Hamiltonian Matrix]]


-----------
##  Recommended Notes and References


- [[Symplectic Matrix]]
- [[Linear Map]]
- [[Matrix]]

- [[Inner Product Space]]
- [[Vector Space over a Field]]

- [[Hamiltonian Function in Mechanic]]
- [[Hamiltonian Systems of Differential Equations]]



- [[Matrix Computations by Golub]] pp 29, 420
- [[Introduction to Smooth Manifolds by Lee]]
- Wikipedia [Hamiltonian_matrix](https://en.wikipedia.org/wiki/Hamiltonian_matrix)