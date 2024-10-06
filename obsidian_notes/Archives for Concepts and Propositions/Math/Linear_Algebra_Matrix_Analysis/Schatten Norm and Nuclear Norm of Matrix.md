---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - matrix_analysis
  - schatten_norm
  - nuclear_norm
topics:
  - matrix_analysis
  - linear_algebra
name: Schatten Norm and Nuclear Norm of Matrix
date of note: 2024-09-13
---

## Concept Definition

>[!important]
>**Name**: Schatten Norm and Nuclear Norm of Matrix

![[Norm and Normed Space#^376595]]


>[!important] Definition
>Let $A \in \mathbb{R}^{m\times n}$. 
>
>Then the **Schatten $p$-Norms** are defined by
>$$
>\lVert A \rVert_{S, p} := \left(\sum_{k=1}^{r}\sigma_{k}^{p}\right)^{1 / p} = \lVert \sigma(A) \rVert_{p} 
>$$
>where 
>- $$\sigma(A) := (\sigma_{1} \,{,}\ldots{,}\,\sigma_{r})$$ are *singular values* of $A$, 
>- $r =\text{rank(A)}$ is the rank of $A$

^4f7716


>[!important] Definition
>Let $A \in \mathbb{R}^{m\times n}$. 
>
>The **trace norm** or **nuclear norm** is defined by the **Schatten $1$-Norms** 
>$$
>\lVert A \rVert_{*} := \lVert A \rVert_{S, 1} = \lVert \sigma(A) \rVert_{1} = \sum_{k=1}^{r}\lvert \sigma_{k} \rvert  
>$$
>
>If $A \in \mathbb{R}^{n\times n}$, then $$\lVert A \rVert_{*} = \text{tr}\left(\sqrt{ A^{*}A }\right).$$

^a510d6

- [[Trace of Matrix]]
- [[Positive Semidefinite Operator]]
- [[Trace Class Operator]]

>[!info]
>The nuclear norm is the **convex envelop** of the **rank function**

- [[Convex Function]]

## Explanation

>[!example]
>The **Frobenius norm** is the  **Schatten $2$-Norms** 
>$$
>\lVert A \rVert_{F} = \lVert A \rVert_{S, 2} = \lVert \sigma(A) \rVert_{2}   
>$$

- [[Frobenius Norm of Matrix]]

>[!example]
>The **$L_{2}$ norm** is the  **Schatten $\infty$-Norms** 
>$$
>\lVert A \rVert_{2} = \lVert A \rVert_{S, \infty} = \lVert \sigma(A) \rVert_{\infty} = \max_{k}\sigma_{k}(A)    
>$$

^9b897c

- [[Operator p-Norm of Matrix]]


## Trace-Class

![[Trace Class Operator#^051e95]]

- [[Trace Class Operator]]



-----------
##  Recommended Notes and References


- [[Frobenius Norm of Matrix]]
- [[Operator p-Norm of Matrix]]
- [[Operator Mixed pq Norm of Matrix]]


- [[Bounded Linear Operator and Norm of Operator]]
- [[Norm and Normed Space]]
- [[Norm Topology]]


- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Analysis of Function of Transform]]
- [[Spectral Theorem in Functional Calculus Form]]
- Wikipedia [Matrix_norm](https://en.wikipedia.org/wiki/Matrix_norm)
- [[Convex Function]]

- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 59 - 61
- [[Matrix CookBook by Petersen]] pp 61
- [[Convex Optimization by Boyd]] pp 72, 93, 194, 634 - 637, 