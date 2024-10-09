---
tags:
  - concept
  - math/convex_analysis
  - optimization/theory
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - second_order_cone_programming
topics:
  - convex_analysis
  - optimization/algorithm
  - optimization/theory
name: Second-Order Cone Programming
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Second-Order Cone Programming

![[Quadratic Programming#^9ccf19]]

- [[Quadratic Programming]]

>[!important] Definition
>The **second-order cone programming (SOCP)** solves the following *convex optimization problem*
>$$
>\begin{align*}
> \min_{x\in \mathbb{R}^{n}} \;&\; \left\langle  f\,,\,x    \right\rangle \\[5pt]
> \text{s.t. }&\; \lVert A_{i}x + b_{i} \rVert_{2} \le \left\langle  c_{i}\,,\, x   \right\rangle + d_{i}, \quad i=1\,{,}\ldots{,}\,m\\[5pt]
> &\; Fx = g
>\end{align*}
>$$
>where $x\in \mathbb{R}^{n}$ is the *optimization variable* and
>- $A_{i}\in \mathbb{R}^{n_{i}\times n}$, $b_{i}\in \mathbb{R}^{n_{i}}$ for $i=1\,{,}\ldots{,}\,m$
>- $c_{i}\in \mathbb{R}^{n}$, and $d\in \mathbb{R}$
>- $F\in \mathbb{R}^{p\times n}$,  and $g\in \mathbb{R}^{p}$
>  
>The constraint of the form $$\lVert Ax + b_{i} \rVert_{2} \le \left\langle  c\,,\, x   \right\rangle + d$$ for $A\in \mathbb{R}^{k\times n}$ is called a **second-order cone constraint**.
>- This is the same as requiring $$[Ax + b\;, \;c^{T}x+d] \in \text{2nd-order cone}  \subseteq \mathbb{R}^{k+1}$$

- [[Convex Optimization Problem]]
- [[Cone Set]]
- [[Convex Cone Set]]


## Explanation





-----------
##  Recommended Notes and References


- [[Semidefinite Programming]]
- [[Positive Semidefinite Transformation]]
- [[Quadratic Programming]]

- [[Inverse Covariance Estimation]]

- [[Convex Function]]
- [[Determinant of Linear Transformation]]
- [[Trace of Positive Semi-Definite Operator]]



- [[Interior Point Method or Barrier Method for Convex Optimization]]



- [[Convex Optimization by Boyd]] pp 156 - 160
- [[Convex Optimization Algorithms by Bertsekas]] pp 17 - 22
- [[Nonlinear Programming by Bertsekas]]