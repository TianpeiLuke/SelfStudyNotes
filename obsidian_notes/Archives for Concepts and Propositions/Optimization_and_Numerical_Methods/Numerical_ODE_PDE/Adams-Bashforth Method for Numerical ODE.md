---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
keywords:
  - adams_bashforth_method_ode
  - linear_multistep_methods_ode
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
>Consider the *initial value problem (IVP)* of *ordinary differential equations*
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
>- The task is to find the *temporal discretization* of the *approximate solution* of the IVP.
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
>In summary, the **two-step Adams-Bashforth** or **AB(2)** over the grid $t_{n} = t_{0} + nh$ is given by
>$$
>x_{n+1} = x_{n} + \frac{1}{2}h\left[ 3f(x_{n}, t_{n}, \lambda) - f(x_{n-1}, t_{n-1}, \lambda) \right] 
>$$
>or in short $$x_{n+1} = x_{n} + \frac{1}{2}h(3f_{n} - f_{n-1})$$ where
>- $$f_{n+j} := f(x_{n+j}, t_{n+j}, \lambda)$$
>- In **AB(2)**, the solution $x_{n+1}$ at time $t_{n+1}$ depends on data $x$ *in two previous time* $t_{n}$ and $t_{n-1}$
>- The **AB(2)** method belongs to the *family of* **two-step linear multistep method (LMM)**

- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]

### $k$-Step Adams-Bashforth

![[k-Step Methods for Numerical ODE#^57a043]]

>[!important] Definition
>The **k-step Adams-Bashforth** or **AB(k)** over the grid $t_{n} = t_{0} + nh$ is given by
>$$
>x_{n+k} - x_{n+k-1} = h\left\{ \beta_{k-1}f_{n+k-1} \,{+}\ldots{+}\, \beta_{0}f_{n} \right\} 
>$$
>where the *coefficients* $\beta_{0}\,{,}\ldots{,}\,\beta_{k-1}$ are chosen so that $$C_{0} = C_{1} \,{=}\ldots{=}\,C_{k-1} = 0$$
>- $$x_{n+j} \approx x(t_{n+j}), \quad f_{n+j} = f(x_{n+j}, t_{n+j}, \lambda) \approx f(x(t_{n+j}), t_{n+j}, \lambda)$$
>- The **AB(k)** method belongs to the *family of* **k-step explicit linear multistep method (LMM)**

- [[k-Step Methods for Numerical ODE]]


## Explanation

>[!info]
>- **Trapezoidal rule (AM(1))** $$x_{n+1} - x_{n} = \frac{1}{2}h(f_{n+1} + f_{n})$$
>- **Adams-Bashforth AB(2)** $$x_{n+1} - x_{n} = \frac{1}{2}h(3f_{n} - f_{n-1})$$
>- **Explicit Euler (AB(1))**: $$x_{n+1} - x_{n} = hf_{n}$$
>- **Implicit Euler**: $$x_{n+1} - x_{n} = hf_{n+1}$$

- [[Explicit Euler Method for Discretization of ODE]]
- [[Implicit Euler Method for Discretization of ODE]]

>[!info]
>The *$1$-step Adams-Bashforth* is the **explicit Euler method**.


## Adams-Moulton 

>[!info]
>The **Adams-Moulton method** is the **implicit** version of *Adams-Bashforth* method.

- [[Adams-Moulton Method for Numerical ODE]]



-----------
##  Recommended Notes and References


- [[Linear Multistep Methods for Numerical ODE]]


- [[Taylor Series Methods for Numerical ODE]]
- [[Ordinary Differential Equations]]
- [[Space of Continuous Differentiable Functions]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]

- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 45 - 48, 66
- [[Numerical Methods for Ordinary Differential Equations by Butcher]] pp 111 - 117