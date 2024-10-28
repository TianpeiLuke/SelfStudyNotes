---
tags:
  - concept
  - math/differential_geometry
keywords:
  - geodesic_curve
  - coordinate_representation
topics:
  - differential_geometry
name: Coordinate Representation of Geodesic Curve
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Geodesic Curve

![[Coordinate Representation of Covariant Derivative Along a Curve#^bb4ecb]]

![[Geodesic on Manifolds#^1d16a0]]

- [[Geodesic on Manifolds]]
- [[Coordinate Representation of Covariant Derivative Along a Curve]]

>[!important] Definition
>In terms of smooth coordinates $(x^i)$, if we write the *component functions* of $\gamma$ as $$x(t) = (x^1(t) \,{,}\ldots{,}\,x^n(t)).$$ 
>
>Since
>- the geodesic curve satisfies the equation $$D_t(x'(t)) = 0$$
>- using the coordinate representation of covariant derivative along a curve, 
>
>we have a *system of $k$ ordinary differential equations (ODEs)* called the **geodesic equations**:
>$$
> \begin{align}
> \frac{d^2}{dt^2}x^k(t)  +  \left(\frac{d}{dt}x^{i}(t)\right)\,\;\Gamma_{i,j}^{k}(x(t))\;\left(\frac{d}{dt}x^j(t)\right) = 0, \quad k=1,\ldots, n.
> \end{align} 
>$$ 
>or
>$$
> \begin{align}
> \ddot{x}^k(t)  +  \dot{x}^{i}(t)\,\dot{x}^j(t)\;\Gamma_{i,j}^{k}(x(t)) = 0, \quad k=1,\ldots, n.
> \end{align} 
>$$ 
>where 
>- $\Gamma_{i,j}^{k}$ is the *connection coefficient* for affine connection $\nabla$.
>- The *Einstein summation convention* is used.
>  
>A (parameterized) curve $\gamma$ is a **geodesic** *if and only if* its *component functions* satisfy the **geodesic equations**. 
>
>Note that this is a **system** of **second-order nonautonomous nonlinear ODEs**.
>- This system of equations is in general, insolveable.
>- If $\Gamma_{i,j}^{k}$ is **constant**, then this system of equations is a **linear second-order ODE**, which is solveable.

^63f205

- [[Ordinary Differential Equations]]
- [[Einstein Summation Convention]]
- [[Linear Ordinary Differential Equations with Constant Coefficients]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]


## Explanation





-----------
##  Recommended Notes and References


- [[Covariant Derivative Along a Curve]]
- [[Connection in Vector Bundle and Covariant Derivative]]
- [[Smooth Manifold]]
- [[Velocity of Smooth Curves]]
- [[Vector Field Along a Curve]]
- [[Parallel Transport of Tensor Field along Curve]]

- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Parameterized Curve on Manifold]]
- [[Space of all Smooth Vector Fields on a Manifold]]

- [[Coordinate Representation of Vector Field Parallel Along a Curve]]


- [[Exponential Map via Geodesic on Riemannian Manifold]]
- [[Gradient Flow on Smooth Manifold]]


- [[Introduction to Riemannian Manifolds by Lee]]
