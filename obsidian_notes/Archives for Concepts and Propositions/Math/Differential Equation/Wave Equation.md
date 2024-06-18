---
tags:
  - concept
  - math/differential_equation
  - math/functional_analysis
keywords:
  - linear_partial_differential_equations
  - wave_equation
topics:
  - differential_equation
name: Wave Equation
date of note: 2024-06-15
---

## Concept Definition

>[!important]
>**Name**: Wave Equation


>[!important] Definition
>Let $t >0$, $x \in U \subset \mathbb{R}^n$ where $U$ is *open*. Define the unknown $u: \overline{U} \times [0, \infty) \to \mathbb{R}$, and the Laplacian
>$$
>\Delta := \sum_{i=1}^{n}\frac{ \partial^2 }{ (\partial x^i)^2 } 
>$$
>is with respect to *the spatial variables* $x := (x^1 \,{,}\ldots{,}\,x^n).$ And suppose $f: U \times [0, \infty) \to \mathbb{R}$ is given. 
>
>The **wave equation** is defined as 
>$$
>\begin{align*}
> \frac{ \partial^2  }{ \partial t^2 } u - \Delta u = 0.
>\end{align*}
>$$
>
>The **nonautonomous wave equation** is defined as 
>$$
>\begin{align*}
> \frac{ \partial^2  }{ \partial t^2 } u - \Delta u = f.
>\end{align*}
>$$
>
>A common abbreviation is to write 
>$$
>\square u = u_{tt} - \Delta u.
>$$


- [[Linear Semilinear and Quasilinear Partial Differential Equations]]
- [[Laplacian of Smooth Map on Riemannian Manifold]]
- [[Coordinate Representation of Laplace Operator]]
- [[Partial Differential Equations]]


## Explanation

>[!info]
>Let $(x,y) := (x, t)$.
>
>The **wave equation**
>$$
>\begin{align*}
> \frac{\partial^2}{\partial t^2} u - \frac{\partial^2}{\partial x^2} u = 0.
>\end{align*}
>$$
>is a **hyperbolic equation** where $$A = -1, \quad B = 0, \quad C = 1$$


## Operator Equation

>[!important]
>The *wave equation* corresponds to the **divergence equation**
>$$
>\frac{ \partial^2  }{ \partial t^2 } u =  -\text{div}(V)
>$$
>in $U$, where $V$ is the **gradient vector field** of *potential function*  $u$, i.e. $$V = \text{grad}(u).$$

- [[Gradient of Smooth Map]]
- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Divergence Theorem on Riemannian Manifold]]







-----------
##  Recommended Notes and References


- [[Linear Semilinear and Quasilinear Partial Differential Equations]]
- [[Partial Differential Equations]]




- [[Partial Differential Equations by Evans]]