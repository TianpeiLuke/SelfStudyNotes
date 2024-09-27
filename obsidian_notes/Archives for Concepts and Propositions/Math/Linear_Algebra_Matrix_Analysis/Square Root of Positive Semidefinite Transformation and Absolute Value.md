---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - square_root_positive_semidefinite_transformation
topics:
  - functional_analysis
name: Square Root of Positive Semidefinite Matrix
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Square Root of Positive Semidefinite Transformation and  Absolute Value

![[Square Root of Positive Semidefinite Operator and Absolute Value#^37d617]]

>[!important] Theorem
>Let $A\in M_{n}$ be **Hermitian**.
>
>- $A$ is **positive semidefinite** *if and only if* there exists a $B\in M_{m,n}$ such that $$A = B^{*}B.$$
>- If $A = B^{*}B$ with $B\in M_{m,n}$, and if $x\in \mathbb{C}^{n}$, then the **normal equation** $$Ax = 0 \; \iff \; Bx = 0,$$ so $$\text{Ker}(A) = \text{Ker}(B), \quad \text{rank}(A) = \text{rank}(B)$$
>- If $A = B^{*}B$ with  $B\in M_{m,n}$,  then $A$ is **positive definite** *if and only if* $B$ has **full column rank.**

^4879e9

- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]
- [[Surjective Injective Invertible Linear Map and Rank]]


>[!important] Definition
>Let $A \in M_{n}$ (i.e. $A\in \mathcal{L}(V)$). The **absolute value** of matrix (linear transformation) $A$ is defined as
>$$
>\lvert A \rvert := \sqrt{ A^{*}A } := A^{1 / 2}. 
>$$

- [[Adjoint of Linear Map]]


## Explanation






-----------
##  Recommended Notes and References

- [[Square Root of Positive Semidefinite Operator and Absolute Value]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]

- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]
- [[Normal Transformation]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 440 - 441