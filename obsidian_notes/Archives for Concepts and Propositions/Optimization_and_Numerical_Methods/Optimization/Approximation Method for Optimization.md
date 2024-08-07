---
tags:
  - concept
  - optimization/algorithm
keywords:
  - approximation_optimization_method
topics:
  - optimization
  - optimization/algorithm
name: Approximation Method
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Approximation Method for Optimization

![[Iterative Descent#^bc1c42]]

>[!important] Definition
>Consider the *unconstrained  minimization problem* of a function $f: \mathbb{R}^{n} \to \mathbb{R}$ over a set $\mathcal{X}$.
>
>The **approximation method**  works as follows:
>1. start at initial point $x_{0}$:
>2. *generate* a sequence $x_{1}, x_{2} \,{,}\ldots{,}\,$  *successively*  such that at each iteration $k$, $x_{k+1}$ solves an **approximation** to *original optimization problem*, i.e.,
>  $$
>  x_{k+1} \in \arg\min_{x \in \mathcal{X}_{k}}\;F_{k}(x),
> $$
> where $F_{k}$ is a function that *approximates* $f$ and $\mathcal{X}_{k}$ is a set that *approximate* $\mathcal{X}.$ Both objective function and feasible region at each iteration may depend on the prior iterates $\{x_{j}, j\le k\}$ and other parameters. 

^9a898b


## Explanation

>[!quote]
>The **key ideas** here are that *minimization of $F_{k}$ over $\mathcal{X}_{k}$* should be **easier** than minimization of $f$ over $\mathcal{X}$, and that $\mathcal{X}_{k}$ should be a good *starting point* for obtaining $\mathcal{X}_{k+1}$ via some (possibly special purpose) method. Of course, the approximation of $f$ by $F_{k}$ and / or $\mathcal{X}$  by $\mathcal{X}_{k}$ should **improve** as $k$ *increases*, and there should be some **convergence guarantees** as $k \to \infty$.
> -- [[Convex Optimization Algorithms by Bertsekas]] pp 55

## Variants

### Linearization

>[!important]
>- **Outer Linearization**, i.e. **cutting plane method**: approximate the *objective function* via the *supporting hyperplane* for the *epigraph* [[Cutting Plane Methods and Outer Linearization]]
>- **Inner Linearization**, i.e. **simplicial decomposition**: approximate the *feasible region* via generalized simplex, i.e. the *convex hull* of *finite extreme points* [[Inner Linearization Methods and Simplicial Decomposition]]

### Proximal Approximation

>[!important]
>Use previous iterates or the gradient descent point as proximity point
>- [[Proximal Algorithm]] $$
>x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{ f(x) + \frac{1}{2c_{k}}\;\lVert x - x_{k} \rVert^2 \right\} 
>$$
>- [[Dual Proximal Algorithm]]: solving the Lagrangian **dual problem** of the proximal problem $$\lambda_{k+1} \in \arg\min_{\lambda \in \mathbb{R}^{n}} \left\{  f^{*}(\lambda) - \left\langle  \lambda\,,\, x_{k} \right\rangle + \frac{c_{k}}{2}\lVert \lambda \rVert^2 \right\} $$
>- [[Proximal Gradient Algorithm]]: choose proximity based on result of *one-step gradient descent* $z_{k}$, $$x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{ f(x) + \frac{1}{2c_{k}}\;\lVert x - z_{k} \rVert^2 \right\}$$
>- [[Dual Proximal Gradient Algorithm]]: solve the **Fenchel dual problem** with *proximal gradient*, and during the proximity step use *one-step gradient descent* on dual $\bar{\lambda}_{k}$ $$z_{k+1} \in \arg\min_{z \in \mathbb{R}^{n}}\left\{ f_{2}(z) - \langle  \bar{\lambda}_{k}\,,\,z \rangle + \frac{\alpha_{k}}{2}\lVert z \rVert^2  \right\} $$ and $\lambda_{k+1} = \bar{\lambda}_{k} - \alpha_{k}\,z_{k+1}.$
>- [[Augmented Lagrangian Algorithm]]: contains *equality constraint*, solve the *dual problem* with *dual proximal algorithm*. Results in a two-step update $$\begin{align*}x_{k+1} \in \arg\min_{x \in \mathcal{X}}L_{c_{k}}(x, \lambda_{k})\\ \lambda_{k+1} = \lambda_{k} + c_{k}\left(Ax_{k+1} - b\right)\end{align*}$$
>- [[Alternating Direction Method of Multipliers Algorithm]]: contains *equality constraint*, solve **Fenchel dual problem** using *dual proximal algorithm* Results in a two-step update $$\begin{align*} (x_{k+1}, z_{k+1}) \in \arg\min_{x \in \mathcal{X},\, z\in \mathbb{R}^{p}}L_{c_{k}}(x, z, \lambda_{k})\\ \lambda_{k+1} = \lambda_{k} + c\,\left(A\,x_{k+1} - z_{k+1}\right)\end{align*}$$
>- [[Generalized Proximal Method]]: replace the quadratic function with *general regularization term* $$
>x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{ f(x) + D(x, x_{k}) \right\} 
>$$
>- [[Mirror Descent Algorithm]]: replace $f$ with its *linearization* $\ell(\cdot; x_{k})$,  and replace the quadratic term with *general regularization term* $$
>x_{k+1} \in \arg\min_{x \in \mathcal{X}}\left\{ \ell(x; x_{k}) + D_{k}(x, x_{k}) \right\} 
>$$

### Block Coordinate Descent

>[!important]
>- [[Block Coordinate Descent Algorithm]]: *partition* the optimization variables into groups, *fixed all but one block* of optimization variables, and *cyclically* iterative solving  $$x_{k+1}^{i} \in \arg\min_{\xi \in \mathcal{X}_{i}}f\left(x_{k+1}^{1} \,{,}\ldots{,}\,x_{k+1}^{i-1},\,\xi,\, x_{k+1}^{i+1} \,{,}\ldots{,}\,x_{k+1}^{m}  \right)$$



-----------
##  Recommended Notes and References

- [[Iterative Descent]]



- [[Convex Optimization Algorithms by Bertsekas]] pp 63