---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
keywords:
  - explicit_euler_method_ode
topics:
  - numerical_differential_equation
name: Explicit Euler Method for Discretization of ODE
date of note: 2024-10-31
---

## Concept Definition

>[!important]
>**Name**: Explicit Euler Method for Discretization of ODE

![[Ordinary Differential Equations#^df84bb]]

![[Taylor Series for Local Polynomial Approximation of Smooth Function#^d63547]]

- [[Ordinary Differential Equations]]
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
>The **explicit Euler method** or **Euler method** or **Euler scheme** is a *temporal discretization method* to approximate the solution of the ODE over a *grid* of points $t = t_{n}$ where $$t_{n} = t_{0} + nh, \quad n=1\,{,}\ldots{,}\,N$$ and $$N = \left\lfloor  \frac{t_{f} - t_{0}}{h}  \right\rfloor.$$
>
>In particular, consider the *first-order Taylor expansion* of $x$, $$x(t_{n} + h) = x(t_{n}) + x'(t_{n})\,h + o(h^2)$$  
>- Substitute the ODE $$x'(t_{n}) = f(x(t_{n}), t_{n}, \lambda),$$ we have $$x(t_{n} + h) = x(t_{n}) + h\,f(x(t_{n}), t_{n}, \lambda) + o(h^2)$$
>  
>Thus the **Euler method** approximate the solution of ODE via recursion as $$x_{n+1} = x_{n} + h\,f_{n}, \quad n=1\,{,}\ldots{,}\,N$$
>where
>- $$x_{n} \approx x(t_{n}), \quad f_{n} := f(x_{n}, t_{n}, \lambda) \approx f(x(t_{n}), t_{n}, \lambda).$$   
>- Sometimes it is more convenient to use $x_{n}'$ for the approximation of $x$ at $t_{n}$, then the *Euler method* is written as $$x_{n+1} = x_{n} + h\,x_{n}'$$



## Explanation

![[Implicit Euler Method for Discretization of ODE#^33e5a8]]

- [[Implicit Euler Method for Discretization of ODE]]

## Gradient Descent as Euler Method on Gradient Flow Problem

![[Gradient Flow in Euclidean Space#^6fbd2b]]

>[!info]
>Use **explicit Euler method** to solve the *gradient flow problem*, we have
>$$
>x_{n+1} = x_{n} - h\,\nabla f(x_{n})
>$$
>which is the **gradient descent algorithm**.

- [[Gradient Flow in Euclidean Space]]
- [[Gradient Descent Algorithm]]

## Linear Multistep Method

- [[Linear Multistep Methods for Numerical ODE]]



-----------
##  Recommended Notes and References


- [[Autonomous and Nonautonomous Ordinary Differential Equations]]

- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 23 - 25
- [[Numerical Methods for Ordinary Differential Equations by Butcher]] pp 55, 70, 83