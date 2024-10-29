---
tags:
  - concept
  - math/differential_geometry
keywords:
  - covariant_derivative
topics:
  - differential_geometry
name: Covariant Derivative Along a Curve
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Covariant Derivative Along a Curve

![[Connection in Vector Bundle and Covariant Derivative#^94b423]]

>[!important] Theorem
>Let $\mathcal{M}$ be a *smooth manifold* with or without boundary and let $\nabla$ be a *connection* in $T\mathcal{M}$. 
>
>For each smooth curve $$\gamma: I \rightarrow \mathcal{M},$$ the *connection* determines a **unique operator**
>$$ 
> \begin{align*}
> D_t: \mathfrak{X}(\gamma) \rightarrow \mathfrak{X}(\gamma)
> \end{align*}
>$$  
>called the **covariant derivative along** $\gamma$, satisfying the following properties:
>- **Linearity** over $\mathbb{R}$: $$\begin{align*} D_t\left(a\,V + b\,W\right) &= a\,D_t(V) + b\,D_t(W), \quad \text{ for }a,b \in \mathbb{R}. \end{align*}$$
>- **Product Rule**: $$\begin{align*}D_t(f\,V) &= f'\,V + f D_t(V), \quad \text{ for }f \in \mathcal{C}^{\infty}(I).\end{align*}$$
>- If $V \in \mathfrak{X}(\gamma)$ is *extendible*, then for every **extension** $\widetilde{V}$ of $V$, $$\begin{align*}D_t(V(t)) &= \nabla_{\gamma'(t)}\widetilde{V}.\end{align*}$$
>
>There is an analogous *operator* on the **space of smooth tensor fields** of *any type* along $\gamma$.

^3107a5

- [[Affine Connection on Tangent Bundle]]
- [[Parameterized Curve on Manifold]]
- [[Smooth Manifold]]
- [[Velocity of Smooth Curves]]
- [[Vector Field on Manifold]]

![[extendible_vector_field.png]]


## Explanation

![[geo_curv.png]]

### Covariant Derivative as Normal Projection of Derivative

>[!info]
>Let $w$ be a *smooth vector field* in an open subset $U \subset \mathcal{S}$ and $p\in U$, i.e. $w(p) \in T_{p}S$.  Let $y\in T_{p}S$. 
>
>Consider a parameterized curve $\alpha: (-\epsilon, \epsilon) \rightarrow U$, with $\alpha(0) = p$ and $\dot{\alpha}(0) = y$, and let $w(t), t\in (-\epsilon, \epsilon)$, be the **restriction** of the *vector field to the curve* $\alpha$. 
>
>The vector obtained by the **normal projection** of $$\frac{d}{dt}w(0)$$ onto the *tangent plane* $T_{p}S$ is called the **covariant derivative** at $p$ of the *vector field* $w$ relative to the vector $y$. This *covariant derivative* is denoted by $$\frac{Dw}{dt}(0) \;\;\text{ or }\;\; D_{y}w.$$


![[cov_deriv.png]]

>[!info]
> The **covariant derivative** only depends on the **intrinsic geometry** of the **surface** and it does *not depend* on the *choice of the curve*. 


## Coordinate Representation

- [[Coordinate Representation of Covariant Derivative Along a Curve]]

## Geodesic and Parallel Transport

- [[Parallel Transport of Tensor Field along Curve]]
- [[Geodesic on Manifolds]]



-----------
##  Recommended Notes and References


- [[Connection in Vector Bundle and Covariant Derivative]]
- [[Vector Field Along a Curve]]
- [[Smooth Map between Euclidean Spaces]]
- [[Smooth Vector Field on Manifold]]
- [[Space of all Smooth Vector Fields on a Manifold]]
- [[Space of all Smooth Tensor Fields on a Manifold]]
- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Tangent Bundle]]
- [[Derivation of Smooth Map at point and Tangent Vector]]


- [[Introduction to Riemannian Manifolds by Lee]]