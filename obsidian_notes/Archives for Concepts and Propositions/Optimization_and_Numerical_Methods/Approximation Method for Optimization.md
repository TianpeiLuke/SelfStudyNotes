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




-----------
##  Recommended Notes and References

- [[Iterative Descent]]



- [[Convex Optimization Algorithms by Bertsekas]] pp 63