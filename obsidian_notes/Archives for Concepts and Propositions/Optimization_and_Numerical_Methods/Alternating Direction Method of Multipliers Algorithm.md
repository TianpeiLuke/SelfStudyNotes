---
tags:
  - concept
  - optimization/algorithm
keywords:
  - admm
  - alternating_direction_method_of_multipliers
topics:
  - optimization
name: Alternating Direction Method of Multipliers Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Alternating Direction Method of Multipliers Algorithm

![[Fenchel Duality Theorem#^0a9d58]]

>[!important] 
>Consider the following optimization problem under *Fenchel duality context*
>$$
>\begin{align*}
> \min & f_{1}(x) + f_{2}\left(Ax\right)\\
> \text{s.t. }& x \in \mathbb{R}^n
>\end{align*}
>$$
>where $A\in \mathbb{R}^{m \times n}$, $f_{1}: \mathbb{R}^n \to (-\infty, +\infty]$, and $f_{2}: \mathbb{R}^m \to (-\infty, +\infty]$ are **closed convex functions.**
>
>This problem can be converted to an **equivalent problem**
>$$
>\begin{align*}
> \min & f_{1}(x) + f_{2}\left(z\right)\\
> \text{s.t. }& Ax = z\\
> & x\in \mathbb{R}^n\\
> & z \in \mathbb{R}^m.
>\end{align*}
>$$
>
>The **augmented Lagrangian function** is defined as 
>$$
>L_{c}(x, z, \lambda) = f_{1}(x) + f_{2}(z) + \left\langle  \lambda\,,\, Ax - z    \right\rangle + \frac{c}{2}\lVert Ax - z \rVert_{2}^2 
>$$
>where $c$ is a *positive parameter*.
>
>The **Alternating Direction Method of Multipliers (ADMM)** algorithm, given the current iterates $(x_{k}, z_{k}, \lambda_{k}) \in  \mathbb{R}^n  \times \mathbb{R}^m \times \mathbb{R}^m$, generates a *new iterate* $(x_{k+1}, z_{k+1}, \lambda_{k+1}$ in the following steps:
>- **minimizing augmented Lagrangian w.r.t. $x$**: $$x_{k+1} \in \arg\min_{x \in \mathbb{R}^n} L_{c}(x, z_{k}, \lambda_{k})$$
>- **minimizing augmented Lagrangian w.r.t. $z$**: $$z_{k+1} \in \arg\min_{z \in \mathbb{R}^m} L_{c}(x_{k+1}, z, \lambda_{k})$$
>- **updating multipliers** $$\lambda_{k+1} = \lambda_{k} + c\,\left(A\,x_{k+1} - z_{k+1}\right) $$

- [[Augmented Lagrangian Algorithm]]
- [[Augmented Lagrangian Function]]
- [[Proximal Algorithm]]
- [[Proximal Gradient Algorithm]]
- [[Convex Function]]


## Explanation

>[!info]
>**ADMM** is seen as **block coordinate descent** on the *augmented Lagrangian function* with **dual ascent update** on multipliers.





-----------
##  Recommended Notes and References

- [[Fenchel Duality Theorem]]
- [[Methods of Lagrangian Multipliers]]

- [[Convex Optimization Algorithms by Bertsekas]] pp 280
- [[boydDistributedOptimizationStatistical2011]]