---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - symmetric_qr_iteration
  - eigenvalue_problem
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Symmetric QR Iteration for Symmetric Eigenvalue Problem
date of note: 2024-10-02
---

## Concept Definition

>[!important]
>**Name**: Symmetric QR Iteration for Symmetric Eigenvalue Problem

### Tridiagonal Reduction for Symmetric Matrix

![[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation#^7e7a23]]

- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]

### Implicit Symmetric QR Step with Wilkinson Shift

![[Shift Strategy for Faster Symmetric QR Iterations#^4796e1]]

![[Shift Strategy for Faster Symmetric QR Iterations#^ab31a0]]

- [[Shift Strategy for Faster Symmetric QR Iterations]]

### Put it Together

>[!important] Definition
>Consider the task of computing the **symmetric Schur decomposition**, or the **eigen-decomposition** of **symmetric matrix** $A\in \mathbb{R}^{n\times n}$, $$D = Q^{T}\,A\,Q.$$
>
>The **symmetric QR iteration algorithm** approximates the eigen-decomposition as follows
>- *Require*: $A\in \mathbb{R}^{n\times n}$ *symmetric*
>- *Require*: tolerance threshold $\text{tol} >0$
>- **Tridiagonal decomposition**: compute $$T = U^{T}AU$$ where
>	- $T$ is a *symmetric tridiagonal matrix*
>	- $U = P_{1}\,{,}\ldots{,}\,P_{n-2}$ is the product of *Householder transformation* 
>- Set $$D := T$$
>	- If $Q$ is desired, form $$Q = P_{1}\,{,}\ldots{,}\,P_{n-2}$$ via *back accumulation*.
>- While $q < n$:
>	- **Partition into Reducible Submatrices**
>		- For $i=1\,{,}\ldots{,}\,n-1$:
>			- Set $D_{i+1,i} = D_{i,i+1} =0$ if $$|D_{i+1,i}| = |D_{i,i+1}| \le \text{tol}\cdot \left( |D_{i,i}| + |D_{i+1,i+1}|  \right)$$
>		- Find *largest* $q$ and *smallest* $p$ such that for the **block diagonal matrix** $$D = \left[ \begin{array}{ccc}D_{\left\{ 1:p \right\}} & 0 & 0\\[5pt] 0& D_{\left\{ p+1:n-q \right\}} & 0 \\[5pt] 0 & 0 & D_{\left\{ n-q+1:n \right\}}\end{array} \right] $$ we have
>			- $D_{\left\{ n-q+1:n \right\}}$ is **diagonal**
>			-  $D_{\left\{ p+1:n-q \right\}}$ is **unreduced**
>	- If $q < n$:
>		- Apply the **implicit symmetric QR step** with **Wilkinson shift**: $$D \leftarrow \text{diag}(I_{p}, Z, I_{q})^{T}\,D\,\text{diag}(I_{p}, Z, I_{q})$$
>			- where $$Z = G_{1}G_{2}\,{}\ldots{}\,G_{n-1}$$ is the *product of Givens rotations*.
>		- If $Q$ is desired, update $$Q \leftarrow Q\,\text{diag}(I_{p}, Z, I_{q})$$
>- *Return*: the symmetric Schur decomposition $$D = Q^{T}\,A\,Q$$ that overwrites $T$. 

>[!important]
>This algorithm requires about $$\frac{4n^3}{3}$$ flops if $Q$ is *not accumulated* and about $$9n^3$$ flops if $Q$ is *accumulated*.

- [[Algorithm Big-O Notations and Rate of Growth]]
- [[Algorithm RAM Model and Complexity Analysis]]


![[eigenvalue_symmetric.png]]


## Explanation

### Apply a Sequence of Givens Rotations to Symmetric Tridiagonal Matrix

>[!important] Definition
>The *left multiplication* a sequence of $n-1$  **Given rotation** on **tridiagonal matrix** can be computed in $O(n)$
>- For $k=1\,{,}\ldots{,}\,n-1$:
>	- $$[c,s] = \text{Givens}(T_{k,k}, T_{k+1,k})$$
>	- Define $m = \min\left\{ k+2,n \right\}$
>	- Left multiplication $$T_{\left\{ k:k+1 \right\}, \left\{ k:m \right\}} \leftarrow \left[ \begin{array}{cc}c & s \\ -s & c\end{array} \right]^{T}  T_{\left\{ k:k+1 \right\}, \left\{ k:m \right\}}$$

>[!important]
>Only $O(n)$ flops are required for transformation. 
>
>If $Q$ are accumulated, then we need $O(n^2)$ flops.






-----------
##  Recommended Notes and References


- [[Shift Strategy for Faster Symmetric QR Iterations]]
- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]

- [[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem]]
- [[QR Iteration for General Eigenvalue Problem]]

- [[Tridiagonal Decomposition of Symmetric Matrix]]
- [[Tridiagonal System of Equations]]
- [[Schur Triangularization and Schur Form]]

- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Hermitian or Symmetric Matrix]]


- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 458 - 464