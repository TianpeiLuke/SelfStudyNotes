---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - mirror_descent_algorithm
topics:
  - optimization/algorithm
name: Mirror Descent Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Mirror Descent Algorithm

>[!important] Definition
>Consider the *convex optimization problem*
>$$
>\begin{align*}
> \min\; & f(x)\\
> \text{s.t. }& x \in \mathcal{X}
>\end{align*}
>$$
>where $f: \mathbb{R}^{n}\to \mathbb{R}$ is a *convex function*, and $\mathcal{X}$ is a *closed convex set*.
>
>The **mirror descent algorithm** solves the following problem at each iteration $k$
>$$
>x_{k+1} \in \arg\min_{x \in \mathcal{X}}\left\{ \ell(x; x_{k}) + D_{k}(x, x_{k}) \right\} 
>$$
>where
>-  $\ell(x;x_{0})$ is the **linearization** of $f$ at $x_{k}$ by *subgradients* $$\ell(x; x_{k}) := f(x_{k}) + \left\langle  g_{k}\,,\, x - x_{k}    \right\rangle, \quad g_{k} \in \partial f(x_{k})$$
>- $D_{k}: \mathbb{R}^n \times \mathbb{R}^n \to \mathbb{R}_{+}$ is a (nonquadratic) **proximal term** 

^1b2c18


- [[Bregman Divergence]]
- [[Proximal Gradient Algorithm]]
- [[Generalized Proximal Method]]
- [[Subdifferential of Convex Function]]
- [[Subgradient Methods]]
- [[Follow-The-Regularized-Leader Algorithm]]

## Explanation

>[!info]
>We can derive mirror descent from **proximal gradient** algorithm, 
>$$
>x_{k+1} \in \arg\min_{x \in \mathcal{X}}\left\{ \ell(x; x_{k}) + \frac{1}{2\alpha_{k}}\lVert x - x_{k} \rVert^2  \right\} 
>$$
>as
>$$
>\arg\min_{x}\left\{   \left\langle  \nabla f(x_{k})\,,\, x - x_{k} \right\rangle + \frac{1}{2\alpha_{k}}\lVert x - x_{k} \rVert^2 \right\}  = \arg\min_{x}\left\{  \frac{1}{2\alpha_{k}}\lVert x- x_{k} + \alpha_{k}\;\nabla f(x_{k}) \rVert^2 \right\}
>$$

- [[Proximal Gradient Algorithm]]

## Online Mirror Descent





-----------
##  Recommended Notes and References


- [[Bregman Projection]]
- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Convex Function]]
- [[Polyhedron and Polytope]]
- [[Strongly Convex Function]]

- [[Exponential Weights Algorithm as Mirror Descent]]
- [[Online Convex Optimization]]

- [[Generalized Proximal Method]]
- [[Gradient Descent Algorithm]]
- [[Approximation Method for Optimization]]

- [[Convex Optimization Algorithms by Bertsekas]] pp 382
- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]] pp 142
- [[Introduction to Online Convex Optimization by Hazan]] pp 77 - 81