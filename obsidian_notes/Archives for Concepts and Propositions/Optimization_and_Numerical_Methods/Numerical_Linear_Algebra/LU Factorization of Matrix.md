---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
keywords:
  - lu_factorization
  - gaussian_elimination
topics:
  - numerical_linear_algebra
name: LU Factorization of Matrix
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: LU Factorization of Matrix

>[!important] Definition
>Let $A\in M_{n}$. 
>
>The **LU factorization** of $A$ is given by 
>$$
>A = L\,U
>$$
>where $L \in M_{n}$ is a *lower triangular matrix* and $U \in M_{n}$ is an *upper triangular matrix*.

- [[Gaussian Elimination for General Linear System]]

### Existence

>[!important] Lemma
>Let $A\in M_{n}$ and suppose that $$A = LU$$ is an **LU factorization**.
>
>For any block $2\times 2$ partition
>$$
>A = \left[ \begin{array}{cc}A_{11} & A_{12} \\[5pt] A_{21} & A_{22}\end{array} \right], \quad L =  \left[ \begin{array}{cc}L_{11} & 0 \\[5pt] L_{21} & L_{22}\end{array} \right], \quad U = \left[ \begin{array}{cc}U_{11} & U_{12} \\[5pt] 0 & U_{22}\end{array} \right]
>$$
>with $A_{11}, L_{11}, U_{11}\in M_{k}$, $k\le n$, we have $$A_{11} = L_{11}\,U_{11}.$$
>
>Consequently, each **leading principal submatrix** of $A$ has an **LU factorization** in which the **factors** are the *corresponding* **leading principal submatrices** of $L$ and $U$

- [[Partition of Matrix and Block Matrix]]
- [[Principal Submatrix]]

>[!info]
>This lemma implies that **LU factorization** has a **recursive structure.**

>[!important] Theorem (Row/Column Inclusion Property)
>Let $A\in M_{n}$.
>
>Then
>- $A$ has an **$LU$ factorization** $$A = LU$$ in which $L$ is **nonsingular** *if and only if* $A$ has **row inclusion property**:
>	- For each $i=1\,{,}\ldots{,}\,n-1$, $A[i+1, [1:i]]$ is a **linear combination** of rows of $A[1:i]$, $$A_{i+1, [1:i]} \in \text{span}\left\{ A_{1, [1:i]} \,{,}\ldots{,}\, A_{i, [1:i]}\right\}, \quad i=1\,{,}\ldots{,}\,n-1$$
>- $A$ has an **$LU$ factorization** in which $U$ is **nonsingular** *if and only if* $A$ has **column inclusion property**:
>	- For each $j=1\,{,}\ldots{,}\,n-1$, $A[[1:j], j+1]$ is a **linear combination** of columns of $A[1:j]$, $$A_{[1:j],j+1} \in \text{span}\left\{ A_{[1:j], 1} \,{,}\ldots{,}\, A_{[1:j],j}\right\}, \quad j=1\,{,}\ldots{,}\,n-1$$

>[!info]
>If all **leading principal matrices** $A[1:k, 1:k]$  are non-singular for $k=1\,{,}\ldots{,}\,r$ with $r=\text{rank}(A)$, then $A$ satisfies both **row inclusion property** and **column inclusion property.**

>[!important] Corollary
>Suppose that $A\in M_{n}$ has  $\text{rank}(A) = r$. 
>
>If all the **leading principal matrices** $A[1:k]$ is **nonsingular**, i.e. the *principal minor* is *nonzero* $$\det \left( A[1:k, 1:k] \right) \neq 0, \quad k=1\,{,}\ldots{,}\,r$$ then $A$ has a **$LU$ factorization**. Furthermore, either factor may be chosen to be **unit triangular**. 
>
>Both $L$ and $U$ are **nonsingular** *if and only if* $r=n$, 
>- that is, *if and only if* $A$ and all of its **leading principal submatrices** are **nonsingular.**

^301e76

- [[Principal Submatrix]]
- [[Minor and Principal Minor]]
- [[Triangular Matrix and Block Triangular Matrix]]

### LDU Factorization and Uniqueness

