---
tags:
  - concept
  - math/differential_geometry
keywords:
  - christoffel_symbols
topics:
  - differential_geometry
name: Christoffel Symbols
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Christoffel Symbols

![[Affine Connection of Basis Frames and Connection Coefficient#^f02c91]]

- [[Affine Connection of Basis Frames and Connection Coefficient]]




- [[Metric Connection for Riemannian Manifold]]



## Explanation


>[!info]
>The smooth function $$\Gamma_{i,j}^{k} \in \mathcal{C}^{\infty}(M)$$ has **three indices**: 
>- **two lower indices** $(i,j)$ corresponds to 
>	- the index of *component* $X^i$ for the **directional vector field** $X$, and 
>	- the index of *component* $Y^j$ for the **differentiated vector field** $Y$ in $\nabla_{X}Y$;
>- the **one upper index** $k$ corresponds to 
>	- the index of the **basis vector field** $\partial/ \partial x^k$ which spans the space of vector fields. 

## Properties

>[!important] Proposition (Change of Basis)
>Let $M$ be a smooth manifold with or without boundary, and let $\nabla$ be a *connection* in $TM$. 
>
>Suppose we are given **two smooth local frames** $(E_i)$ and $(\widetilde{E}_j)$ for $TM$ on an open subset $U \subseteq M$, related by $\widetilde{E}_i = A_i^j E_j$ for some matrix of functions $(A_i^j)$. 
>
>Let $\Gamma_{i,j}^{k}$ and $\widetilde{\Gamma}_{i,j}^{k}$ denote the **connection coefficients** of $\nabla$ with respect to these two frames.
>
> Then
> $$
> \begin{align}
> \widetilde{\Gamma}_{i,j}^{k} &= (A^{-1})_{t}^{k}A_{i}^{r}A_{j}^{s}\Gamma_{r,s}^{t}+ (A^{-1})_{t}^{k}A_{i}^{s}E_{s}(A_{j}^{t})  
> \end{align}
>$$ 




-----------
##  Recommended Notes and References

- [[Connection in Vector Bundle]]
- [[Affine Connection on Tangent Bundle]]


- [[Introduction to Riemannian Manifolds by Lee]]