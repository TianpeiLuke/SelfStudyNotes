---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
keywords:
  - taylor_series_method_ode
topics:
  - numerical_differential_equation
name: Taylor Series Methods for Numerical ODE
date of note: 2024-10-31
---

## Concept Definition

>[!important]
>**Name**: Taylor Series Methods for Numerical ODE

![[Taylor Series for Local Polynomial Approximation of Smooth Function#^2aeac6]]

>[!important] Definition
>Consider the *initial value problem* of *ordinary differential equations*
>$$
>\left\{
>\begin{align*}
>\frac{d}{dt} x(t) &= f\left(x(t), t, \lambda\right),\\
>x(t_{0}) &= x_{0}
>\end{align*}
>\right.
>$$
>where 
>- $f: U \times J \times \Lambda \to \mathbb{R}^n$ is a smooth function, i.e. it is *continuous differentiable*. 
>- $J \subseteq \mathbb{R}$, $U \subseteq \mathbb{R}^n$, and $\Lambda \subseteq \mathbb{R}^k$ be open subsets.
>  
>An **order-p Taylor series method** approximates the solution of ODE via the Taylor series expansion on $x$
>$$
>x(t+h) = x(t) + h\,x^{(1)}(t)\; + \frac{1}{2}h^2\,(x^{(2)}(t))^2 \,{+}\ldots{+}\,\frac{h^{p}}{p!}x^{(p)}(t) + R_{p}(t)
>$$
>where
>$$
>R_{p}(t) := \frac{1}{(p+1)!}h^{p+1}\,x^{(p+1)}(\xi), \quad \xi\in (t, t+h).
>$$
>- Choose $t = t_{n}$, we have **TS(p) method** $$x_{n+1} = x_{n} + hx_{n}' + \frac{1}{2}h^2x_{n}^{(2)} \,{+}\ldots{+}\,\frac{h^{p}}{p!}x_{n}^{(p)}$$ where $$x_{n}' \approx x^{(1)}(t_{n}) \quad{,}\ldots{,}\quad x_{n}^{(p)}\approx x^{(p)}(t_{n})$$
>- To obtain $x_{n}^{(p)}\approx x^{(p)}(t_{n})$, it is *necessary* to **differentiate** the *RHS of ODE* $f(x(t), t, \lambda)$ **$(p-1)$ times**,
>- Note that $$x_{n}' \approx x^{(1)}(t_{n}) = f(x_{n}, t_{n}, \lambda)$$
>- e.g. $$\begin{align*}x_{n}^{(2)} &\approx \frac{d}{dt} \left(\frac{d}{dt} x(t_{n})\right) \\[5pt] &= \frac{d}{dt} f(x(t_{n}), t_{n}, \lambda) \\[5pt] &= \partial_{x}f\,\left(\frac{d}{dt} x\right) + \partial_{t}f \\[5pt] &= \left\{  f\,\partial_{x}f\, + \partial_{t}f \right\}  \big|_{t_{n}}\end{align*}$$ 

^96fcb1

- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]


## Explanation





-----------
##  Recommended Notes and References


- [[Ordinary Differential Equations]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]

- [[Numerical Methods for Ordinary Differential Equations by Butcher]] pp 94, 120 -122
- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 33 - 39