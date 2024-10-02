---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - qr_factorization
topics:
  - numerical_linear_algebra
  - matrix_analysis
  - linear_algebra
name: QR Factorization of Matrix
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: QR Factorization of Matrix

>[!important] Theorem (QR Factorization)
>Let $A\in M_{m,n}$.
>
>- If $m \ge n$, there **exists** a matrix $Q\in M_{m,n}$ with **orthonormal columns** i.e. $$Q=[q_{1}\,{,}\ldots{,}\,q_{n}],\quad \left\langle q_{i},q_{j} \right\rangle = \delta_{i,j}$$ and an **upper triangular matrix** $R\in M_{n}$ with **non-negative main diagonal entries** such that $$A = Q\,R.$$
>- If $\text{rank}(A) = n$ (i.e. $A$ has **full column rank**), then the factors $Q$ and $R$ are **uniquely** determined and the **main diagonal entries** are **all positive**.  
>- If $m=n$ then $Q\in \mathcal{U}(n)$ is **unitary.** $$Q^{*}\,Q = Q\,Q^{*} = I_{n}.$$
>- There **exists** a **unitary** $Q\in \mathcal{U}(m)$, and an **upper triangular** $R\in M_{m,n}$ with **non-negative  diagonal entries** such that $$A = Q\,R.$$
>- If $A\in \mathbb{R}^{m\times n}$, then all factors $Q, R$ in above may be taken to be real.

^b07f79

^b07f79

- [[Orthogonality in Inner Product Space]]
- [[Unitary and Orthogonal Transformation]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Surjective Injective Invertible Linear Map and Rank]]

>[!important] Definition
>Let $A\in M_{m,n}$.
>
>The **QR factorization** of $A$ is given by $$A = Q\,R$$ where $Q$ has *orthonormal columns* and $R$ is an *upper triangular matrix* with *non-negative diagonal entries.*

>[!important] Proposition
>Let $A\in \mathbb{R}^{m\times n}$ be a matrix with **full column rank**, and $$A = QR$$ be the **QR factorization** of $A$.
>
>Let  
>- $A = [a_{1}\,{,}\ldots{,}\,a_{n}]$ be **column partition** of $A$ with columns $a_{i}$ and
>- $Q = [q_{1}\,{,}\ldots{,}\,q_{m}]\in \mathcal{U}(m)$  be **column partition** of $Q$ with columns $q_{i}$.
>
> Then for $k=1\,{,}\ldots{,}\,n$
> $$
> \text{span}\left\{ a_{1}\,{,}\ldots{,}\,a_{k}  \right\} = \text{span}\left\{ q_{1}\,{,}\ldots{,}\,q_{k} \right\}. 
> $$  
>and the **diagonal terms** of *upper triangular matrix* $r_{kk} \neq_{0}$. 
>
>Moreover, if 
>- $Q_{1} = [q_{1}\,{,}\ldots{,}\,q_{n}]\in M_{m\times n}$ and 
>- $Q_{2} = [q_{n+1}\,{,}\ldots{,}\,q_{m}]$, and 
>- $R_{1} = R[1:n, 1:n]$ is the leading principal matrix of $R$
>
>then
>$$
>\begin{align*}
> \text{R}(A) &= \text{R}(Q_{1}) \\[5pt]
> \text{R}(A)^{\perp} &= \text{R}(Q_{2})
>\end{align*}
>$$
>and
>$$
>A = Q_{1}\,R_{1}
>$$

- [[Linear Span over a Set of Vectors]]
- [[Range and Kernel of Linear Map]]
- [[Partition of Matrix and Block Matrix]]


## Explanation

>[!info]
>The following factorization is equivalent
>$$
>A = L\,Q
>$$
>where $L$ is a *lower triangular matrix* with *non-negative diagonal entries* and $Q$ has **orthonormal rows**.


## QR Factorization Algorithms

### QR Factorization via Householder Transformation

- [[Householder Transformation and Householder Reflection]]
- [[Householder QR Factorization]]
- [[Block Householder QR Factorization]]

### QR Factorization via Givens Transformation

- [[Givens Rotations and Jacobi Rotations]]
- [[Givens QR Factorization]]

### QR Factorization via Gram-Schmidt Orthogonalization

- [[Gram-Schmidt Orthogonalization]]
- [[Modified Gram-Schmidt Algorithm for QR Factorization]]


-----------
##  Recommended Notes and References

- [[Orthogonality in Inner Product Space]]


- [[Triangular Matrix and Block Triangular Matrix]]
- [[Unitary and Orthogonal Transformation]]
- [[Matrix]]


- [[Matrix Computations by Golub]] pp 246 - 248
- [[Matrix Analysis by Horn]] pp 89 - 91
- [[Numerical Linear Algebra by Trefethen]] pp 48 - 56
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 72