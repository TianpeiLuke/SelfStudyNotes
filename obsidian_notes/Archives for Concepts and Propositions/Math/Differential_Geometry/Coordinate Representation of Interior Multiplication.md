---
tags:
  - concept
  - math/differential_geometry
keywords:
  - coordinate_representation
  - interior_multiplication
topics:
  - differential_geometry
name: Coordinate Representation of Interior Multiplication
date of note: 2024-07-10
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Interior Multiplication

![[Interior Multiplication#^2aa9cb]]

>[!important] Definition
>Let $X \in \mathfrak{X}(M)$ be a vector field on $M$. 
>$$X = X^i \frac{ \partial  }{ \partial x^i }.$$
>
>The **interior product** $X   \mathbin{\lrcorner } \left(dx^{1} \,{\wedge}\ldots{\wedge}\, dx^{k}\right)$ has the following representation:
>$$
> \begin{align}
>X \mathbin{\lrcorner } \left(dx^{1} \,{\wedge}\ldots{\wedge}\, dx^{k}\right) &= \sum_{i=1}^{k}(-1)^{i-1}dx^i(X) \,dx^{1} \,{\wedge}\ldots{\wedge}\, \widehat{dx^i} \,{\wedge}\ldots{\wedge}\,dx^{k} \nonumber \\
> &= \sum_{i=1}^{k}(-1)^{i-1}X^i\,dx^{1} \,{\wedge}\ldots{\wedge}\,\widehat{dx^i} \,{\wedge}\ldots{\wedge}\, dx^{k}
> \end{align}
>$$ 
> where $\widehat{dx^i}$ indicates that $dx^i$ is **omitted**.  
> 
> In general, if  $\omega^{i} \in \mathfrak{X}^{*}(M),\; i=1\,{,}\ldots{,}\,k$, and $X \in \mathfrak{X}(M)$, we have
>$$
> \begin{align}
>X \mathbin{\lrcorner } \left(\omega^{1} \,{\wedge}\ldots{\wedge}\, \omega^{k}\right) &= \sum_{i=1}^{k}(-1)^{i-1}\omega^i(X) \,\omega^{1} \,{\wedge}\ldots{\wedge}\, \widehat{\omega^i} \,{\wedge}\ldots{\wedge}\,\omega^{k} \nonumber
> \end{align}
>$$ 

- [[Interior Multiplication]]
- [[Vector Field on Manifold]]
- [[Differential k-Form on Manifold]]


## Explanation



## Laplace Expansion

>[!important] 
>For $\omega^{i} \in \mathfrak{X}^{*}(M),\; i=1\,{,}\ldots{,}\,n$, and $X_{j} \in \mathfrak{X}(M), \; j=1\,{,}\ldots{,}\,n$, define matrix $$A = \left[\omega^{i}\left(X_{j}\right)\right]_{i,j},$$ we have the 
>$$
>\begin{align*}
>\det A &= \left(\omega^{1} \,{\wedge}\ldots{\wedge}\,\omega^{n}\right)\left(X_{1} \,{,}\ldots{,}\,X_{n}\right)
>\end{align*}
>$$
>
>Since 
>$$
>\begin{align*}
>X_{1} \mathbin{\lrcorner } \left(\omega^{1} \,{\wedge}\ldots{\wedge}\,\omega^{n}\right) &= \sum_{i=1}^{k}(-1)^{i-1}\omega^i(X_{1}) \,\omega^{1} \,{\wedge}\ldots{\wedge}\, \widehat{\omega^{i}} \,{\wedge}\ldots{\wedge}\,\omega^{k}
>\end{align*}
>$$
>by definition
>$$
>\left(X_{1} \mathbin{\lrcorner } \left(\omega^{1} \,{\wedge}\ldots{\wedge}\,\omega^{n}\right)\right)\left(X_{2} \,{,}\ldots{,}\,X_{n}\right) = \left(\omega^{1} \,{\wedge}\ldots{\wedge}\,\omega^{n}\right)\left(X_{1} \,{,}\ldots{,}\,X_{n}\right)
>$$
>
>So by the **expansion of interior multiplication**, we can find 
>$$
>\begin{align*}
>\det A&=\left(\omega^{1} \,{\wedge}\ldots{\wedge}\,\omega^{n}\right)\left(X_{1} \,{,}\ldots{,}\,X_{n}\right)\\
>&= \sum_{i=1}^{k}(-1)^{i-1}\omega^i(X_{1}) \,\left(\omega^{1} \,{\wedge}\ldots{\wedge}\, \widehat{\omega^{i}} \,{\wedge}\ldots{\wedge}\,\omega^{k}\right) \left(X_{2} \,{,}\ldots{,}\,X_{n}\right) \\
>&= \sum_{i=1}^{k}(-1)^{i-1}\omega^i(X_{1}) \,\det A_{1}^{i}
>\end{align*}
>$$
>which is the **Laplace expansion theorem** for *minors along the first column.*


- [[Determinant of Linear Transformation]]
- [[Laplace Expansion Theorem]]
- [interior-product-proof-of-the-basic-fomula](https://math.stackexchange.com/questions/171277/interior-product-proof-of-the-basic-fomula)


-----------
##  Recommended Notes and References


- [[Interior Multiplication]]
- [[Exterior Derivatives of Differential Form]]
- [[Differential k-Form on Manifold]]
- [[Exterior Forms]]

- [[Tensor Field on Manifold]]
- [[Introduction to Riemannian Manifolds by Lee]] 