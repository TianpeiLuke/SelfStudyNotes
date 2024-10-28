---
tags:
  - concept
  - math/differential_geometry
keywords:
  - covariant_derivative
  - covariant_derivative_along_curve
  - coordinate_representation
topics:
  - differential_geometry
name: Coordinate Representation of Covariant Derivative Along a Curve
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Covariant Derivative Along a Curve

![[Coordinate Representation of Vector Field on Manifold#^b98f3e]]

![[Covariant Derivative Along a Curve#^3107a5]]

- [[Covariant Derivative Along a Curve]]

>[!important]
>Choose *smooth coordinates* $(x^i)$ for $\mathcal{M}$ in a neighborhood of $\gamma(t_0)$, and write the *coordinate representation* of *vector field along curve* $\gamma(t)$
>$$
> \begin{align*}
> V(t) &=  V^{i}(t) \frac{ \partial}{ \partial x^{i} }\Big|_{\gamma(t)}
> \end{align*}
>$$  
>for $t$ near $t_0$, where $V^1 \,{,}\ldots{,}\,V^n$ are *smooth real-valued functions* defined on some neighborhood of $t_0$ in $I$. 
>
>By the properties of $D_t$, since each $\partial / \partial x^i$ is *extendible*, the **coordinate representation** of **covariant derivative along curve** $\gamma(t)$ is given by
>$$
> \begin{align*}
> D_t(V_t) &= \dot{V}^i(t) \frac{ \partial}{ \partial x^{i} }\Big|_{\gamma(t)} + V^i(t)\, \nabla_{\gamma'(t)}\left(\frac{ \partial}{ \partial x^{i} }\Big|_{\gamma(t)}\right) \\[10pt]
> &= \left(\dot{V}^k(t)  + \dot{\gamma}^{i}(t)V^j(t)\,\Gamma_{i,j}^{k}(\gamma(t))\right)  \frac{ \partial}{ \partial x^{k} }\Big|_{\gamma(t)}
> \end{align*}
>$$ 
>where $\Gamma_{i,j}^{k}$ is the **connection coefficients** of $\nabla$ with respect to basis frames.
>- We use *Einstein summation convention.*

^bb4ecb

- [[Coordinate Representation of Vector Field on Manifold]]
- [[Affine Connection of Basis Frames and Connection Coefficient]]
- [[Einstein Summation Convention]]


## Explanation


![[Coordinate Representation of Connection#^8b43b3]]

## Geodesic Equations

- [[Coordinate Representation of Geodesic and Geodesic Equations]]



-----------
##  Recommended Notes and References




- [[Integral Curve of Vector Field]]
- [[Coordinate Representation of Connection]]

- [[Coordinate Chart]]