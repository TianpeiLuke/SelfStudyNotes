---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
keywords:
  - adams_bashforth_method_ode
topics:
  - numerical_differential_equation
name: Adams-Bashforth Method for Numerical ODE
date of note: 2024-11-01
---

## Concept Definition

>[!important]
>**Name**: Adams-Bashforth Method for Numerical ODE

![[Trapezoidal Rule as Two-Step Method for Numerical ODE#^82f709]]

- [[Trapezoidal Rule as Two-Step Method for Numerical ODE]]

### Two-Step Adams-Bashforth

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
>Consider the *second-order Taylor expansion*, $$z(t+h) = z(t) + hz'(t) + \frac{1}{2}h^2z''(t) + O(h^3)$$  and substitute the *Taylor expansion* of $z'$ *backward*,  $$z'(t - h) = z'(t) - h\,z''(t) + O(h^2) \implies h\,z''(t) = z'(t) - z'(t- h) + O(h^2)$$  
>We have a new approximation
>$$
>\begin{align*}
>z(t+h) &= z(t) + hz'(t) + \frac{1}{2}h\left[z'(t) - z'(t- h) + O(h^2)  \right] + O(h^3) \\[5pt]
>&= z(t) + \frac{1}{2}h\left[ 3z'(t) - z'(t- h) \right] + O(h^3) 
>\end{align*}
>$$
>- Replace $z = x$ and $z' = f(x, t)$, we have $$x(t+ h) = x(t) + \frac{1}{2}h\left[ 3f(x(t), t, \lambda) - f(x(t-h), t-h, \lambda) \right] $$
>  
>In summary, the **two-step Adams-Bashforth** or **AB(2)** for discretization of ODE over the grid $t_{n} = t_{0} + nh$ is given by 
>$$
>x_{n+1} = x_{n} + \frac{1}{2}h\left[ 3f(x_{n}, t_{n}, \lambda) - f(x_{n-1}, t_{n-1}, \lambda) \right] 
>$$
>or in short $$x_{n+1} = x_{n} + \frac{1}{2}h(3f_{n} - f_{n-1})$$ where
>- $$f_{n+j} := f(x_{n+j}, t_{n+j}, \lambda)$$
>- In **AB(2)**, the solution $x_{n+1}$ at time $t_{n+1}$ depends on data $x$ *in two previous time* $t_{n}$ and $t_{n-1}$
>- The **AB(2)** method belongs to the *family of* **two-step linear multistep method (LMM)**

- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]


## Explanation

>[!info]
>- **Trapezoidal rule** $$x_{n+1} - x_{n} = \frac{1}{2}h(f_{n+1} + f_{n})$$
>- **Adams-Bashforth AB(2)** $$x_{n+1} - x_{n} = \frac{1}{2}h(3f_{n} - f_{n-1})$$
>- **Explicit Euler**: $$x_{n+1} - x_{n} = hf_{n}$$
>- **Implicit Euler**: $$x_{n+1} - x_{n} = hf_{n+1}$$

- [[Explicit Euler Method for Discretization of ODE]]
- [[Implicit Euler Method for Discretization of ODE]]



-----------
##  Recommended Notes and References


- [[Linear Multistep Methods for Numerical ODE]]


- [[Taylor Series Methods for Numerical ODE]]
- [[Ordinary Differential Equations]]


- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 45 - 48, 66
- [[Numerical Methods for Ordinary Differential Equations by Butcher]] pp 111 - 117