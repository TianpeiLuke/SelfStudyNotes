---
tags:
  - concept
  - math/differential_equation
  - math/stochastic_process
keywords:
  - feynman_kac_formula
topics:
  - differential_equation
  - stochastic_process
name: Feynman-Kac Formula
date of note: 2024-06-12
---

## Concept Definition

>[!important]
>**Name**: Feynman-Kac Formula

![[Martingale via Solution of SDE and Backward Equation#^f4351f]]

>[!important] Theorem (Feynman-Kac Formula)
>For given **bounded functions** $\phi(x,t)$, and $g(x)$, assume that there **exists** a solution to *the second-order parabolic equation* with initial condition
>$$
>\begin{align*}
>\left\{
>\begin{array}{cc}
>\dfrac{ \partial  }{ \partial t}f(x, t) + L_{t}\,f(x, t) = \phi(x,t)\;f(x,t)& \\
>f(x, T) = g(x)& \\
>\end{array}
>\right.
>\end{align*}
>$$ 
>where 
>$$
>L_{t} := \frac{1}{2}\sigma^2(x, t)\,\frac{ \partial^2 }{ \partial x^2 } + \mu(x, t) \frac{ \partial  }{ \partial x } 
>$$
> is the *generator* of stochastic differential equation.
> 
> Then the **solution** of above PDE is **unique** and it is represented as
>$$
>\begin{align*}
> f(x, t) =  \mathbb{E}\left[ \exp\left( -\int_{t}^{T}\,\phi(X_{s}, s) ds\right)\;g\left(X_{T}\right)\;\Big|\;X_{t} = x \right]
>\end{align*}
>$$ 

- [[Martingale via Solution of SDE and Backward Equation]]
- [[Linear Stochastic Differential Equation Explicit Solution]]
- [[Infinitesimal Generator of Stochastic Differential Equation]]

- [[Introduction to Stochastic Calculus by Klebaner]] pp 155
- [[Introduction to Stochastic Differential Equations by Evans]] pp 110
- Oksendal, B. (2013). _Stochastic differential equations: an introduction with applications_. Springer Science & Business Media pp 145

## Explanation

>[!info]
>Use the semigroup $\left\{ T_{s,t} \right\}$ associated with transition function $p$ then the solution of above PDE can be written as
>$$
>f(s, x) =  \left[T_{s, t}\left( g(\cdot)\,e^{- \int_{s}^{\cdot}\;\phi(\cdot, s)\,ds} \right) \right] (x)
>$$
>

- [[Semigroup associated with Transition Function]]




-----------
##  Recommended Notes and References

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]
- [[Martingale via Solution of SDE and Backward Equation]]

- [[Second-Order Parabolic Equation]]
- [[Second-Order Linear Partial Differential Equations]]
- [[Stochastic Differential Equations]]
- [[Martingale]]

- [[Introduction to Stochastic Calculus by Klebaner]]
- [[Introduction to Stochastic Differential Equations by Evans]]