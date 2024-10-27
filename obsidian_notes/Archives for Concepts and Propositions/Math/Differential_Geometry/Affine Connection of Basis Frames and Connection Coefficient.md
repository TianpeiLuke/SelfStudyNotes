---
tags:
  - concept
  - math/differential_geometry
keywords:
  - affine_connection
  - basis_vector_space
topics:
  - differential_geometry
name: Affine Connection of Basis Frames
date of note: 2024-05-21
---

## Concept Definition

>[!important]
>**Name**: Affine Connection of Basis Frames

>[!info] 
>For computations, we need to examine how a connection appears in terms of **a local frame.** 


>[!important] Definition
>Let $(E_i)$ be a *smooth local frame* for $TM$ on an *open subset* $U\subseteq M$. 
>
>For every choice of the indices $i$ and $j$, we can expand the vector field $\nabla_{E_i}E_j$ in terms of this same frame:
>$$
> \begin{align}
> \nabla_{E_i}E_j &= \Gamma_{i,j}^{k}\,E_k. 
> \end{align}
>$$  
>
>As $i$, $j$, and $k$ range from $1$ to $n = \text{dim }M$, this defines **$n^3$ smooth functions** $$\Gamma_{i,j}^{k}: U \rightarrow \mathbb{R},$$ called **the connection coefficients** of $\nabla$ *with respect to the given frame*. 

^f02c91

- [[Christoffel Symbols]]
- [[Einstein Summation Convention]]

>[!important]
>The $n^3$ functions $$\{\Gamma_{i,j}^{k}\}$$ are called **the Christoffel symbols** under **the metric connections**.

- [[Metric Connection for Riemannian Manifold]]


## Explanation


>[!info]
>The smooth function $$\Gamma_{i,j}^{k} \in \mathcal{C}^{\infty}(M)$$ has **three indices**: 
>- **two lower indices** $(i,j)$ corresponds to 
>	- the index of *component* $X^i$ for the **directional vector field** $X$, and 
>	- the index of *component* $Y^j$ for the **differentiated vector field** $Y$ in $\nabla_{X}Y$;
>- the **one upper index** $k$ corresponds to 
>	- the index of the **basis vector field** $\partial/ \partial x^k$ which spans the space of vector fields. 





-----------
##  Recommended Notes and References

- [[Affine Connection on Tangent Bundle]]
- [[Christoffel Symbols]]
- [[Einstein Summation Convention

- [[Introduction to Riemannian Manifolds by Lee]]