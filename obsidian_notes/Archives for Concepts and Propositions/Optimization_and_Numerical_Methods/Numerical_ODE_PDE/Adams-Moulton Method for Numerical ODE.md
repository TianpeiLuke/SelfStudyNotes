---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
keywords:
  - adams_moulton_method_ode
topics:
  - numerical_differential_equation
name: Adams-Moulton Method for Numerical ODE
date of note: 2024-11-01
---

## Concept Definition

>[!important]
>**Name**: Adams-Moulton Method for Numerical ODE

![[k-Step Methods for Numerical ODE#^57a043]]

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
>The **k-step Adams-Moulton** or **AM(k)** over the grid $t_{n} = t_{0} + nh$ is given by
>$$
>x_{n+k} - x_{n+k-1} = h\left\{ \beta_{k}f_{n+k} + \beta_{k-1}f_{n+k-1} \,{+}\ldots{+}\, \beta_{0}f_{n} \right\} 
>$$
>where the *coefficients* $\beta_{0}\,{,}\ldots{,}\,\beta_{k}$ are chosen so that $$C_{0} = C_{1} \,{=}\ldots{=}\,C_{k-1} = 0$$
>- $$x_{n+j} \approx x(t_{n+j}), \quad f_{n+j} = f(x_{n+j}, t_{n+j}, \lambda) \approx f(x(t_{n+j}), t_{n+j}, \lambda)$$
>- The **AB(k)** method belongs to the *family of* **k-step implicit linear multistep method (LMM)**


- [[k-Step Methods for Numerical ODE]]

## Explanation

>[!info]
>The *$1$-step Adams-Moulton* method is the **trapezoidal rule**.

- [[Trapezoidal Rule as Two-Step Method for Numerical ODE]]



## Adams-Bashforth Method

- [[Adams-Bashforth Method for Numerical ODE]]


-----------
##  Recommended Notes and References


- [[Linear Multistep Methods for Numerical ODE]]

- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 66
- [[Numerical Methods for Ordinary Differential Equations by Butcher]] pp 111 - 117