---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - l1_norm_matrix
  - l2_norm_matrix
  - lp_norm_matrix
topics:
  - matrix_analysis
  - linear_algebra
name: Operator p-Norm of Matrix
date of note: 2024-09-13
---

## Concept Definition


>[!important]
>**Name**: Operator $p$-Norm of Matrix

![[Norm and Normed Space#^376595]]

![[Bounded Linear Operator and Norm of Operator#^52c1c9]]

![[Operator Mixed pq Norm of Matrix#^0d8b17]]

- [[Operator Mixed pq Norm of Matrix]]

### Matrix $1$-Norm

>[!important] Definition
>Let $A \in \mathbb{R}^{m\times n}$. 
>
>Then the **matrix 1-norm** is defined as 
>$$
>\lVert A \rVert_{1} := \max_{j\in [n]}\left(\sum_{i=1}^{m}\lvert a_{i,j} \rvert \right)
>$$
>$L_{1}$ norm is also called the **"maximum column sum" norm**

^be3a94

### Matrix $p$-Norm


>[!important] Definition
>Let $A \in \mathbb{R}^{m\times n}$. 
>
>Then the **matrix $p$-norm** for $p \ge 1$ is defined as 
>$$
>\lVert A \rVert_{p} := \max_{\lVert x \rVert_{p} \neq 0 } \frac{\lVert A x \rVert_{p} }{\lVert x \rVert_{p} } := \max_{\lVert x \rVert_{p} = 1 } \lVert Ax \rVert_{p} 
>$$
>This is an **operator norm** _subordinate to_ (or **induced by**) two vector norms $\lVert  \rVert_{p}.$

^c830b5

### Matrix $\infty$-Norm

>[!important] Definition
>Let $A \in \mathbb{R}^{m\times n}$. 
>
>Then the **matrix $\infty$-norm**  is defined as 
>$$
>\lVert A \rVert_{\infty} := \max_{i\in [m]}\left(\sum_{j=1}^{n}\lvert a_{i,j} \rvert \right)
>$$
>$L_{\infty}$ norm is also called the **"maximum row sum" norm**

^866ef8


### Matrix $2$-Norm or Spectral Norm

>[!important] Definition
>Let $A \in \mathbb{R}^{m\times n}$. 
>
>Then the **matrix 2-norm** or **spectral norm** of $A$ is defined as 
>$$
>\lVert A \rVert_{2} := \max_{\lVert x \rVert_{2} \neq 0 } \frac{\lVert A x \rVert_{2} }{\lVert x \rVert_{2} } := \max_{\lVert x \rVert_{2} = 1 } \lVert Ax \rVert_{2}. 
>$$
>
>The **matrix 2-norm** of $A$ is equivalent to the *largest singular value* of $A$
>$$
>\lVert A \rVert_{2} = \sigma_{1}(A) = \sqrt{ \lambda_{\text{max}}\left(A^{T}\,A\right) }  = \sqrt{ \lambda_{\text{max}}\left(A\,A^{T}\right) } 
>$$

^542fc3

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Singular Value Decomposition of Linear Map]]


## Explanation

>[!info]
>The $L_{1}$ norm of matrix can be seen as special case of $L_{p,q}$ norm when $p = q =1$:
>$$
>\lVert A \rVert_{1} := \lVert A \rVert_{1, 1} := \max_{\lVert x \rVert_{1} \neq 0 } \frac{\lVert A x \rVert_{1} }{\lVert x \rVert_{1} } := \max_{\lVert x \rVert_{1} = 1 } \lVert Ax \rVert_{1} 
>$$

>[!info]
>$L_{p}$ norm is also called the **operator $p$-norm**, or **subordinate norm**.

- [[Bounded Linear Operator and Norm of Operator]]

## Schatten Norm

![[Schatten Norm and Nuclear Norm of Matrix#^4f7716]]

![[Schatten Norm and Nuclear Norm of Matrix#^9b897c]]

- [[Schatten Norm and Nuclear Norm of Matrix]]


-----------
##  Recommended Notes and References

- [[Operator Mixed pq Norm of Matrix]]
- [[Schatten Norm and Nuclear Norm of Matrix]]
- [[Frobenius Norm of Matrix]]


- [[Bounded Linear Operator and Norm of Operator]]
- [[Norm and Normed Space]]
- [[Norm Topology]]
- [[Matrix]]


- [[Lp Space]]
- [[Spectral Theorem in Functional Calculus Form]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- Wikipedia [Matrix_norm](https://en.wikipedia.org/wiki/Matrix_norm)
- [[Convex Function]]


- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 59 - 61