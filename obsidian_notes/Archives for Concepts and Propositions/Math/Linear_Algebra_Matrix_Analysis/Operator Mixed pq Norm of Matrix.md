---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - l_pq_norm_matrx
topics:
  - matrix_analysis
  - linear_algebra
name: Lpq Norm of Matrix
date of note: 2024-09-13
---

## Concept Definition

>[!important]
>**Name**: $L_{p,q}$ Norm of Matrix

![[Norm and Normed Space#^376595]]

![[Bounded Linear Operator and Norm of Operator#^52c1c9]]

>[!important] Definition
>Let $A \in \mathbb{R}^{m\times n}$. 
>
>Then the **$L_{p,q}$ norm of matrix** is defined as 
>$$
>\lVert A \rVert_{p, q} := \max_{\lVert x \rVert_{q} \neq 0 } \frac{\lVert A x \rVert_{p} }{\lVert x \rVert_{q} } := \max_{\lVert x \rVert_{q} = 1 } \lVert Ax \rVert_{p} 
>$$

^0d8b17

### $L_{p}$ norm 

![[Operator p-Norm of Matrix#^c830b5]]

![[Operator p-Norm of Matrix#^be3a94]]

![[Operator p-Norm of Matrix#^866ef8]]

![[Operator p-Norm of Matrix#^542fc3]]

- [[Operator p-Norm of Matrix]]


## Explanation

>[!info]
>$L_{p,q}$ norm is also called the **$p,q$ operator norm**.



-----------
##  Recommended Notes and References


- [[Operator p-Norm of Matrix]]
- [[Frobenius Norm of Matrix]]
- [[Matrix]]

- [[Bounded Linear Operator and Norm of Operator]]
- [[Norm and Normed Space]]
- [[Norm Topology]]
- [[Convex Function]]


- [[Lp Space]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- Wikipedia [Matrix_norm](https://en.wikipedia.org/wiki/Matrix_norm)


- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 59 - 61