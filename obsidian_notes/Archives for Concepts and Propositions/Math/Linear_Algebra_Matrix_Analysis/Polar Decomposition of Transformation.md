---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - polar_decomposition_operator
  - polar_decomposition_matrix
topics:
  - matrix_analysis
  - linear_algebra
name: Polar Decomposition of Transformation
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Polar Decomposition of Transformation

>[!important] Theorem (Polar Decomposition)
>Let $A\in M_{n,m}$.
>
>- If $n < m$, then $$A = PU$$ where $P\in M_{n}$ is **positive semidefinite**, and $U$ has **orthonormal rows** i.e. $UU^{*} = I_{n}$.
>	- The factor $$P = (AA^{*})^{1 / 2}$$ is **uniquely** determined; which is a **polynomial** in $AA^{*}$
>	- The factor $U$ is determined if $A$ has **full row rank** $\text{rank}(A) = n$
>- If $n > m$, then $$A = UQ$$ where  $Q\in M_{m}$ is **positive semidefinite**, and $U\in M_{n,m}$ has **orthonormal columns**.
>	- The factor $$Q = (A^{*}A)^{1 / 2}$$ is **uniquely** determined; which is a **polynomial** in $A^{*}A$
>	- The factor $U$ is determined if $A$ has **full column rank** $\text{rank}(A) = m$
>- If $n = m$, then $$A = PU = UQ$$ where $P, Q\in M_{n}$ are **positive semidefinite**, and $U$ is **unitary**. 
>	- The factors $$P = (AA^{*})^{1 / 2}, \quad Q = (A^{*}A)^{1 / 2}$$ are both **uniquely** determined;  $P$  is a **polynomial** in $AA^{*}$ and  $Q$ is a **polynomial** in $A^{*}A$
>	- The factor $U$ is **unquely determined** if $A$ is **invertible** i.e. $A \in \text{GL}(n)$
>- If $A$ is real, then all factors may be taken to be real.

^636e45

- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Unitary and Orthogonal Transformation]]
- [[Isometry and Isometric isomorphism]]
- [[Positive Semidefinite Transformation]]
- [[Rank and Nullity of Linear Map]]
- [[Square Root of Positive Semidefinite Transformation and Absolute Value]]
- [[Matrix Polynomial]]


## Explanation

>[!info]
>The **polar decomposition** is a generalization of the polar form of complex value $$z = re^{i\theta}$$

>[!important]
>Note that any *symmetric positive definite matrix* $P$ can be uniquely represented by a **matrix exponential** $$P = e^{X}$$ for some symmetric $X$.
>
>Thus the **polar decomposition** for $A\in \text{GL}(n)$ can be written as $$A = Ue^{X} = e^{Z}U$$

- [[Matrix Exponential]]

### Special Subgroup

>[!important] Proposition
>- For any matrix in **special linear group** $A\in \text{SL}(n; \mathbb{C})$ i.e. $\det(A) = 1$, $$A = Ue^{X}$$ where $X\in \text{SU}(n)$ is from **special unitary group** and $X$ is **self-adjoint** with **zero trace** $$\text{tr}(X) = 0$$
>- For any matrix in **special linear group** $A\in \text{SL}(n; \mathbb{R})$ i.e. $\det(A) = 1$, $$A = Ue^{X}$$ where $X\in \text{SO}(n)$ is from **special orthogonal group** and $X$ is **real symmetric** with **zero trace** $$\text{tr}(X) = 0$$


- [[Special Linear Group]]
- [[Special Orthogonal Group and Special Unitary Group]]
- [[Trace of Matrix]]


## Normal Transformation

- [[Normal Transformation]]



## Hilbert Space

![[Polar Decomposition of Bounded Operator#^7e985f]]

- [[Polar Decomposition of Bounded Operator]]

## Singular Value Decomposition

- [[Singular Value Decomposition of Linear Map]]


-----------
##  Recommended Notes and References



- [[Positive Semidefinite Transformation]]

- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


- [[Vector Space over a Field]]
- [[Inner Product Space]]

- [[Finite Dimensional Vector Spaces by Halmos]] pp 169 - 171
- [[Matrix Analysis by Horn]] pp 449 - 453, 456
- [[Matrix Computations by Golub]] pp 540
- [[Numerical Linear Algebra by Trefethen]] pp 331
- [[Lie Groups Lie Algebra and Representations by Hall]] pp 42 - 46