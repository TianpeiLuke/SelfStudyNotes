---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
keywords:
  - implicit_euler_method_ode
topics:
  - numerical_differential_equation
name: Implicit Euler Method for Discretization of ODE
date of note: 2024-10-31
---

## Concept Definition

>[!important]
>**Name**: Implicit Euler Method for Discretization of ODE

![[Ordinary Differential Equations#^df84bb]]

![[Taylor Series for Local Polynomial Approximation of Smooth Function#^d63547]]

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
>Assume the time discretization $$t_{n} = t_{0} + nh, \quad n=1\,{,}\ldots{,}\,N$$ and $$N = \left\lfloor  \frac{t_{f} - t_{0}}{h}  \right\rfloor.$$  Denote $x_{n} := x(t_{n})$ as the curve $x$ evaluated at $t_{n}.$ 
>
>The **implicit Euler method** or **backward Euler method** approximate the ODE via *linear equation* as $$x_{n+1} = x_{n} + h\,f_{n+1}, \quad n=1\,{,}\ldots{,}\,N$$
>where
>- the function $f$ is evaluated at *future time-step* $t_{n}$ $$f_{n+1} := f(x_{n+1}, t_{n+1}, \lambda).$$   


- [[Ordinary Differential Equations]]
- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]
- [[Implicit Function Theorem]]

## Explanation

>[!info]
>- The **explicit Euler method** $$x_{n+1} = x_{n} + h\,f(x_{n}, t_{n})$$ is a *recursion formula*, where $x_{n+1}$ can be obtained via **forward pass** only.
>	- The explicit Euler method leads to **gradient descent** $$x_{n+1} = x_{n} + h\,\nabla L(x_{n})$$ 
>- The **implicit Euler method** $$x_{n+1} = x_{n} + h\,f(x_{n+1}, t_{n+1})$$ is an *algebraic equation*.
>	- The implicit Euler method leads to **JKO update** $$x_{n+1} \in \arg\min_{x}\left\{ L(x) + \frac{\lVert x - x_{n} \rVert_{2}^2 }{2h} \right\} $$ 

^33e5a8

- [[Explicit Euler Method for Discretization of ODE]]

## Gradient Flow

![[Gradient Flow in Euclidean Space#^ce373d]]

![[Gradient Flow in Euclidean Space#^476dc0]]

- [[Gradient Flow in Euclidean Space]]


## Linear Multistep Method

- [[Linear Multistep Methods for Numerical ODE]]




-----------
##  Recommended Notes and References




- [[Autonomous and Nonautonomous Ordinary Differential Equations]]

- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 48, 54, 58, 67, 78–79, 103, 111–121, 159, 181, 191, 205, 214
- [[Numerical Methods for Ordinary Differential Equations by Butcher]] pp 68 - 69