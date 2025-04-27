---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
  - coordinate_descent_algorithm
  - block_coordinate_descent_algorithm
  - COD
keywords:
  - coordinate_descent_algorithm
  - block_coordinate_descent_algorithm
topics:
  - optimization/algorithm
name: Block Coordinate Descent Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Block Coordinate Descent Algorithm

>[!important] Definition
>Consider the *convex optimization problem*
>$$
>\begin{align*}
> \min \;& f(x) \\
> \text{ s.t. }& x \in \mathcal{X}
>\end{align*}
>$$
>where $f: \mathbb{R}^{n} \to \mathbb{R}$ is a *differentiable convex function* and $\mathcal{X}$ is the *Cartesian product* of *closed convex sets* $$\mathcal{X} = \prod_{i=1}^{m}\mathcal{X}_{i}$$ where $\mathcal{X}_{i} \subset \mathbb{R}^{n_{i}}$ is *closed convex* subset. We partition the vector $x\in \mathbb{R}$ as $$x = [x^{1} \,{,}\ldots{,}\, x^{m}]$$ where $x^i \in \mathcal{X}_{i}.$
>
>The  **block coordinate descent algorithm** is defined as follows: Given the current iterate $x_{k} = (x_{k}^1 \,{,}\ldots{,}\, x_{k}^{m}),$ we generate iterate $x_{k+1} = (x_{k+1}^1 \,{,}\ldots{,}\, x_{k+1}^{m}),$ by iterating over each blocks. That is, at iteration $k$
>  
>- For $i=1 \,{,}\ldots{,}\,m$:
>  $$
>  x_{k+1}^{i} \in \arg\min_{\xi \in \mathcal{X}_{i}}f\left(x_{k+1}^{1} \,{,}\ldots{,}\,x_{k+1}^{i-1},\,\xi,\, x_{k+1}^{i+1} \,{,}\ldots{,}\,x_{k+1}^{m}  \right)
> $$
>where we assume that the *preceding minimization* has *at least one optimal solution.*
>
>Thus, at each iteration, the cost is minimized *with respect to each of the block components* $x^i$, taken in **cyclic order**, with each minimization incorporating the results of the *preceding minimizations*.

- [[Convex Optimization Problem]]
- [[Closed Convex Function and Closure Operation]]
- [[Proper Convex Function]]

## Explanation

>[!quote]
>Similar to the *proximal gradient* and *incremental methods* of the  preceding two sections, the **idea** is to **split** *the optimization process* into a **sequence of simpler optimizations**, with the motivation to **exploit the  special structure** of the problem. In the **block coordinate descent method**, however, the simpler optimizations revolve around the **components** $x^i$ **of** $x$, rather than the *components* of $f$ or the *components* of $\mathcal{X}$, as in the *proximal gradient* and the *incremental methods.*
>
>-- [[Convex Optimization Algorithms by Bertsekas]] pp 370

- [[Approximation Method for Optimization]]
- [[Proximal Gradient Algorithm]]\
- [[Incremental Algorithm]]

- [[k-d Tree Structure for ANN Search]]


-----------
##  Recommended Notes and References

- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Arbitrary Cartestian Products]]

- [[Gibbs Sampling]]
- [[Mean Field Approximation for PGM]]

- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]
- [[Convex Optimization Algorithms by Bertsekas]] pp 71, 369