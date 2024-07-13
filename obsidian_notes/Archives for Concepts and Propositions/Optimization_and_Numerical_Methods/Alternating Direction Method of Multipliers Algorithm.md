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

>[!important] Definition
>Consider the following optimization problem under *Fenchel duality context*
>$$
>\begin{align*}
> \min \;& f_{1}(x) + f_{2}\left(Ax\right)\\
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
>The **Alternating Direction Method of Multipliers (ADMM)** algorithm, given the current iterates $(x_{k}, z_{k}, \lambda_{k}) \in  \mathbb{R}^n  \times \mathbb{R}^m \times \mathbb{R}^m$, generates a *new iterate* $(x_{k+1}, z_{k+1}, \lambda_{k+1})$ in the following steps:
>- **minimizing augmented Lagrangian w.r.t. $x$**: $$x_{k+1} \in \arg\min_{x \in \mathbb{R}^n} L_{c}(x, z_{k}, \lambda_{k})$$
>- **minimizing augmented Lagrangian w.r.t. $z$**: $$z_{k+1} \in \arg\min_{z \in \mathbb{R}^m} L_{c}(x_{k+1}, z, \lambda_{k})$$
>- **updating multipliers** $$\lambda_{k+1} = \lambda_{k} + c\,\left(A\,x_{k+1} - z_{k+1}\right) $$


- [[Augmented Lagrangian Function]]
- [[Proximal Algorithm]]
- [[Proximal Gradient Algorithm]]
- [[Closed Convex Function and Closure Operation]]
- [[Convex Optimization Problem]]

## Explanation


>[!info]
>Recall that the *augmented Lagrangian method* solve the following problem:
>$$
>\begin{align*}
>  \min_{x \in \mathcal{X}}\;& f(x) \\
>  \text{s.t. }& Ax = b
>\end{align*}
>$$
>
>*ADMM* is seen as **augmented Lagrangian method** where the the *offset bias variable* $b$ of the linear equality constraint $b$ is also an *optimization variable*.
>$$
>\begin{align*}
>  \min_{x \in \mathcal{X}, \, b\in \mathbb{R}^{m}}\;& f(x) + g(b) \\
>  \text{s.t. }& Ax = b
>\end{align*}
>$$

- [[Augmented Lagrangian Algorithm]]

## Variants

>[!important] Definition
>Consider the following optimization problem
>$$
>\begin{align*}
> \min & f(x) + g\left(z\right)\\
> \text{s.t. }& Ax + Bz = c\\
> & x\in \mathbb{R}^n\\
> & z \in \mathbb{R}^p.
>\end{align*}
>$$
>where $A\in \mathbb{R}^{m \times n}$,  $B \in \mathbb{R}^{m \times p}$ $f: \mathbb{R}^n \to (-\infty, +\infty]$, and $g: \mathbb{R}^p \to (-\infty, +\infty]$ are **closed convex functions.**
>
>
>The **augmented Lagrangian function** is defined as 
>$$
>L_{c}(x, z, \lambda) = f(x) + g(z) + \left\langle  \lambda\,,\, Ax + Bz - c \right\rangle + \frac{c}{2}\lVert Ax + Bz - c \rVert_{2}^2 
>$$
>where $c$ is a *positive parameter*.
>
>The **Alternating Direction Method of Multipliers (ADMM)** algorithm, given the current iterates $(x_{k}, z_{k}, \lambda_{k}) \in  \mathbb{R}^n  \times \mathbb{R}^m \times \mathbb{R}^m$, generates a *new iterate* $(x_{k+1}, z_{k+1}, \lambda_{k+1})$ in the following steps:
>- **minimizing augmented Lagrangian w.r.t. $x$**: $$x_{k+1} \in \arg\min_{x \in \mathbb{R}^n} L_{c}(x, z_{k}, \lambda_{k})$$
>- **minimizing augmented Lagrangian w.r.t. $z$**: $$z_{k+1} \in \arg\min_{z \in \mathbb{R}^m} L_{c}(x_{k+1}, z, \lambda_{k})$$
>- **updating multipliers** $$\lambda_{k+1} = \lambda_{k} + c\,\left(A\,x_{k+1} + B z_{k+1} - c\right) $$

- [[Closed Convex Function and Closure Operation]]
### Dual Proximal Gradient 

![[Dual Proximal Gradient Algorithm#^627a6c]]

- [[Dual Proximal Gradient Algorithm]]

>[!info]
>It is interesting to note that this algorithm bears similarity to the **ADMM** for minimizing $$f_{1}(x)+ f_{2}(Ax)$$
>
>We can see that combining the gradient update formula for the intermediate value and the dual update formula
>$$
>\lambda_{k+1} = \lambda_{k} + \alpha_{k}\left(Ax_{k+1} - z_{k+1}\right)
>$$
>and
>$$
>x_{k+1} = \arg\min_{x} \left\{ f_{1}(x) + \left\langle  \lambda_{k}\,,\,Ax - z_{k} \right\rangle \right\} 
>$$
>With this, we can verify that the intermediate step $z_{k+1}$ minimizes the *augmented Lagrangian*
>$$
>z_{k+1} \in \arg\min_{z} \left\{ f_{2}(z) + \left\langle  \lambda_{k}\,,\, Ax_{k+1} - z \right\rangle + \frac{\alpha_{k}}{2}\lVert Ax_{k+1} - z\rVert^2  \right\} 
>$$
>
>Compare to ADMM, we have
>- $x_{k+1}$ is the *minimizer* of the *Lagrangian* not the *augmented Lagrangian*.
>- there is a **restriction on the magnitude of stepsize** due to Lipschitz constant  $L$ of the gradient of dual $\nabla f_{1}^{*}(-A\,\lambda)$. 
>
>ADMM can choose the *penalty parameter freely*, while the *augmented Lagrangian method* has *restrictions*.

>[!quote]
>Thus all three *proximal-type methods*, 
>- **proximal gradient**, 
>- **ADMM**, and 
>- **augmented Lagrangian**, 
>
>have *similarities*, and **relative strengths** and **weaknesses**. The choice between them hinges largely on the given problem's structure.
>
>-- [[Convex Optimization Algorithms by Bertsekas]] pp 337




-----------
##  Recommended Notes and References

- [[Fenchel Duality Theorem]]
- [[Lagrange Dual Problem]]
- [[Methods of Lagrangian Multipliers]]
- [[Approximation Method for Optimization]]


- [[Convex Optimization Algorithms by Bertsekas]] pp 280
- [[boydDistributedOptimizationStatistical2011]]