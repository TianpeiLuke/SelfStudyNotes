---
tags:
  - concept
  - math/differential_equation
keywords:
  - autonomous_ode
  - nonautonomous_ode
topics:
  - differential_equation
name: Autonomous and Nonautonomous Ordinary Differential Equations
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Types of Ordinary Differential Equations

>[!important] Definition
>An **autonomous differential equation** is given by
>$$
>\begin{align*}
> \frac{d}{dt} x &= f(x,\lambda)
>\end{align*}
>$$
>for $x\in \mathbb{R}^n$ and $\lambda\in \mathbb{R}^{k}$; that is, the function $f$ *does not depends explicitly* on the independent variable $t$.

- [[Ordinary Differential Equations]]
- [[Ordinary Differential Equations by Chicone]]. pp 6

>[!important] Definition
>If the function $f$ *does depends explicitly* on the independent variable $t$, then the ODE is called an **non-autonomous differential equation**.



## Explanation

>[!important]
>Every **solution** of the **nonautonomous differential equation** can be obtained from a *solution* of **the autonomous system**.
>
>That is, for 
>$$
>\begin{align*}
> \frac{d}{dt} x &= f(x,t, \lambda)
>\end{align*}
>$$
>we can define a new variable $\tau$ so that 
>$$
>\begin{align*}
> \frac{d}{dt} x &= f(x, \tau, \lambda)\\
> \frac{d}{dt} \tau &= 1
>\end{align*}
>$$

## Vector Field and Integral Curve

![[Integral Curve of Vector Field#^3d69fd]]

- [[Vector Field on Manifold]]

- [[Integral Curve of Vector Field]]

## Flows

![[Global Flow on Smooth Manifold#^532ef7]]


- [[Global Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Global Flow]]

>[!important]
>The solution $$t\mapsto \phi(t, x)$$ of the ordinary differential equations $$\frac{d}{dt} x = f(x)$$ forms a **flow**





-----------
##  Recommended Notes and References



- [[Ordinary Differential Equations]]

- [[Ordinary Differential Equations by Chicone]]
- [[Homogeneous Linear Stochastic Differential Equation]]