---
tags:
  - concept
  - math/differential_geometry
keywords:
  - geodesic_curve
  - covariant_derivative_along_curve
topics:
  - differential_geometry
name: Geodesic on Manifolds
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Geodesic on Manifolds

![[Covariant Derivative Along a Curve#^3107a5]]

>[!important] Definition
>Let $\mathcal{M}$ be a smooth manifold, endowed with a *connection* $\nabla$ on $T\mathcal{M}$.
>
>A *smooth curve* $\gamma$, $$\gamma: J \to \mathcal{M}$$ is called a **geodesic** *with respect to* $\nabla$ 
>- if its **acceleration** i.e. *covariant derivative* of *velocity field* $\gamma'(t)$ *along* $\gamma$  is *zero*: $$D_t(\gamma'(t)) = 0.$$ 

^1d16a0

- [[Covariant Derivative Along a Curve]]
- [[Affine Connection on Tangent Bundle]]

- [[Smooth Manifold]]
- [[Velocity of Smooth Curves]]
- [[Integral Curve of Vector Field]]



## Explanation

>[!important]
>There are *two alternatives* for the definition of **geodesics**:
>
>- *Geodesics* is the "**shortest**" path that connects two points on the surface; This definition is hard since the definition of manifold is abstract. 
>	- This definition requires the definition of **distance**, i.e. for **Riemannian manifold**
>- Geodesics is the curve on the surface that has **zero tangential acceleration**. 
>	- This is the motivation to introduce the concept of **connections**.

- [[Riemannian Metric and Riemannian Manifold]]


>[!info]
>The **geodesic curve** concerns on the *covariant derivative* of **velocity field** $\gamma'(t)$ along the **velocity direction** $\gamma'(t)$,
>$$
>\nabla_{\gamma'(t)}\,\gamma'(t)
>$$
>
>The geodesic definition states that the curve's **total acceleration** should be **orthogonal** to it **velocity** so that its **acceleration along velocity direction** is $0$. 
>- A *geodesic curve* is moving along the surface with **constant speed.**

![[geodesic_curve_fig.png]]


## Coordinate Representation

- [[Coordinate Representation of Geodesic and Geodesic Equations]]


-----------
##  Recommended Notes and References


- [[Connection in Vector Bundle and Covariant Derivative]]
- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Parameterized Curve on Manifold]]
- [[Space of all Smooth Vector Fields on a Manifold]]


- [[Exponential Map via Geodesic on Riemannian Manifold]]
- [[Gradient Flow on Smooth Manifold]]


- [[Introduction to Riemannian Manifolds by Lee]]