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
>Let $\Omega$ be a *bounded open domain* in $\mathbb{R}^{n}$, and $u(x) \in X$ be a vector-valued  *smooth function* in $\Omega$, where $X$ is a subset in the *space of smooth functions* $\mathcal{C}^{1}(\Omega, \mathbb{R}^{m})$.  Let $u_{0}\in \mathcal{C}^{1}(\Omega)$ be a point in function space. 
>
>Moreover, define $$F: C \subset \mathbb{R}^{n}\times \mathbb{R}^{m}\times \mathbb{R}^{n\times m} \to \mathbb{R}$$ as a *real-valued $\mathcal{C}^{1}$-smooth function* on an open set of $\mathbb{R}^{n}\times \mathbb{R}^{m}\times \mathbb{R}^{n\times m}$
>- Then there exists some $\delta >0$ such that $$F(x, v(x), Dv(x))$$ is defined in all $x\in \bar{\Omega}$, and for all $v\in \mathcal{C}^{1}(\bar{\Omega}, \mathbb{R}^{m})$ with $\lVert v - u \rVert_{\mathcal{C}^{1}(\Omega)} < \delta$
>
>Define a *functional* $J$ on $X$ as $$J(u) := \int_{\Omega} F(x, u(x), Du(x)) dx$$
>where $Du(x) = \left( \partial_{i}u^{j} \right)_{i,j}$ is the *Jacobian matrix*.
>
>The **first variation** $\delta J$ at $u_{0}$ *in direction of* $h$ is defined as 
>$$
>\delta J(u_{0}, h) := \frac{d}{dt}\Big|_{t=0} J(u_{0} + t\,h) = \lim_{ t \to 0 } \frac{|J(u_{0} + t\,h) - J(u_{0})|}{t}
>$$
>where 
>- $h\in \mathcal{C}_{c}^{1}(\Omega, \mathbb{R}^{m})$ is any functions on $\Omega$ with *compact support* and
>- $|\epsilon| < \epsilon_{0}$ with $$0 < \epsilon_{0} \le \frac{\delta}{\lVert h \rVert_{\mathcal{C}^{1}(\Omega)} }$$

^d58f5c

- [[Smooth Map between Euclidean Spaces]]
- [[Coordinate Representation of Differential at Point]]


## Explanation


>[!important]
>The **first variation** of $J$ is also called the **Gateaux differential** of $J$

- [[Gateaux Derivative and Weak Derivative in Banach Space]]


![[Variational Derivative of Functional#^60b0b8]]

>[!important]
>Based on variational derivative formula, 
>$$
>\delta J(u_{0}, h) := \int_{\Omega}\left\{ \frac{ \partial F}{ \partial u}(x, u_{0}, \nabla u_{0}) - \text{div}\left( \frac{ \partial F }{ \partial  \nabla u }  \right)(x, u_{0}, \nabla u_{0}) \right\}h(x)\,dx 
>$$


- [[Euler–Lagrange Equations]]
- [[Variational Derivative of Functional]]




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
- [[Optimization by Vector Space Methods by Luenberger]] pp 171