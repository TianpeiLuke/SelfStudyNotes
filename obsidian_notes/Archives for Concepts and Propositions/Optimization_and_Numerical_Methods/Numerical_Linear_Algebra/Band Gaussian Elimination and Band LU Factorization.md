---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - banded_system_of_equations
  - system_of_linear_equations
  - band_lu_factorization
  - band_gaussian_elimination
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Band Gaussian Elimination and Band LU Factorization
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Band Gaussian Elimination and Band LU Factorization

![[LU Factorization of Matrix#^62518f]]

![[Gaussian Elimination for General Linear System#^057350]]

>[!important] Theorem
>Suppose $A\in M_{n}$ has a **LU factorization** $$A = LU.$$
>
>If $A$ has **upper bandwidth** $q$ and **lower bandwith** $p$, then $U$ has **upper bandwidth** $q$ and $L$ has **lower bandwith** $p$.

^4f120b

- [[LU Factorization of Matrix]]
- [[Gaussian Elimination for General Linear System]]

### Band Gaussian Elimination

>[!important] Definition
>Consider the problem of solving the *$LU$ factorization* $$A= L\,U$$ where $A \in M_{n}$ has *upper bandwidth* $q$ and *lower bandwidth* $p$, $L$ is an *unit lower triangular matrix* and $U$ is *upper triangular matrix*.
>
>The **band Gaussian elimination without pivoting** computes the *band LU factorization* as follows:
>- *Require*: $A\in \mathbb{R}^{n\times n}$ with *upper bandwidth* $q$ and *lower bandwidth* $p$
>- *Initialize*: $L = I$, and $U = A$
>- For $k=1\,{,}\ldots{,}\,n-1$:
>	- For $j=k+1\,{,}\ldots{,}\,\min\{k+p, n\}$: 
>		- **Update $L$**: compute the $(j,k)$ entry of $L$ $$L_{j,k} = \frac{U_{j,k}}{U_{k,k}}$$
>		- For $i=k+1\,{,}\ldots{,}\,\min\{k+q, n\}$:
>			- **Update** $U$: compute the $(j,i)$ entry of $U$ $$U_{j, i} \leftarrow U_{j, i} - L_{j,k}\,U_{k, i}.$$

^bb2266

>[!important]
>If $n \gg p$ and $n \gg q$, then this algorithm involves about $$2npq$$ flops. 

- [[Algorithm Big-O Notations and Rate of Growth]]
- [[Algorithm RAM Model and Complexity Analysis]]


## Explanation

>[!info]
>When $p = q = 1$, the corresponding system of equations is a [[Tridiagonal System of Equations]].
>
>Thus there exists a **LU factorization** of a **tridiagonal system** $$T = LU$$ where $L$ and $U$ are **lower** and **upper bidiagonal system**.
>
>From above, we see that the *LU factorization* has **linear time complexity** $2n.$

- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]




-----------
##  Recommended Notes and References


- [[LU Factorization of Matrix]]
- [[Banded System of Equations]]
- [[Band Triangular System of Equations]]
- [[Band Forward Substitution and Band Back Substitution]]

- [[Gaussian Elimination with Complete Pivoting]]
- [[Gaussian Elimination for General Linear System]]

\

- [[Matrix Computations by Golub]] pp 176 - 179
- [[Numerical Linear Algebra by Trefethen]] pp 147 - 171 
- [[Convex Optimization by Boyd]] pp 673