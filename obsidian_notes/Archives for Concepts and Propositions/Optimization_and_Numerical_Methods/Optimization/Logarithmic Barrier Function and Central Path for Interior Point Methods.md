---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
  - math/convex_analysis
  - optimization/convex_optimization
keywords:
  - interior_point_method
  - logarithmic_barrier
  - barrier_method
topics:
  - optimization
name: Logarithmic Barrier Function and Central Path for Interior Point Methods
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Logarithmic Barrier Function and Central Path for Interior Point Methods

![[Convex Optimization Problem#^bc3f9c]]


>[!important] Definition
>Consider the *convex optimization problem*
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) \\
>\text{s.t.}\;& f_{i}(x) \leq 0, \quad i =1 \,{,}\ldots{,}\, m\\
>&Ax - b = 0
\end{align*}
>\;\; (P)
>$$
>where both the *objective function* $f_{0}$ and *inequality constraint functions* $f_{i}$ are **convex** and **twice continuously differentiable** functions and $A \in \mathbb{R}^{p \times n}$ is of **full rank** $\text{rank}(A) = p < n.$
>
>We can rewrite the optimization problem as
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) + \sum_{i=1}^{m}\delta_{-}\{ f_{i}(x)\}\\
>\text{s.t.}\;& Ax  = b
\end{align*}
>$$
>where 
>$$
>\delta_{-}(u) = \left\{\begin{array}{cc}
> 0 & u \le 0\\
> +\infty & u > 0
>\end{array}
>\right.
>$$
>
>The basic idea of the **barrier method** is to *approximate* the bifunction $\delta_{-}$ by the function
>$$
>\hat{\delta}_{-}(u) = -\left(\frac{1}{t}\right)\log\left(-u\right),\, \quad \text{where }\; \text{dom}(\hat{\delta}_{-}) = - \mathbb{R}_{++}, 
>$$
>and $t >0$ is a *parameter* that set the accuracy of the approximation. Moreover,
>- $\hat{\delta}_{-}$ is a *convex function* and *non-decreasing*.
>- $\hat{\delta}_{-} = \infty$ if $u >0$
>- $\hat{\delta}_{-}$ is *differentiable* and *closed*
>  
>Substituting the approximation  $\hat{\delta}_{-}$, the optimization problem becomes
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) - \frac{1}{t}\sum_{i=1}^{m}\log\left(-f_{i}(x)\right)\\
>\text{s.t.}\;& Ax  = b
\end{align*}
>$$  
>which is also a *convex optimization problem*. 

^8b91e9

>[!important] Definition
>The function 
>$$
>\phi(x) :=  -\sum_{i=1}^{m}\log\left(-f_{i}(x)\right), 
>$$
>with domain
>$$
>\text{dom }(\phi) := \{ x\in \mathcal{X}: f_{i}(x) <0, \; i=1 \,{,}\ldots{,}\,m \},
>$$
>is called the **logarithmic barrier** or **log barrier** for the convex optimization problem $(P)$

^779aa5

- [[Convex Optimization Problem]]
- [[Bifunction and Convex Bifunction]]
- [[Operations that Preserve Convexity]]

>[!info]
>The **domain** of log barrier function is the interior of inequality constraint set, where all of inequality constraints are *strict inequality* or *inactive*.


## Explanation





-----------
##  Recommended Notes and References


- [[Interior Point Method or Barrier Method for Convex Optimization]]
- [[Newton Method]]
- [[Secant Equation and Quasi-Newton Methods]]
- [[BFGS Algorithm]]



- [[Sequential Quadratic Programming]]
- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Convex Function]]
- [[Karush-Kuhn-Tucker Optimality Condition]]

- [[Convex Optimization by Boyd]] pp 561
- [[Numerical Optimization by Nocedal]] pp 563 - 594
- [[Nonlinear Programming by Bertsekas]] pp 446 - 473