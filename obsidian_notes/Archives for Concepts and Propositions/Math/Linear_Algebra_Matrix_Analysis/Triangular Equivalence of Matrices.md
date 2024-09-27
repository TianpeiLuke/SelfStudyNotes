---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - triangular_equivalence_matrix
topics:
  - matrix_analysis
  - numerical_linear_algebra
name: Triangular Equivalence of Matrices
date of note: 2024-09-23
---

## Concept Definition

>[!important]
>**Name**: Triangular Equivalence of Matrices

>[!important] Definition
>Two matrices $A, B\in M_{n}$ are said to be **triangular equivalent** if there are *nonsingular matrices* $L,U\in M_{n}$ such that $L$ is *lower triangular*, and $U$ is *upper triangular*, and $$A = L\,B\,U.$$

- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Permutation Matrix and Reversal Matrix]]

## Explanation




## Permutation Matrix as Canonical Form for Triangular Equivalence of Nonsingular Matrix

### LPU Factorization

![[LPU Factorization of Nonsingular Matrix#^463de6]]

- [[LPU Factorization of Nonsingular Matrix]]

### Canonical Form

>[!important] Theorem
>Let $A, B\in M_{n}$ be **nonsingular.**
>
>The following are **equivalent**:
>- There is a **unique permutation matrix** $P\in M_{n}$ such that both $A$ and $B$ are **triangularly equivalent** to $P$. $$A = L\,P\,U.$$
>- $A$ and $B$ are **triangularly equivalent**.
>- The following **rank equalities** hold for all $p,q\in \left\{ 1\,{,}\ldots{,}\, n\right\}$ $$\text{rank}(A[1:p, 1:q]) = \text{rank}(B[1:p, 1:q]).$$

- [[Partition of Matrix and Block Matrix]]
- [[Principal Submatrix]]
- [[Rank and Nullity of Linear Map]]

### LPDU Factorization

![[LPDU Factorization of Nonsingular Matrix and Pivoting#^f64407]]

- [[LPDU Factorization of Nonsingular Matrix and Pivoting]]






-----------
##  Recommended Notes and References


- [[LPU Factorization of Nonsingular Matrix]]
- [[LU Factorization of Matrix]]
- [[LDU Factorization of Symmetric Matrix]]
- [[LDU Factorization with Symmetric Pivoting]]


- [[Unitary Similarity and Unitary Diagonalizable]]
- [[Similarity Relation between Linear Maps and Matrices]]
- [[Equivalence Relation]]
- [[Equivalence Class]]


- [[Matrix Computations by Golub]]
- [[Matrix Analysis by Horn]] pp 220