---
tags:
  - concept
  - optimization/theory
  - algorithm/stochastic_search
  - algorithm/heuristic_search
  - nelder_mead_simplex_method
keywords:
  - nelder_mead_simplex_method
topics:
  - optimization/algorithm
  - heuristic_search
  - algorithm/search
name: Nelder–Mead Simplex Method
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: Nelder–Mead Simplex Method


### Algorithm

>[!important] Definition
>The **Nelder–Mead Simplex Method** is a heuristic optimization algorithm used to minimize a scalar-valued function of multiple real variables without requiring gradient information.
>
>- *Require*: an initial simplex formed by $n+1$ points in $\mathbb{R}^n$.
>- *Require*: an objective function $f: \mathbb{R}^n \to \mathbb{R}$ to be minimized.
>- **Initialize** the simplex vertices $\{x_1, \ldots, x_{n+1}\}$ and evaluate $f(x_i)$ for each vertex.
>- While not *convergence*:
>    - **Order** the vertices so that
>      $$
>      f(x_1) \leq f(x_2) \leq \cdots \leq f(x_{n+1}).
>      $$
>    - Compute the **centroid** of the best $n$ vertices:
>      $$
>      \bar{x} = \frac{1}{n} \sum_{i=1}^n x_i.
>      $$
>    - **Reflect** the worst point $x_{n+1}$ through the centroid:
>      $$
>      x_r = \bar{x} + \alpha (\bar{x} - x_{n+1}),
>      $$
>      where $\alpha > 0$ is the reflection coefficient.
>    - **Evaluate** $f(x_r)$ and decide the next step:
>        - If $f(x_1) \leq f(x_r) < f(x_n)$ (better than second worst), **accept reflection**: replace $x_{n+1}$ with $x_r$.
>        - If $f(x_r) < f(x_1)$ (best point), **expand**:
>          $$
>          x_e = \bar{x} + \gamma (x_r - \bar{x}),
>          $$
>          where $\gamma > 1$ is the expansion coefficient. Replace $x_{n+1}$ with $x_e$ if $f(x_e) < f(x_r)$; otherwise, keep $x_r$.
>        - If $f(x_r) \geq f(x_n)$ (worse point), **contract**:
>          - If $f(x_r) < f(x_{n+1})$ (better than worst), **outside contraction**:
>            $$
>            x_c = \bar{x} + \rho (x_r - \bar{x}),
>            $$
>          - Else **inside contraction**:
>            $$
>            x_c = \bar{x} - \rho (\bar{x} - x_{n+1}),
>            $$
>          where $0 < \rho < 0.5$ is the contraction coefficient.
>        - If contraction fails, **shrink** the simplex toward the best point:
>          $$
>          x_i \leftarrow x_1 + \sigma (x_i - x_1) \quad \text{for all } i=2,\ldots,n+1,
>          $$
>          where $0 < \sigma < 1$ is the shrinkage coefficient.
>- *Return*: the best point $x_1$ as the approximate minimizer.


## Explanation

| Step            | Operation                                | Purpose                |
| --------------- | ---------------------------------------- | ---------------------- |
| **Reflection**  | Probe outward away from worst point      | Explore new region     |
| **Expansion**   | Probe further if reflection is very good | Accelerate improvement |
| **Contraction** | Pull inward if reflection is bad         | Rescue poor moves      |
| **Shrink**      | Collapse simplex toward best point       | Reset when stuck       |




-----------
##  Recommended Notes and References



- [[Greedy Search and Hill Climbing]]
- [[Natural Evolutionary Strategies]]
- [[Evolutionary Computation Algorithms]]
- [[Derivative-Free Optimization]]

- [[Numerical Optimization by Nocedal]] pp 238
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 298 - 307
- [[Convex Optimization Algorithms by Bertsekas]] pp 83
- [[Nonlinear Programming by Bertsekas]] pp 162