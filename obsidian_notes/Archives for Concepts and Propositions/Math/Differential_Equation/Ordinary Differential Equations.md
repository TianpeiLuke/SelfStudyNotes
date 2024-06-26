---
tags:
  - concept
  - math/differential_equation
keywords:
  - ordinary_differential_equations
  - system_of_odes
topics:
  - differential_equation
name: Ordinary Differential Equations
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Ordinary Differential Equations

>[!important] Definition
>Let $J \subseteq \mathbb{R}$, $U \subseteq \mathbb{R}^n$, and $\Lambda \subseteq \mathbb{R}^k$ be open subsets, and suppose that $f: U \times J \times \Lambda \to \mathbb{R}^n$ is a smooth function, i.e. it is continuous differentiable.
>
>An **ordinary differential equation (ODE)** is an equation of the form
>$$
>\begin{align*}
> \frac{d}{dt} x &= f(x, t, \lambda)
>\end{align*}
>$$
>where the vector $x\in \mathbb{R}^n$ are **state variables** and $\lambda\in \Lambda$ is a vector of **parameters**.

- [[Ordinary Differential Equations by Chicone]] pp 2

>[!important] Definition
>- If we are concerned with the *component* of the vector variable $x$, we say that the above is a **system of differential equations**.
>  
>- If we are interested in changes with respect to *parameters* $\lambda$, the differential equation is called a **family of differential equations**.  

>[!important] Definition
>If $\lambda \in \Lambda$ is fixed, then a **solution** of differential equation is a function $\phi: J_{0} \to U$ given by  $$t \mapsto \phi(t)$$, where $J_{0}$ is an open subset of $J$ such that 
>$$
>\begin{align*}
> \frac{d}{dt} \phi(t) &= f(\phi(t), t, \lambda)
>\end{align*}
>$$
>for all $t \in J_{0}$.

>[!important] Definition
>We also call a solution as "**trajectory**", "*phase curve*" and "**integral curve**"

- [[Integral Curve of Vector Field]]

>[!important] Definition
>If we are interested in the future state given initial state, the corresponding differential equations can be written as
>$$
>\left\{
>\begin{align*}
>\frac{d}{dt} x(t) &= f\left(x(t), t, \lambda\right),\\
>x(t_{0}) &= x_{0}
>\end{align*}
>\right.
>$$
>The second equation is called the **initial condition**.
>
>If the differential equations is defined as above and $(x_{0}, t_{0}) \in U\times J$, then the pair of equations is called an **initial value problem**.



## Explanation



## Existence, Smoothness and Extension of Solution

>[!quote]
> The fundamental issues of the general theory of differential equations are the **existence**, **uniqueness**, **extension**, and **continuity** with respect to **parameters of solutions** of **initial value problems.** Fortunately, all of these issues are resolved by the following foundational results of the subject: *Every initial value problem has a unique solution that is smooth with respect to initial conditions and parameters. Moreover, the solution of an initial value problem can be extended in time until it either reaches the boundary of the domain of definition of the differential equation or blows up to infinity.*
> 
>-- [[Ordinary Differential Equations by Chicone]] pp 3 


- [[Existence and Uniqueness of Solution of Ordinary Differential Equations]]
- [[Smoothness of Solution of ODE]]
- [[Extension of Solution of Ordinary Differential Equations]]

## Type of ODEs

- [[Autonomous and Nonautonomous Ordinary Differential Equations]]




-----------
##  Recommended Notes and References



- [[Vector Field as Infinitesimal Generator of Local Flow]]
- [[Stochastic Differential Equations]]

- [[Ordinary Differential Equations by Chicone]]
- Chicone, C. (2006). _Ordinary Differential Equations with Applications_ (2nd edition). Springer.