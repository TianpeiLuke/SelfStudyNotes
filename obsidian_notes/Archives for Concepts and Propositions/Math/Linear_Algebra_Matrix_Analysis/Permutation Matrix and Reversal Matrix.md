---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - permutation
  - permutation_group
  - permutation_matrix
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Permutation Matrix
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Permutation Matrix

>[!important] Definition
>A square matrix $P$ is a **permutation matrix** if exactly *one entry* in each *row* and *column* is equal to $1$ and all other entries are $0$.
>
>- *Left multiplication* of a matrix $A \in M_{m,n}$ by an $m\times m$ **permutation matrix** $P$ *permutes* the *rows* of $A$, $$\hat{A} := P\,A$$ 
>- while *right multiplication* of $A$ by an $n\times n$ **permutation matrix** $P$ *permutes* the *columns* of $A$. $$\tilde{A} := A\,P$$

- [[Elementary Row and Column Operations]]

>[!important] Definition
>The $n\times n$ **reversal matrix** is the *permutation matrix*
>$$
>K_{n} = \left[ \begin{array}{cccc} & & & 1\\ &  & 1 & \\  & \cdots & & \\ 1 & & & \end{array} \right] = [K_{i,j}] \in M_{n}
>$$
>where $K_{i, n-i+1} = 1$ and all other entries are zero. 
>
>The reversal matrix is sometimes called the **sip matrix** (**standard involutory permutation**), the **backward identity**, or the **exchange matrix**.
>- $$K_{n}\,A$$ has the *rows* of $A$ in **reversed order.**
>- $$A\,K_{n}$$ has the *columns* of $A$ in **reversed order.**

>[!important] Definition
>For any n-by-n matrix $A=[a_{i,j}]$ the entries $$a_{i, n-i+1}, \quad \text{ for } i = 1 \,{,}\ldots{,}\,n$$ comprise its **counterdiagonal** (sometimes called the **secondary diagonal**, **backward diagonal**, **cross diagonal**, **dexter-diagonal**, or **antidiagonal**).


## Explanation


## Determinant

>[!important] Proposition
>The **determinant** of **permutation** $P\in M_{n}$ is $$\det(P) = \pm 1.$$ That is, a permutation matrix is **non-singular**. Moreover, $$P^{T} = P^{-1}.$$


## Group of Permutation Matrices


>[!info]
>The set of *all permutation matrices* is a **permutation group** $S_{n}$.
>$$S_{n} \subset  \text{SL}(n, F)$$

- [[Symmetric Group]]
- [[Special Linear Group]]





-----------
##  Recommended Notes and References


- [[Skew-Hermitian and Skew-Symmetric Matrix]]

- [[Elementary Row and Column Operations]]
- [[Circulant Matrix and Circulant Permutation Operation]]
- [[Discrete Fourier Transform]]
- [[Matrix]]
- [[Symmetric Group]]



- [[Numerical Linear Algebra by Trefethen]] 
- [[Matrix Computations by Golub]] pp 
- [[Matrix Analysis by Horn]] pp 32 - 33
- [[Matrix CookBook by Petersen]] pp 56