---
tags:
  - concept
  - math/differential_geometry
keywords:
  - connection
  - coordinate_representation
topics:
  - differential_geometry
name: Coordinate Representation of Connection
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Connection

>[!important] Proposition
>Let $M$ be a smooth manifold with or without boundary, and let $\nabla$ be a connection in $TM$. 
>
>Suppose $(E_i)$ is a *smooth local frame* over an open subset $U\subseteq M$, and let $\set{\Gamma_{i,j}^{k}}$ be the **connection coefficients** of $\nabla$ with respect to this frame. 
>
>For smooth vector fields $X, Y  \in \mathfrak{X}(M)$, written in terms of the frame as 
>$$X = X^i\,E_i, \qquad Y = Y^j\,E_j,$$
>one has
>$$
> \begin{align}
> \nabla_{X}Y &= \left( X(Y^k) + X^i\,Y^j \Gamma_{i,j}^{k} \right)\,E_k.
> \end{align}
>$$ 

- [[Affine Connection of Basis Frames and Connection Coefficient]]
- [[Einstein Summation Convention]]
## Explanation

>[!info]
>The smooth function $$\Gamma_{i,j}^{k} \in \mathcal{C}^{\infty}(M)$$ has **three indices**: 
>- **two lower indices** $(i,j)$ corresponds to 
>	- the index of *component* $X^i$ for the **directional vector field** $X$, and 
>	- the index of *component* $Y^j$ for the **differentiated vector field** $Y$ in $\nabla_{X}Y$;
>- the **one upper index** $k$ corresponds to 
>	- the index of the **basis vector field** $\partial/ \partial x^k$ which spans the space of vector fields. 


>[!important]
>Compare these two coordinate representation:
>$$
> \begin{align*}
> \nabla_{X}Y &= \left(X(Y^k) + X^i\,Y^j \Gamma_{i,j}^{k}\right)\,E_k &&\text{for }X, Y \in \mathfrak{X}(M)\\
> \overline{\nabla}_{X}{Y} &=X(Y^k) \,E_k  &&\text{for }X, Y \in \Gamma(T\mathbb{R}^{n}).
> \end{align*}
>$$  
>
>- The connection coefficients $\{\Gamma_{i,j}^{k}\}$ account for an **additional  "_rotation_" of basis vector** when moving $Y$ from *one tangent space* to another *along the direction* of $X$. 
>- For Euclidean space, the **basis is fixed** when *moving* **along the tangent direction** (i.e. **no rotation** just *translation*).




-----------
##  Recommended Notes and References

- [[Affine Connection on Tangent Bundle]]
- [[Affine Connection of Basis Frames and Connection Coefficient]]


