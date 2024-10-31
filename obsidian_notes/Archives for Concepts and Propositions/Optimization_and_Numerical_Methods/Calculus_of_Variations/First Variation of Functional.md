---
tags:
  - concept
  - math/functional_analysis
  - math/calculus_of_variations
  - math/differential_equation
keywords:
  - first_variation_functional
topics:
  - variational_calculus
  - functional_analysis
name: First Variation of Functional
date of note: 2024-10-26
---

## Concept Definition

>[!important]
>**Name**: First Variation of Functional

>[!important] Definition
>Let $\Omega$ be an open domain in $\mathbb{R}^{n}$, and $u(x) \in X$ be a smooth function in $\Omega$, where $X$ is a subset in the *space of smooth functions* $\mathcal{C}^{\infty}(\Omega, \mathbb{R})$.  Let $u_{0}\in \mathcal{C}^{\infty}(\Omega)$ be a point in function space.
>
>Define a *functional* $J$ on $X$ as $$J(u) := \int_{\Omega} F(x, u(x), Du(x)) dx$$
>where $Du(x) = \left( \partial_{i}u \right)_{i=1\,{,}\ldots{,}\,n}$
>
>The **first variation** $\delta J$ at $u_{0}$ is defined as 
>$$
>\delta J(u_{0}, h) := \frac{d}{dt}\Big|_{t=0} J(u_{0} + t\,h) = \lim_{ t \to 0 } \frac{|J(u_{0} + t\,h) - J(u_{0})|}{t}
>$$
>where $h$ is any functions on $\Omega$ with *compact support*.



## Explanation


>[!important]
>The **first variation** of $J$ is also called the **Gateaux differential** of $J$

- [[Gateaux Derivative and Weak Derivative in Banach Space]]






-----------
##  Recommended Notes and References


- [[Variational Derivative of Functional]]
- [[Fréchet Derivative and Strong Derivative in Banach Space]]


- [[Banach Space]]
- [[Bounded Linear Functional]]
- [[Euler–Lagrange Equations]]
- [[Lagrangian Function in Mechanics]]
- [[Gradient Flow in Wasserstein Space]]

- [[Minimizing Curves in Riemannian Manifold]]


- [[Ordinary Differential Equations by Chicone]] pp 225
- [[Partial Differential Equations by Evans]] pp 441
- [[Calculus of Variations by Gelfand]]  pp 14