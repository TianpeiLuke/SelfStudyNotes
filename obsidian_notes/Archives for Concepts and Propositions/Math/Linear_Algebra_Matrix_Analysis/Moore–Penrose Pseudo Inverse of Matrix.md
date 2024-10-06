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
>Denote the **Moore-Penrose Pseudo Inverse** of $A$ as $A^{+}.$

^56d67e


## Explanation

>[!info]
>$$
>A\in \mathbb{R}^{n\times m}, \; A^{+} \in \mathbb{R}^{m \times n}
>$$

## Existence

>[!important] Proposition
>Let $A \in M_{n,m}$ be matrix of dimension $n\times m$.  
>
>The **Moore-Penrose Pseudo Inverse** $A^{+}$ **exists** and is **unique**.


## Properties

>[!important] Proposition
>Let $A \in M_{n,m}$ be matrix of dimension $n\times m$.  The **Moore-Penrose Pseudo Inverse** $A^{+}$.
>
>The following properties hold
>- If $A$ is **non-singular**, then $$A^{+} = A^{-1}.$$
>- **Dual Pseudo Inverse** $$\left(A^{+}\right)^{+} = A$$
>- **Pseudoinverse and Transpose** $$\left(A^{T}\right)^{+} = \left(A^{+}\right)^{T}$$
>- **Pseudoinverse of Symmetric Idempotent**: if $A^2= A$, $A = A^{T}$, then $$A^{+} = A$$
>- Both $$A\,A^{+}, \;\; A^{+}\,A$$ are **idempotent**.
>- **Rank**: $$\text{rank}(A) = \text{rank}(A^{+}) = \text{rank}\left(A\,A^{+}\right) = \text{rank}\left(A^{+}\,A\right)$$
>- $$A^{T}\,A\,A^{+} = A^{T} = A^{+}\,A\,A^{T}$$
>- $$A^{T}\,\left(A^{+}\right)^{T}\,A^{+} = A^{+}= A^{+}\,\left(A^{+}\right)^{T}\,A^{T}$$
>- $$\left(A^{T}\,A\right)^{+} = A^{+}\,\left(A^{+}\right)^{T},$$ $$\left(A\,A^{T}\right)^{+} = \left(A^{+}\right)^{T}\,A^{+}.$$
>- $$A\left(A^{T}\,A\right)^{+}\, A^{T}\,A = A = A\,A^{T}\left(A\,A^{T}\right)^{+}\,A$$
>- $$A^{+} = \left(A^{T}\,A\right)^{+}\,A^{T} = A^{T}\,\left(A\,A^{T}\right)^{+}$$
>- **Full Column Rank**: if $A$ has *full column rank*, $$A^{+} = \left(A^{T}\,A\right)^{-1}\,A^{T}.$$
>- **Full Row Rank**: if $A$ has *full row rank*, $$A^{+} = A^{T}\,\left(A\,A^{T}\right)^{-1}.$$
>- **Zero**: $$A = 0 \;\iff\; A^{+} = 0.$$
>- $$AB = 0 \;\iff \; B^{+}\,A^{+} = 0$$
>- $$A^{+}\,B = 0 \;\iff\; A^{T}\,B = 0$$
>- **Kronecker product** $$\left(A \otimes B\right)^{+} = A^{+} \otimes B^{+}.$$

^56317c

- [[Normal Transformation]]
- [[Rank and Nullity of Linear Map]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Range and Kernel of Product Map and Normal Map]]




## SVD of Moore-Penrose Pseudoinverse

![[Singular Value Decomposition and Pseudoinverse#^652a04]]

- [[Singular Value Decomposition and Pseudoinverse]]

## Orthogonal Project on Range and Kernel Spaces

![[Fundamental Orthogonal Projections#^6010c1]]

- [[Fundamental Orthogonal Projections]]




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
- [[Matrix CookBook by Petersen]] pp 21
- [[Numerical Linear Algebra by Trefethen]] pp 81 - 85, 94, 129, 335
- [[Convex Optimization by Boyd]] pp 88, 141, 153, 177, 185, 305