>[!important] Corollary (LDU Factorization and Uniqueness of LU Factorization)
>Let $A\in M_{n}$. 
>
>- Suppose that $A$ is **nonsingular**. Then $A$ has a **$LU$ factorization** $$A = LU$$ *if and only if* all of its **leading principal submatrices** are nonsingular $$\det \left( A[1:k, 1:k] \right) \neq 0, \quad k=1\,{,}\ldots{,}\,n$$
>
>- Suppose that $A[1:k, 1:k]$ are nonsingular for all $k=1\,{,}\ldots{,}\,n$. Then $$A = L\,D\,U$$ where $L$ is a **lower triangular matrix**, $U$ is an **upper triangular matrix**, $D = \text{diag}(d_{1}\,{,}\ldots{,}\,d_{n})$ is **diagonal** with $$\begin{align*}d_{1} &= a_{11}, \\[5pt]  d_{i} &= \frac{\det\left(A[1:i, 1:i]\right)}{\det \left( A[1:i-1, 1:i-1] \right)}, \quad i=2\,{,}\ldots{,}\,n\end{align*}$$ The factors $L, U, D$ are **uniquely determined.** 

^62518f

>[!important] Definition
>Let $A\in M_{n}$ with *nonsingular leading principal submatrices* $A[1:k]$.
>
>Then the **LDU factorization** of $A$ is given by 
>$$A = L\,D\,U$$ where $L$ is a **lower triangular matrix**, $U$ is an **upper triangular matrix**, $D = \text{diag}(d_{1}\,{,}\ldots{,}\,d_{n})$ is **diagonal** with $$\begin{align*}d_{1} &= a_{11}, \\[5pt]  d_{i} &= \frac{\det\left(A[1:i, 1:i]\right)}{\det \left( A[1:i-1, 1:i-1] \right)}, \quad i=2\,{,}\ldots{,}\,n\end{align*}$$ which are the *ratios* of *successive principle minors*.

### PLU Factorization

![[PLU Factorization with Pivoting#^0aac00]]

- [[PLU Factorization with Pivoting]]


## Explanation

>[!quote]
>The **LU factorization** is a "high level" algebraic description of **Gaussian elimination**.
>
>-- [[Matrix Computations by Golub]] pp 111

- [[Gaussian Elimination for General Linear System]]


>[!info]
>Without the condition on **nonsingular leading principal submatrices**  $$\det \left( A[1:k, 1:k] \right) \neq 0, \quad k=1\,{,}\ldots{,}\,n,$$ there is **no guarantee** that the *LU factorization* **exist** or to be **unique**.

>[!info]
>Given the $LU$ factorization, we can decompose the system of equations $$Ax = b \iff LUx = b$$ into **two systems**:
>- $$Ly = b$$ which can be solved by **forward substitution** with $O(n^2)$ complexity
>- $$Ux = y$$ which can be solved by **back substitution** with $O(n^2)$ complexity
>

- [[Forward Substitution of Lower Triangular System]]
- [[Back Substitution of Upper Triangular System]]

- [[Algorithm Big-O Notations and Rate of Growth]]
- [[Algorithm RAM Model and Complexity Analysis]]


## LU Factorization via Gaussian Elimination

![[Gaussian Elimination for General Linear System#^057350]]

- [[Gaussian Elimination for General Linear System]]


## $LDL^{T}$ Factorization for Symmetric Matrix

>[!info]
>If $A = A^{T}$, then the **$LDU$ factorization** becomes **$LDL^{T}$ factorization** $$A = L\,D\,L^{T}$$ where the $U = L^{T}$ matrix in $LDU$ factorization.

- [[LDU Factorization of Symmetric Matrix]]

## Band LU Factorization

![[Band Gaussian Elimination and Band LU Factorization#^4f120b]]

- [[Band Gaussian Elimination and Band LU Factorization]]



-----------
##  Recommended Notes and References




- [[LDU Factorization of Symmetric Matrix]]

- [[System of Linear Equations or Linear System]]
- [[Sparse Linear System and Graph]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Matrix]]



- [[Numerical Linear Algebra by Trefethen]] pp 147 - 171 
- [[Matrix Computations by Golub]] pp 111
- [[Matrix Analysis by Horn]] pp 216 - 223
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 5 - 6
- [[Matrix CookBook by Petersen]] pp 32
- [[Convex Optimization by Boyd]] pp 668, 671