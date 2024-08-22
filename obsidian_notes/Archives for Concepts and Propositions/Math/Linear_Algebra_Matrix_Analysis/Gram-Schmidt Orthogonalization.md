---
tags:
  - concept
  - math/functional_analysis
  - math/probability
  - math/stochastic_process
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - gram_schmidt_orthogonalization
  - orthogonality
topics:
  - linear_algebra
  - matrix_analysis
  - functional_analysis
name: Gram-Schmidt Orthogonalization
date of note: 2024-06-05
---

## Concept Definition

>[!important]
>**Name**: Gram-Schmidt Orthogonalization

>[!important] Definition
>Let $V$ be an *inner product* space.
>
>The **Gram–Schmidt orthogonalization process** is described as follow
>- *Require*: a list of *linearly independent* vectors $\left\{ x_{1} \,{,}\ldots{,}\,x_{n} \right\}$
>- *Initlalize* $r_{1} = x_{1}$
>- Normalize $$z_{1} = \frac{r_{1}}{\lVert r_{1} \rVert_{2} }$$
>- For $k=2 \,{,}\ldots{,}\,n$:
>	- Collect all previous *orthonormal vectors* $(z_{1} \,{,}\ldots{,}\,z_{k-1})$
>	- Compute the **residual** $$r_{k} = x_{k} - \sum_{i=1}^{k-1} \left\langle x_{k} , z_{i} \right\rangle\,z_{i}$$
>		- Note that the residual is **orthogonal to** all previous *orthonormal vectors*  $$\left\langle r_{k} , z_{i} \right\rangle = 0, \quad i=1 \,{,}\ldots{,}\,k-1$$
>	- **Normalize** the residual as new vector $$z_{k} = \frac{r_{k}}{\lVert r_{k} \rVert_{2} }$$
>- *Result*: a list of **orthonormal vectors** $\left\{ z_{1} \,{,}\ldots{,}\,  z_{n}\right\}$

^4fc278


- [[Linear Independence]]
- [[Orthogonality in Inner Product Space]]
- [[Inner Product Space]]

## Explanation

>[!important]
>The **Gram–Schmidt process** may be applied to **any finite list of vectors**, *independent or not*.
>- If $x_{1} \,{,}\ldots{,}\,x_{n}$ are **linearly dependent**, the Gram–Schmidt process produces a vector $r_{k} = 0$ for the least value of $k$ for which $x_{k}$ is a *linear combination* of $x_{1} \,{,}\ldots{,}\,x_{k-1}.$

>[!important] 
>If the vectors $x_{1} \,{,}\ldots{,}\,x_{k}$ are **orthonormal** and the vectors $$x_{1} \,{,}\ldots{,}\,x_{k}, x_{k+1} \,{,}\ldots{,}\,x_{n}$$ are *linearly independent*, applying the **Gram–Schmidt process** to the latter list produces the list $$x_{1} \,{,}\ldots{,}\,x_{k}, z_{k+1} \,{,}\ldots{,}\,z_{n}$$ of orthonormal vectors.



## Complete Orthonormal Basis in Hilbert Space

- [[Complete Orthonormal Basis of Hilbert Space]]



-----------
##  Recommended Notes and References


- [[Orthogonality in Inner Product Space]]
- [[Hilbert Space]]
- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Inner Product Space]]

- [[QR Factorization of Matrix]]

- [[Least Square Estimation with QR Factorization]]


- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Matrix Computations by Golub]]  pp 254 - 256
- [[Matrix Analysis by Horn]] pp 15 - 16

