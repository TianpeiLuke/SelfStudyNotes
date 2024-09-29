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

### Modified Gram-Schmidt Algorithm

- [[Modified Gram-Schmidt Algorithm for QR Factorization]]


## Explanation

>[!important]
>The **Gram–Schmidt process** may be applied to **any finite list of vectors**, *independent or not*.
>- If $x_{1} \,{,}\ldots{,}\,x_{n}$ are **linearly dependent**, the Gram–Schmidt process produces a vector $r_{k} = 0$ for the least value of $k$ for which $x_{k}$ is a *linear combination* of $x_{1} \,{,}\ldots{,}\,x_{k-1}.$

>[!important] 
>If the vectors $x_{1} \,{,}\ldots{,}\,x_{k}$ are **orthonormal** and the vectors $$x_{1} \,{,}\ldots{,}\,x_{k}, x_{k+1} \,{,}\ldots{,}\,x_{n}$$ are *linearly independent*, applying the **Gram–Schmidt process** to the latter list produces the list $$x_{1} \,{,}\ldots{,}\,x_{k}, z_{k+1} \,{,}\ldots{,}\,z_{n}$$ of orthonormal vectors.



## Complete Orthonormal Basis in Hilbert Space

- [[Complete Orthonormal Basis of Hilbert Space]]

## QR Factorization

>[!info]
>The Gram-Schmidt process is essentially the **$QR$ factorization** where
>- $$Q= [z_{1} \,{,}\ldots{,}\,z_{n}]$$
>- $$R = [\left\langle  z_{i}\,,\,x_{j}    \right\rangle],\quad j=i\,{,}\ldots{,}\,n$$

>[!important] Definition
>Consider the **QR factorization** of full column rank $A\in \mathbb{R}^{m\times n}$ with $\text{rank}(A) = n$, $$A = Q_{1}R_{1}$$ where $Q_{1}\in \mathbb{R}^{m\times n}$ with *orthornormal columns*, and $R\in \mathbb{R}^{n\times n}$ is an *upper triangular matrix.*
>
>The **classical Gram-Schmidt (CGS) algorithm** is described as follows:
>- *Require*: $A\in \mathbb{R}^{m\times n}$ with $\text{rank}(A) = n$
>- Compute the **1st diagonal term** of $R$ $$R_{1,1} = \lVert A_{:,1} \rVert_{2}$$
>- Find *first column* of $Q$ by **normalizing** first column of $A$ $$Q_{:,1} = \frac{A_{:,1}}{R_{1,1}}$$
>- For $k=2\,{,}\ldots{,}\,n$:
>	- Compute $R$ as the *projection* of columns of $A$ onto the *basis columns* of $Q$ $$R_{\{ 1:k-1 \},k} = Q_{\{ 1:m \}, \{ 1: k-1 \}}^{T}\,A_{\{ 1:m \}, k}$$
>	- Compute the **residual** $$r_{k} :=  A_{\{ 1:m \}, k} - Q_{\{ 1:m \}, \{ 1:k-1 \}}\,R_{\{ 1:k-1 \},k}$$
>	- Compute $k$-th **diagonal term** of $R$ as the norm of residual $$R_{k,k} = \lVert z \rVert_{2}$$
>	- Find *$k$-th column* of $Q$ by **normalizing** the residual   $$Q_{\{ 1:m \},k} = \frac{z}{R_{k,k}}$$
>- *Return*: 
>	- the upper triangular matrix $$R_{1} = [R_{k,\{ k:n \}}^{(n)}]$$
>	- the matrix $Q_{1}$ with orthornormal columns. 

^4a4caa

- [[Modified Gram-Schmidt Algorithm for QR Factorization]]
- [[QR Factorization of Matrix]]


## Least Square Estimation via Gram-Schmidt Orthogonalization

- [[Least Square Estimation with QR Factorization]]



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

