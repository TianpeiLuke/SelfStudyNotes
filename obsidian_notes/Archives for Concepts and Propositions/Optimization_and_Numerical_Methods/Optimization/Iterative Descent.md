---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - iterative_descent
topics:
  - optimization/algorithm
name: Iterative Descent
date of note: 2024-07-01
---

## Concept Definition

>[!important]
>**Name**: Iterative Descent

>[!important] Definition
>Consider the *unconstrained  minimization problem* of a *continuous differentiable* function $f: \mathbb{R}^{n} \to \mathbb{R}$. 
>
>The **iterative descent** algorithm works as follows:
>1. start at initial point $x_{0}$:
>2. *generate* a sequence $x_{1}, x_{2} \,{,}\ldots{,}\,$  *successively*  such that $f$ *decreases* at each iteration; that is, $$f(x_{k+1}) \le f(x_{k}), \quad k=0 \,{,}\ldots{,}\,$$

^bc1c42




## Explanation

>[!important]
>**Iterative descent** is a **greedy algorithm** since it improve the objective function based on the current information only.


## Variants

- [[Gradient Descent Algorithm]]
- [[Newton Method]]
- [[Secant Equation and Quasi-Newton Methods]]
- [[BFGS Algorithm]]
- [[Conjugate Gradient Algorithm Linear]]
- [[Conjugate Gradient Algorithm Nonlinear]]

- [[Subgradient Methods]]
- [[Gradient Projection Method]]
- [[epsilon-Subgradient Methods]]

- [[Feasible Direction Method]]
- [[Block Coordinate Descent Algorithm]]



-----------
##  Recommended Notes and References

- [[Unconstrained Local Minimization]]

- [[Nonlinear Programming by Bertsekas]]
- [[Convex Optimization Algorithms by Bertsekas]] pp 54