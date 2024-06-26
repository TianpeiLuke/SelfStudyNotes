---
tags:
  - concept
  - math/differential_equation
  - math/functional_analysis
keywords:
  - linear_partial_differential_equations
  - heat_equation
  - diffusion_process
topics:
  - differential_equation
name: 
date of note: 2024-06-15
---

## Concept Definition

>[!important]
>**Name**: Heat Equation and Diffusion Equation


>[!important] Definition
>Let $t >0$, $x \in U \subset \mathbb{R}^n$ where $U$ is *open*. Define the unknown $u: \overline{U} \times [0, \infty) \to \mathbb{R}$, and the Laplacian
>$$
>\Delta := \sum_{i}^{n}\frac{ \partial^2 }{ (\partial x^i)^2} 
>$$
>is with respect to *the spatial variables* $x := (x^1 \,{,}\ldots{,}\,x^n).$ And suppose $f: U \times [0, \infty) \to \mathbb{R}$ is given. 
>
>The **heat equation** or **diffusion equation** is defined as 
>$$
>\begin{align*}
> \frac{ \partial  }{ \partial t }  u - \Delta u = 0.
>\end{align*}
>$$
>
>The **nonautonomous heat equation** is defined as 
>$$
>\begin{align*}
> \frac{ \partial  }{ \partial t }  u - \Delta u = f.
>\end{align*}
>$$

- [[Linear Semilinear and Quasilinear Partial Differential Equations]]
- [[Laplacian of Smooth Map on Riemannian Manifold]]
- [[Coordinate Representation of Laplace Operator]]


## Explanation

>[!info]
>Let $(x,y) := (x, t)$.
>
>The **heat equation** or **diffusion equation** 
>$$
>\begin{align*}
> \frac{\partial}{\partial t} u - \frac{\partial^2}{\partial x^2} u = 0.
>\end{align*}
>$$
>is **parabolic equation** since
>$$
>A = -1, \quad B = 0, \quad C = 0
>$$

- [[Second-Order Linear Partial Differential Equations]]

## Operator Equation

>[!important]
>The *heat equation* corresponds to the **divergence equation**
>$$
>\frac{ \partial  }{ \partial t } u =  -\text{div}(V)
>$$
>in $U$, where $V$ is the **gradient vector field** of *potential function*  $u$, i.e. $$V = \text{grad}(u)$$

- [[Gradient of Smooth Map]]
- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Divergence Theorem on Riemannian Manifold]]


## Laplace Equation and Poisson Equation

- [[Laplace Equation and Poisson Equation]]


## Stochastic Differential Equation and Brownian Motion

>[!important]
>The heat equation corresponds to the **Kolmogorov backward equation** with respect to the *generator* of Brownian motion, i.e. $\mu = 0$ and $\sigma = 1$, then change of time $t = -s$.
>$$
> dX_{t} = dW_{t} 
>$$
>
>In particular, the **unique**, bounded solution of heat equation with *initial boundary conditions*
>$$
>\left\{
>\begin{align*}
> \frac{ \partial  }{ \partial t }  u &= \frac{1}{2}\Delta u.\\[5pt]
>  u(x,  0) &= g(x)\\
>  u(0, t) & = 0\\
>  u(L, t) & = 0
>\end{align*}
>\right.
>$$
>is given by
>$$
> u(x, t) := \mathbb{E}\left[ g(W_{t})\, \mathbb{1}\left(t < \tau\right) \;|\; W_{0} = x \right]
>$$
>and $\tau$ is the **first hitting time (stopping time)** where $g(W_{t})$ first hits *either boundary.*
>$$
>\tau = \min\{ t: \; g(W_{t}) \in \{ L, 0 \} \}.
>$$


- [[Diffusion and Infinite Dimensional ODE]]
- [[Brownian Motion Wiener Process]]
- [[Infinitesimal Generator of Brownian Motion and Laplacian]]
- [[Itô Process]]
- [[Stopping Time and Stochastic Integral]]




## Kolmogorov Backward Equation and Forward Equation

![[Fokker–Planck and Kolmogorov Forward-Backward Equation#^89943e]]

![[Fokker–Planck and Kolmogorov Forward-Backward Equation#^6aedc0]]


- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]







-----------
##  Recommended Notes and References

- [[Laplace Equation and Poisson Equation]]

- [[Autonomous and Nonautonomous Ordinary Differential Equations]]
- [[Linear Semilinear and Quasilinear Partial Differential Equations]]
- [[Partial Differential Equations]]

- [[Diffusion and Infinite Dimensional ODE]]
- [[Itô Process]]
- [[Stochastic Differential Equations]]

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]


- [[Partial Differential Equations by Evans]]

- [[Introduction to Stochastic Calculus by Klebaner]]
- [[Introduction to Stochastic Differential Equations by Evans]]