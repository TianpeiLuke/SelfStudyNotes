---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - frobenius_norm_matrix
topics:
  - linear_algebra
  - matrix_analysis
name: Frobenius Norm of Matrix
date of note: 2024-09-13
---

## Concept Definition

>[!important]
>**Name**: Frobenius Norm of Matrix

![[Norm and Normed Space#^376595]]

![[Bounded Linear Operator and Norm of Operator#^52c1c9]]

>[!important] Definition
>Let $A \in \mathbb{R}^{m\times n}$. 
>
>Then the **Frobenius norm** or **matrix Euclidean norm** of $A$ is defined as 
>$$
>\lVert A \rVert_{F} := \left(\sum_{i=1}^{m}\sum_{j=1}^{n} a_{i,j}^2\right)^{1 / 2}
>$$

## Explanation

>[!important] Proposition
>The **Frobenius norm** or **matrix Euclidean norm** of $A$ is equivalent to
>$$
>\lVert A \rVert_{F} := \left(\sum_{k=1}^{r}\,\sigma_{k}^2(A)\right)^{1 / 2} = \left(\text{tr}\left(A^{*}\,A\right)\right)^{1 / 2} = \left(\text{tr}\left(A\,A^{*}\right)\right)^{1 / 2} 
>$$
>where 
>- $\{ \sigma_{k} \}$ are **singular values** of $A$, 
>- and $r = \text{rank(A)}$.

- [[Singular Value Decomposition of Linear Map]]


>[!info]
>The **Frobenius norm** is also called
>- **$\ell_{2}$-norm**
>- **Schur norm**
>- **Hilbert-Schmidt norm**
>- **Schatten 2-norm**

- [[Hilbert-Schmidt Operator]]

## Related Norms 

![[Operator p-Norm of Matrix#^542fc3]]

- [[Operator p-Norm of Matrix]]

![[Schatten Norm and Nuclear Norm of Matrix#^4f7716]]

![[Schatten Norm and Nuclear Norm of Matrix#^a510d6]]

- [[Schatten Norm and Nuclear Norm of Matrix]]





-----------
##  Recommended Notes and References


- [[Operator Mixed pq Norm of Matrix]]
- [[Schatten Norm and Nuclear Norm of Matrix]]
- [[Operator p-Norm of Matrix]]


- [[Hilbert-Schmidt Operator]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Norm and Normed Space]]
- [[Norm Topology]]
- [[Convex Function]]

- [[Lp Space]]
- [[Matrix]]
- Wikipedia [Matrix_norm](https://en.wikipedia.org/wiki/Matrix_norm)
- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 59 - 61
- [[Matrix Computations by Golub]] pp 71, 77 - 79