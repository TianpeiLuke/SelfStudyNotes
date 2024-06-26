---
tags:
  - concept
  - math/differential_equation
keywords:
  - second_order_linear_pde
topics:
  - differential_equation
name: Second-Order Linear Partial Differential Equations
date of note: 2024-06-15
---

## Concept Definition

>[!important]
>**Name**: Second-Order Linear Partial Differential Equations

>[!important] Definition
>Let $u: \mathbb{R} \times \mathbb{R} \to \mathbb{R}$ be the unknown function.
>
>Any *second-order linear PDE* can be written as
>$$
>\left(A\,\frac{ \partial^2 }{ \partial x^2 } + B \frac{ \partial^2 }{ \partial x\, \partial y} + C \frac{ \partial^2 }{ \partial y^2 }\right) + \left(D\,\frac{ \partial }{ \partial x } + E\,\frac{ \partial }{ \partial y }\right) u + F\,u = 0
>$$
>where $A, B, C,D, E,F$ are all functions of $(x,y)$.
>
>- The partial differential equation is called an **elliptic equation** if $$B^2 - A\,C < 0$$
>- The partial differential equation is called a **hyperbolic equation** if $$B^2 - A\,C > 0$$
>- The partial differential equation is called a **parabolic equation** if $$B^2 - A\,C = 0$$

- [[Linear Semilinear and Quasilinear Partial Differential Equations]]
- [[Second-Order Elliptic Equation]]
- [[Second-Order Hyperbolic Equation]]
- [[Second-Order Parabolic Equation]]



## Explanation



## Examples

>[!example]
>The **Laplace equation** 
>$$
>\begin{align*}
> \left(\frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2}\right) u= 0.
>\end{align*}
>$$
>and **(linear) Poisson equation**
>$$
>\begin{align*}
> \left(\frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2}\right) u - f = 0.
>\end{align*}
>$$
>are both **elliptic equation** since
>$$
>A = 1, \quad B = 0, \quad C = 1
>$$

- [[Laplace Equation and Poisson Equation]]

>[!example]
>The **Helmhotz equation** 
>$$
>\begin{align*}
> \left(\frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2}\right) u - \lambda u = 0.
>\end{align*}
>$$
>is an **elliptic equation** since
>$$
>A = 1, \quad B = 0, \quad C = 1
>$$

- [[Helmhotz Equation]]

>[!example]
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

- [[Heat Equation and Diffusion Equation]]

>[!example]
>Let $(x,y) := (x, t)$.
>
>The **wave equation**
>$$
>\begin{align*}
> \frac{\partial^2}{\partial t^2} u - \frac{\partial^2}{\partial x^2} u = 0.
>\end{align*}
>$$
>is a **hyperbolic equation** where $$A = -1, \quad B = 0, \quad C = 1$$

- [[Wave Equation]]

>[!example]
>Let $(x,y) := (x, t)$.
>
>The **Kolmogorov  backward equation**
>$$
>\begin{align*}
> \frac{\partial}{\partial t} u + \frac{1}{2}\sigma^2\frac{\partial^2}{\partial x^2} u + \mu \frac{ \partial  }{ \partial x }u = 0.
>\end{align*}
>$$
>is a **parabolic equation** where $$A = \frac{1}{2}\sigma^2, \quad B = 0, \quad C = 0$$

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]

>[!example]
>Let $(x,y) := (x, t)$.
>
>The **Kolmogorov  forward equation** or **Fokker-Planck equation**
>$$
>\begin{align*}
>\frac{\partial}{ \partial t } u - \frac{1}{2}\frac{\partial^2 }{ \partial x^2 }\left(\sigma^2\, u\right) + \frac{\partial }{\partial x }\left(\mu\,u\right) = 0
>\end{align*}
>$$
>is a **parabolic equation** where $$A = -\frac{1}{2}, \quad B = 0, \quad C = 0$$

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]







-----------
##  Recommended Notes and References

- [[Partial Differential Equations]]

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]
- [[Laplace Equation and Poisson Equation]]


- [[Partial Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]
- [[Introduction to Stochastic Differential Equations by Evans]]


- Wikipedia [Elliptic_partial_differential_equation](https://en.wikipedia.org/wiki/Elliptic_partial_differential_equation)
- Wikipedia [Hyperbolic_partial_differential_equation](https://en.wikipedia.org/wiki/Hyperbolic_partial_differential_equation)
- Wikipedia [Parabolic_partial_differential_equation](https://en.wikipedia.org/wiki/Parabolic_partial_differential_equation)