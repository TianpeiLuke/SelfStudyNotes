---
tags:
  - concept
  - math/differential_geometry
keywords:
  - parallel_transport
  - coordinate_representation
topics:
  - differential_geometry
name: Coordinate Representation of Vector Field Parallel Along a Curve
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Vector Field Parallel Along a Curve

![[Coordinate Representation of Covariant Derivative Along a Curve#^bb4ecb]]

- [[Coordinate Representation of Covariant Derivative Along a Curve]]

![[Parallel Transport of Tensor Field along Curve#^a259b7]]


>[!important]
>Given 
>- a smooth curve $\gamma$ with a local coordinate representation $$\gamma(t) = (\gamma^1(t) \,{,}\ldots{,}\, \gamma^n(t)),$$ 
>- and a vector field  $V$ along $\gamma$ $$\begin{align*}V(t) &=  V^{i}(t) \frac{ \partial}{ \partial x^{i} }\Big|_{\gamma(t)}\end{align*}$$  
>
>the formula for *covariant derivative along curve* shows that a vector field $V$ is **parallel along** $\gamma$ *if and only if* the coordinate functions in $V$ satisfies the following **system of ordinary differential equations**
>$$
> \begin{align}
>  \frac{d}{dt}V^k(t)  + \left[\dot{\gamma}^{i}(t)\,\Gamma_{i,j}^{k}(\gamma(t))\right]\;V^j(t) = 0, \quad k=1,\,{,}\ldots{,}\,n
> \end{align}
>$$  
>or
>$$
> \begin{align}
> \dot{V}^k(t)  + \dot{\gamma}^{i}(t)\;\Gamma_{i,j}^{k}(\gamma(t))\;V^j(t) = 0, \quad k=1,\,{,}\ldots{,}\,n
> \end{align}
>$$  
>where 
>- $\Gamma_{i,j}^{k}$ is *connection coefficients* for affine connection $\nabla$
>- Both $\gamma(t)$ and $\dot{\gamma}(t)$ are known, so $\Gamma_{i,j}^{k}(\gamma(t))$ is known.
>
>This is a **system** of **$k$ linear non-autonomous ordinary differential equations (ODEs)** with respect to $$(V^1(t) \,{,}\ldots{,}\, V^n(t)).$$
>- Compare to *geodesic equation*, this system of equations is simpler since the **curve $\gamma$ is known**.

- [[Ordinary Differential Equations]]
- [[Homogeneous Linear Differential Equations]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]


## Explanation


## Geodesic Equations

![[Coordinate Representation of Geodesic and Geodesic Equations#^63f205]]

- [[Coordinate Representation of Geodesic and Geodesic Equations]]





-----------
##  Recommended Notes and References


- [[Coordinate Representation of Vector Field on Manifold]]
- [[Vector Field Along a Curve]]
- [[Parallel Transport of Tensor Field along Curve]]

- [[Coordinate Representation of Connection]]
- [[Coordinate Chart]]
