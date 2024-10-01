---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - band_cholesky_factorization
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Band Cholesky Factorization of Hermitian Positive Definite Matrices
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Band Cholesky Factorization of Hermitian Positive Definite Matrices

![[Band Gaussian Elimination and Band LU Factorization#^4f120b]]

![[Cholesky Factorization of Hermitian Positive Definite Matrices#^c9a9c1]]

>[!important] Proposition
>Let $A\in M_{n}$ be **Hermitian** and **positive definite** with bandwidth $p$.
>
>Then there exists a **lower triangular matrix** $G \in M_{n}$ with **positive** *diagonal entries* and lower bandwidth $p$ such that $$A = G\,G^{*}.$$

- [[Band Gaussian Elimination and Band LU Factorization]]
- [[Banded System of Equations]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]

### Algorithm

![[Cholesky Factorization of Hermitian Positive Definite Matrices#^770789]]

>[!important] Definition
>The **band Cholesky factorization** algorithm (with inplace update) is described as below:
>- *Require*: **symmetric positive definite matrix** $A \succ 0$ with **bandwidth** $p$
>- For $j=1\,{,}\ldots{,}\,n$:
>	- For $k=\max\left\{1, j-p \right\}\,{,}\ldots{,}\,j-1$:
>		- $\rho = \min\left\{ k+p, n \right\}$
>		- Update columns of lower triangular part of $A$ in place $$A_{\left\{ j:\lambda \right\}, j} \leftarrow A_{\left\{ j:\lambda \right\}, j} - A_{j,k}\,A_{\{j:\lambda\},k}$$
>	- $\lambda = \min\left\{ j+p, n \right\}$
>	- Adjust columns of lower triangular part of $A$  $$A_{\{j: \lambda\},j} = \frac{A_{\left\{ j: \lambda \right\}, j}}{\sqrt{A_{j,j}}} $$
>- *Return* the **Cholesky factor** as a *banded lower triangular matrix*  of $A$.

>[!important]
>If $n \gg  p$, then this algorithm requires about $$n\,\left( p^2  + 3p\right)$$ flops and $$n$$ square roots.
>
>- We just need to store the **nonzero lower triangular part** of $A$, which of the size $(p+1)\times n$.
>- Combined with band triangular system solver, we need $$np^2 + 7\,np + 2n$$ flops to solve $Ax= b$.
>- For small $p$, the **square roots** would requires a significant portion of computation. 
>- If we use $LDL^{T}$, it woudl take $$np^2 + 8\,np + n$$ flops with *no additional square roots*.

- [[LDU Factorization of Symmetric Matrix]]



## Explanation





-----------
##  Recommended Notes and References


- [[Band Gaussian Elimination and Band LU Factorization]]
- [[Banded System of Equations]]

- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]
- [[Positive Semidefinite Transformation]]
- [[Hermitian or Symmetric Matrix]]


- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]
- [[Gaussian Elimination to solve Linear System]]
- [[LU Factorization of Matrix]]


- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
\

- [[Matrix Computations by Golub]] pp 180 
- [[Numerical Linear Algebra by Trefethen]] pp 