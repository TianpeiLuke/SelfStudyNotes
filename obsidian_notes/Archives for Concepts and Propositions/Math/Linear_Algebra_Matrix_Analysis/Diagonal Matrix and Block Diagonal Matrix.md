---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - diagonal_matrix
  - block_diagonal_matrix
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Diagonal Matrix and Block Diagonal Matrix
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Diagonal Matrix and Block Diagonal Matrix

### Square Matrix

>[!important] Definition
>A matrix $D=[a_{i,j}]\in M_{n}$ is called an **diagonal matrix** if $a_{i,j} =0$ whenever $j \neq i$, i.e.  $$D = \left[ \begin{array}{ccccc}a_{11} &  &  & 0 \\[5pt]  & a_{22} &  &  \\[5pt]  &  & \ddots &  \\[5pt] 0 &  &  & a_{nn}\end{array} \right].$$
>We denote it as $$D = \text{diag}(a_{11} \,{,}\ldots{,}\,a_{nn}).$$
>- If $a_{ii} >0$ for all $i$, we call $D$ a **positive diagonal matrix**
>- If $a_{ii} <0$ for all $i$, we call $D$ a **negative diagonal matrix**.
>- If $a_{ii} \ge 0$ for all $i$, we call $D$ a **nonnegative diagonal matrix**
>- If $a_{ii} \le 0$ for all $i$, we call $D$ a **nonpositive diagonal matrix**.

- [[Nonnegative and Positive Matrix]]
- [[Matrix Transformation]]

### Diagonal Operation

>[!important] Definition
>Given a matrix $A = [a_{i,j}]$, the **diagonal operation** of $A$ is a vector given by the diagonal terms of $A$
>$$
>\text{diag}(A) = \left( a_{11} \,{,}\ldots{,}\, a_{nn}\right) \in F^{n}.
>$$
>
>Conversely, given a vector $d = (d_{1} \,{,}\ldots{,}\,d_{n})$, then **diagonal transformation**  of $d$
>$$
>\text{diag}(d) := \text{diag}\left\{ d_{1} \,{,}\ldots{,}\,d_{n} \right\} =  \left[ \begin{array}{ccccc} d_{1} &  &  & 0 \\[5pt]  & d_{2} &  &  \\[5pt]  &  & \ddots &  \\[5pt] 0 &  &  & d_{n}\end{array} \right].
>$$


### Non-Square Matrix

>[!important] Definition
>A matrix $T\in M_{m,n}$ is **diagonal** if 
>$$
>T = \left\{\begin{array}{cc}\left[ D, \; 0 \right] & \text{ if }m \le n \\[5pt] \left[\begin{array}{c} D\\[5pt] 0  \end{array}\right]  & \text{ if }m \ge n \end{array}\right.
>$$
>where $D\in M_{min\left\{ m,n \right\}}$ is *diagonal*.



### Block Diagonal Matrix

>[!important] Definition
>A matrix $U=[A_{i,j}]\in M_{n}$  is called an **block diagonal matrix** if $A_{i,j} =0$ whenever $j \neq i$, where $$A_{i,j}\in M_{n_{i}}, \quad \sum_{i=1}^{k}n_{i} = n$$ i.e. $$U = \left[ \begin{array}{ccccc}A_{11} &  &  & \\[5pt]  & A_{22} &  &  \\[5pt]  &  & \ddots &  \\[5pt] &  &  & A_{kk}\end{array} \right].$$ 
>
>It is convenient to write the block diagonal matrix as the **direct sum** of matrices $$A = \bigoplus_{i=1}^{k}A_{ii} = A_{11}\,{\oplus}\ldots{\oplus}\,A_{kk}.$$

- [[Direct Sum of Subspaces]]


## Explanation



## Properties




## Diagonalization

- [[Diagonalizable Matrix]]
- [[Simultaneously Diagonalizable Matrices]]
- [[Unitary Similarity and Unitary Diagonalizable]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]




-----------
##  Recommended Notes and References

- [[Triangular Matrix and Block Triangular Matrix]]
- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]


- [[Matrix Computations by Golub]] pp 
- [[Matrix Analysis by Horn]] pp 30 - 31
- [[Matrix Analysis for Scientists and Engineers by Laub]]