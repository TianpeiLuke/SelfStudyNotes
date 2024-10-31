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

>[!important] Definition
>Let $(\mathcal{M}, g)$ be a Riemannian or pseudo-Riemannian manifold.
>
>The **Christoffel symbols of the second kind** are the *connection coefficients* of a *Levi-Civita connection* $\nabla$ with respect to a smooth local frame in $T\mathcal{M}$.
>
>That is, it is a set of $n^3$ smooth functions $\{\Gamma_{i,j}^{k}\}$ that satisfies the equation
>$$
>\nabla_{E_{i}}E_{j} = \Gamma_{i,j}^{k}E_{k}, \quad \forall i,j,k=1\,{,}\ldots{,}\,n
>$$
>where $\{ E_{i} \}$ are local frames in $T\mathcal{M}$ and $\nabla$ is the *Levi-Civita connection*.

- [[Metric Connection for Riemannian Manifold]]
- [[Levi Civita Connection and Riemannian Connection]]
- [[Einstein Summation Convention]]


>[!important] Definition
>Let $(\mathcal{M}, g)$ be a Riemannian or pseudo-Riemannian manifold.
>
>The **Christoffel symbols of the first kind**  is a set of $n^3$ smooth functions $\{\Gamma_{i,j,l}\}$ that satisfies the equation
>$$
>\Gamma_{i,j,l} = g_{k,l}\Gamma_{i,j}^{k}
>$$
>where $\{\Gamma_{i,j}^{k}\}$ is the *Christoffel symbols of the second kind* with respect to the *Levi-Civita connection*  $\nabla$.


## Explanation


>[!info]
>The smooth function $$\Gamma_{i,j}^{k} \in \mathcal{C}^{\infty}(M)$$ has **three indices**: 
>- **two lower indices** $(i,j)$ corresponds to 
>	- the index of *component* $X^i$ for the **directional vector field** $X$, and 
>	- the index of *component* $Y^j$ for the **differentiated vector field** $Y$ in $\nabla_{X}Y$;
>- the **one upper index** $k$ corresponds to 
>	- the index of the **basis vector field** $\partial/ \partial x^k$ which spans the space of vector fields. 

## Properties

- [[Affine Connection of Basis Frames and Connection Coefficient]]


## Coordinate Representation 

- [[Coordinate Representation of Levi-Civita Connection and Christoffel Symbols]]




-----------
##  Recommended Notes and References

- [[Connection in Vector Bundle and Covariant Derivative]]
- [[Affine Connection on Tangent Bundle]]


- [[Introduction to Riemannian Manifolds by Lee]] pp 124