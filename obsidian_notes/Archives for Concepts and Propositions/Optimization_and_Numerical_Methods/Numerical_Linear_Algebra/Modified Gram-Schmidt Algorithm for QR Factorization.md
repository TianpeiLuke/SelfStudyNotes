---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - modified_gram_schmidt_orthogonalization
  - gram_schmidt_orthogonalization
topics:
  - numerical_linear_algebra
name: Modified Gram-Schmidt Algorithm for QR Factorization
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Modified Gram-Schmidt Algorithm for QR Factorization

![[Gram-Schmidt Orthogonalization#^4a4caa]]

- [[Gram-Schmidt Orthogonalization]]

>[!important] Definition
>Consider the **QR factorization** of full column rank $A\in \mathbb{R}^{m\times n}$ with $\text{rank}(A) = n$, $$A = Q_{1}R_{1}$$ where $Q_{1}\in \mathbb{R}^{m\times n}$ with *orthornormal columns*, and $R\in \mathbb{R}^{n\times n}$ is an *upper triangular matrix.*
>
>The **modified Gram-Schmidt (MGS) algorithm** is described as follows:
>- *Require*: $A\in \mathbb{R}^{m\times n}$ with $\text{rank}(A) = n$
>- For $k=1\,{,}\ldots{,}\,n$:
>	- Set diagonal term of upper triangular matrix be the *norm* of $k$-th column  of $A$ $$R_{k,k} = \lVert A_{\{ 1:m \}, k} \rVert $$
>	- Set $k$-th column of $Q$ $$Q_{\{ 1:m \}, k} = \frac{A_{\{ 1:m \},k}}{R_{k,k}}$$
>	- For $j=k+1\,{,}\ldots{,}\,n$:
>		- Compute $R$ as the *projection* of columns of $A$ onto the *basis columns* of $Q$ $$R_{k,j} = Q_{\{ 1:m \}, k}^{T}\,A_{\{ 1:m \}, j}$$
>		- Overwrite the $j$-th column of $A$ by the **residual** $$A_{\{ 1:m \}, j} \leftarrow A_{\{ 1:m \}, j} - Q_{\{ 1:m \}, k}\,R_{k,j}$$
>- *Return*: 
>	- the upper triangular matrix $$R_{1} = [R_{k,\{ k:n \}}^{(n)}]$$
>	- the matrix $Q_{1}$ as the result of overwritten $A$ $$Q_{1} := A^{(n)}$$ 

- [[QR Factorization of Matrix]]
- [[Surjective Injective Invertible Linear Map and Rank]]

>[!important]
>The **modified Gram-Schmidt (MGS) algorithm** requires only $$2mn^2$$ flops.
>- Compared to **Householder QR** which requires $$2mn^2 - \frac{2n^3}{3}$$ with additional $$2mn^2 - \frac{2n^3}{3}$$ to reconstruct $Q$ for *back accumulation*
>- **MGS** requires only **half** as many as operations as compared to *Householder QR*

- [[Householder QR Factorization]]

## Explanation





-----------
##  Recommended Notes and References


- [[Gram-Schmidt Orthogonalization]]
- [[QR Factorization of Matrix]]

- [[Unitary and Orthogonal Transformation]]
- [[Triangular Matrix and Block Triangular Matrix]]

- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Inner Product Space]]
- [[Matrix]]



- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 254 - 255