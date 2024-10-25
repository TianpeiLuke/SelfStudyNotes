---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
  - optimization/linear_optimization
keywords:
  - extended_monotropic_program
topics:
  - optimization
  - convex_analysis
name: Extended Monotropic Program
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Extended Monotropic Program

>[!important] 
>The **extended monotropic program (EMP)** solves the following *convex optimization*:
>$$
>\begin{align*}
> \min_{x}\;&\; \sum_{i=1}^{m}f_{i}(x_{i}) \\[5pt]
> \text{s.t. }\;&\; x \in \mathcal{S} \subset \mathbb{R}^{n_{1} \,{+}\ldots{+}\, n_{m}}
>\end{align*}
>$$
>where 
>- the optimization variable is *partitioned* into $m$ *blocks*  $$x = (x_{1}\,{,}\ldots{,}\,x_{m}), \quad x_{i}\in \mathbb{R}^{n_{i}}, \;i=1\,{,}\ldots{,}\,m$$
>- and each component $$f_{i}: \mathbb{R}^{n_{i}} \to (-\infty, +\infty]$$  is a *closed proper convex function*
>- and $S$ is a *linear subspace* of $\mathbb{R}^{n_{1} \,{+}\ldots{+}\, n_{m}}$.

- [[Convex Optimization Problem]]
- [[Convex Function]]
- [[Closed Convex Function and Closure Operation]]
- [[Proper Convex Function]]
- [[Linear Subspace]]

## Explanation

>[!info]
>Although the vectors $x_{1}\,{,}\ldots{,}\,x_{m}$ are *independent* in *objective function*, they are **coupled through** the **subspace constraint** $$(x_{1}\,{,}\ldots{,}\,x_{m}) \in \mathcal{S}$$

## Variants

>[!info] 
>We can convert the optimization problem with **additive objective function** into **EMP**
>$$
>\begin{align*}
> \min_{x}\;&\; \sum_{i=1}^{m}f_{i}(x) \\[5pt]
> \text{s.t. }\;&\; x \in \mathcal{X}
>\end{align*}
>$$
>We can introduce an **auxilary variable** as the $m$ copies of $x$  $$z = (z_{1}\,{,}\ldots{,}\,z_{m}), \quad z_{i} =x$$
>
>Then the optimization problem is equivalent to the following **EMP problem** 
>$$
>\begin{align*}
> \min_{x}\;&\; \sum_{i=1}^{m}f_{i}(z_{i}) \\[5pt]
> \text{s.t. }\;&\;(z_{1}\,{,}\ldots{,}\,z_{m}) \in \mathcal{S} = \left\{ (x \,{,}\ldots{,}\, x):\; x\in \mathcal{X} \right\} 
>\end{align*}
>$$


>[!info] 
>Consider the optimization problem with **additive regularization function** into **EMP**
>$$
>\begin{align*}
> \min_{x}\;&\; F(x) + \sum_{i=1}^{m}f_{i}(x_{i}) 
>\end{align*}
>$$
>where $x = (x_{1}\,{,}\ldots{,}\,x_{m}),$ and both $F$ and $f_{i}$ are *closed proper convex function*.
>- We can introduce an **auxilary variable** for $F$
>
>Then the optimization problem is equivalent to the following **EMP problem** 
>$$
>\begin{align*}
> \min_{x, z}\;&\; F(z) +  \sum_{i=1}^{m}f_{i}(x_{i}) \\[5pt]
> \text{s.t. }\;& (z, x)\in \mathcal{S}
>\end{align*}
>$$



## Example

### Network Optimization

>[!example]
>A classical example of EMP is a single commodity **network optimization problem**, where
>- $x_{i}$ represents the **(scalar) flow** of an arc of a directed graph 
>- and $S$ is the **circulation subspace** of the graph.
>  
>The **network optimization** is of the form
>$$
>\begin{align*}
> \min_{x}\;&\; \sum_{i=1}^{m}f_{i}(x_{i}) \\[5pt]
> \text{s.t. }\;&\; Ax = b
>\end{align*}
>$$
>where $f_{i}$ are all *linear* as $$f_{i}(x_{i}) = c_{i}x_{i}$$

- [[Network Flow Problem as Linear Optimization]]
- [[Maximum Flow Problem]]
- [[Minimum Cost Flow Problem]]

### LASSO and Basis Pursuit

>[!example]
>The **basis pursuit** problem or **basis pursuit linear program** is to solve the **$\ell_{1}$ norm minimization problem** with *affine equality constraint*
>$$
>\begin{align}
> \min_{\beta\in \mathbb{R}^{d}} &\; \sum_{i=1}^{d}\lvert \beta_{i} \rvert  \\[5pt]
>\text{s.t. }& X\beta = y 
>\end{align}
>$$

- [[LASSO and Sparsity-Induced Least Square]]





-----------
##  Recommended Notes and References


- [[Gradient Descent Algorithm]]

- [[Incremental Algorithm]]
- [[Incremental Gradient Algorithm]]
- [[Polyhedral Approximation for Optimization]]
- [[Polyhedron and Polytope]]



- [[Convex Optimization Algorithms by Bertsekas]] pp 197 - 201, 406