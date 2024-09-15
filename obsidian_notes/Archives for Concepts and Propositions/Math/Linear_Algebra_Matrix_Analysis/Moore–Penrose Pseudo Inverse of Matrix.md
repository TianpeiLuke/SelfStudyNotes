---
tags:
  - concept
  - math/matrix_analysis
  - statistics/estimation
  - math/linear_algebra
keywords:
  - moore_penrose_inverse
  - genearlized_inverse
  - matrix
  - pseudo_inverse_matrix
topics:
  - matrix_analysis
name: Moore–Penrose Generalized Inverse of Matrix
date of note: 2024-07-26
---

## Concept Definition

>[!important]
>**Name**: Moore–Penrose Pseudo Inverse of Matrix

>[!important] Definition
>Let $A \in M_{n,m}$ be matrix of dimension $n\times m$. 
>
>The **Moore-Penrose Pseudo Inverse** $X \in M_{m,n}$ of $A$ satisfies the following conditions
>- $$AXA = A$$
>- $$XAX = X$$
>- $$(AX)^{T} = AX$$
>- $$(XA)^{T} = XA$$
>  
>Denote the **Moore-Penrose Pseudo Inverse** of $A$ as $A^{\dagger}.$


## Explanation

>[!info]
>$$
>A\in \mathbb{R}^{n\times m}, \; A^{\dagger} \in \mathbb{R}^{m \times n}
>$$

## Existence

>[!important] Proposition
>Let $A \in M_{n,m}$ be matrix of dimension $n\times m$.  
>
>The **Moore-Penrose Pseudo Inverse** $A^{\dagger}$ **exists** and is **unique**.


## Properties

>[!important] Proposition
>Let $A \in M_{n,m}$ be matrix of dimension $n\times m$.  The **Moore-Penrose Pseudo Inverse** $A^{\dagger}$.
>
>The following properties hold
>- If $A$ is **non-singular**, then $$A^{\dagger} = A^{-1}.$$
>- **Dual Pseudo Inverse** $$\left(A^{\dagger}\right)^{\dagger} = A$$
>- **Pseudoinverse and Transpose** $$\left(A^{T}\right)^{\dagger} = \left(A^{\dagger}\right)^{T}$$
>- **Pseudoinverse of Symmetric Idempotent**: if $A^2= A$, $A = A^{T}$, then $$A^{\dagger} = A$$
>- Both $$A\,A^{\dagger}, \;\; A^{\dagger}\,A$$ are **idempotent**.
>- **Rank**: $$\text{rank}(A) = \text{rank}(A^{\dagger}) = \text{rank}\left(A\,A^{\dagger}\right) = \text{rank}\left(A^{\dagger}\,A\right)$$
>- $$A^{T}\,A\,A^{\dagger} = A^{T} = A^{\dagger}\,A\,A^{T}$$
>- $$A^{T}\,\left(A^{\dagger}\right)^{T}\,A^{\dagger} = A^{\dagger}= A^{\dagger}\,\left(A^{\dagger}\right)^{T}\,A^{T}$$
>- $$\left(A^{T}\,A\right)^{\dagger} = A^{\dagger}\,\left(A^{\dagger}\right)^{T},$$ $$\left(A\,A^{T}\right)^{\dagger} = \left(A^{\dagger}\right)^{T}\,A^{\dagger}.$$
>- $$A\left(A^{T}\,A\right)^{\dagger}\, A^{T}\,A = A = A\,A^{T}\left(A\,A^{T}\right)^{\dagger}\,A$$
>- $$A^{\dagger} = \left(A^{T}\,A\right)^{\dagger}\,A^{T} = A^{T}\,\left(A\,A^{T}\right)^{\dagger}$$
>- **Full Column Rank**: if $A$ has *full column rank*, $$A^{\dagger} = \left(A^{T}\,A\right)^{-1}\,A^{T}.$$
>- **Full Row Rank**: if $A$ has *full row rank*, $$A^{\dagger} = A^{T}\,\left(A\,A^{T}\right)^{-1}.$$
>- **Zero**: $$A = 0 \;\iff\; A^{\dagger} = 0.$$
>- $$AB = 0 \;\iff \; B^{\dagger}\,A^{\dagger} = 0$$
>- $$A^{\dagger}\,B = 0 \;\iff\; A^{T}\,B = 0$$
>- **Kronecker product** $$\left(A \otimes B\right)^{\dagger} = A^{\dagger} \otimes B^{\dagger}.$$

- [[Normal Transformation]]
- [[Rank and Nullity of Linear Map]]
- [[Least Square Estimation Solution and Geometric Interpretation]]




-----------
##  Recommended Notes and References

- [[Schur Complement and Inversion of Block Matrix]]
- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]
- [[Singular Value Decomposition of Linear Map]]


- [[Linear Regression]]
- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]

- Wikipedia [Moore-Penrose_inverse](https://en.wikipedia.org/wiki/Moore%E2%80%93Penrose_inverse)
- [[Matrix Analysis by Horn]] pp 453 - 454
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 29 - 31