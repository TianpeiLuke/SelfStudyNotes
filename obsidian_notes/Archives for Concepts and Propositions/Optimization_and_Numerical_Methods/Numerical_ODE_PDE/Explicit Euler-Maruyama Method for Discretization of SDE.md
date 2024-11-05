---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
  - math/stochastic_differential_equations
keywords:
  - euler_maruyama_method_sde
topics:
  - numerical_differential_equation
  - stochastic_differential_equation
name: Explicit Euler-Maruyama Method for Discretization of SDE
date of note: 2024-10-31
---

## Concept Definition

>[!important]
>**Name**: Explicit Euler-Maruyama Method for Discretization of SDE

![[Stochastic Differential Equations#^dda568]]


>[!important] Definition
>Consider the *stochastic differential equation*
>$$
>\left\{ 
>\begin{align*}
>dX(t) &= \mu\left( X(t)\right)\,dt + \sigma\left( X(t)\right)\,dW\\
>X(0)&= X_{0}
>\end{align*}
>\right.
>$$
>
>The **Euler-Maruyama method** is given by
>$$
>x_{n+1} = x_{n} + h\,\mu(x_{n}) + \sqrt{h}\,\sigma(x_{n})\,\xi_{n}
>$$
>where $\xi_{n} \stackrel{i.i.d.}{\sim} \mathcal{N}(0,I)$

- [[Stochastic Differential Equations]]
- [[Time Homogeneous Diffusion and SDE]]
- [[Explicit Euler Method for Discretization of ODE]]

## Explanation


## Langevin Dynamics

- [[Langevin Equation]]
- [[Langevin Dynamics and Langevin Sampling]]




-----------
##  Recommended Notes and References




- [[Ordinary Differential Equations]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]
- [[Homogeneous Linear Stochastic Differential Equation]]

- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 231