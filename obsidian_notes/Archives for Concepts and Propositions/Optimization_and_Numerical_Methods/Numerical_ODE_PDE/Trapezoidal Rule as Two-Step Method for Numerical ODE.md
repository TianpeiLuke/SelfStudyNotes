---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
keywords:
  - trapezoidal_method_ode
topics:
  - numerical_differential_equation
name: Trapezoidal Rule as Two-Step Method for Numerical ODE
date of note: 2024-11-01
---

## Concept Definition

>[!important]
>**Name**: Trapezoidal Rule as Two-Step Method for Numerical ODE

![[Taylor Series Methods for Numerical ODE#^96fcb1]]

- [[Taylor Series Methods for Numerical ODE]]
- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]

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
>Consider the *second-order Taylor expansion*, $$z(t+h) = z(t) + hz'(t) + \frac{1}{2}h^2z''(t) + O(h^3)$$  and substitute the Taylor expansion of $z'$,  $$z'(t+ h) = z'(t) + h\,z''(t) + O(h^2) \implies h\,z''(t) = z'(t+ h) - z'(t) + O(h^2)$$  
>We have a new approximation
>$$
>\begin{align*}
>z(t+h) &= z(t) + hz'(t) + \frac{1}{2}h\left[z'(t+ h) - z'(t) + O(h^2)  \right] + O(h^3) \\[5pt]
>&= z(t) + \frac{1}{2}h\left[ z'(t+h) + z'(t) \right] + O(h^3) 
>\end{align*}
>$$
>- This approximation applies when $z \in \mathcal{C}^3$
>- Replace $z = x$ and $z' = f(x, t)$, we have $$x(t+ h) = x(t) + \frac{1}{2}h\left[ f(x(t+h), t+h, \lambda) - f(x(t), t, \lambda) \right] $$
>  
>  
>In summary, the **trapezoidal rule** for discretization of ODE over the grid $t_{n} = t_{0} + nh$ is given by 
>$$
>x_{n+1} = x_{n} + \frac{1}{2}h\left[ f(x_{n+1}, t_{n+1}, \lambda) + f(x_{n}, t_{n}, \lambda) \right] 
>$$
>or in short $$x_{n+1} - x_{n} = \frac{1}{2}h(f_{n+1} + f_{n})$$ where
>- $$f_{n+j} := f(x_{n+j}, t_{n+j}, \lambda)$$
>- Note that $f_{n}$ is just an *approximation* of the gradient of $x$ at $t_{n}$, not exactly the gradient (which is RHS) $$f(x_{n}, t_{n}, \lambda) \approx f(x(t_{n}), t_{n}, \lambda) = x'(t_{n})$$
>- Since $x_{n+1}$ appears on both hand sides of the equation, the **trapezoidal rule** is an **implicit method.**

^82f709

- [[Implicit Euler Method for Discretization of ODE]]


## Explanation





-----------
##  Recommended Notes and References


- [[Linear Multistep Methods for Numerical ODE]]
- [[Ordinary Differential Equations]]


- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 45 - 48