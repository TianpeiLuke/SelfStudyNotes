---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
  - proximal_gradient_algorithm
keywords:
  - proximal_gradient_algorithm
topics:
  - optimization/algorithm
name: Proximal Gradient Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Proximal Gradient Algorithm

>[!important] Definition
>Consider the *convex optimization problem*
>$$
>\begin{align*}
> \min\; & f(x) + h\left(x\right)\\
> \text{s.t. }& x \in \mathbb{R}^n
>\end{align*}
>$$
>where
>- $h: \mathbb{R}^{n} \to \mathbb{R}$ is a *closed proper convex function*, and 
>- $f: \mathbb{R}^{n}\to \mathbb{R}$ is a *differentiable convex function*, and 
>- $f$ has *Lipschitz continuous gradient*, i.e. for some $L >0$, $$\lVert \nabla f(x) - \nabla f(y) \rVert \le L \lVert x - y \rVert, \;\; \forall x, y \in \mathbb{R}^n. $$
>  
>At each iteration $k$, the **proximal gradient algorithm** solves the following problem
>$$
>x_{k+1}  \in \arg\min_{x\in \mathbb{R}^n}\left\{ \ell(x; x_{k}) + h(x) + \frac{1}{2 \alpha_{k}}\;\lVert x - x_{k} \rVert^2 \right\} 
>$$
>where $\alpha_{k} >0$ is a scalar parameter, and $$\ell(y; x) := f(x) + \left\langle  \nabla f(x)\,,\, y -x   \right\rangle, \quad x, y \in \mathbb{R}^n$$ is the **first-order linear approximation** of $f$ at $x$.


- [[Strongly Convex Function]]
- [[Lipschitz Continuous Function]]
- [[Gradient Projection Method]]

## Explanation

>[!info]
>The **proximal gradient method** combines the **proximal algorithm** with **gradient projection algorithm**.
>- If $f$ is a **linear function**, then the proximal gradient method is *the proximal method*
>- If $h$ is an **indicator function** of a **closed convex set** $$h(x) = \chi_{\mathcal{X}}(x),$$ then we  have *gradient projection method.*

- [[Gradient Projection Method]]
- [[Proximal Algorithm]]
- [[Characteristic Function of Set]]


>[!quote]
>The method **exploits the structure** of problems where $f + h$ is **not suitable for proximal minimization**, while $h$ **alone** (plus a *linear function*) **is**. The resulting benefit is that we can *treat* as much as possible of the cost function with *proximal minimization*, which is more general (admits **non-differentiable** and/or *extended real-valued cost*) as well as more "**stable**" than the gradient method (it involves essentially no restriction on the *step-size* $\alpha$). A typical example is the case where $h$ is a **regularization** function such as the **$\ell_{1}$ norm**, for which the proximal iteration can be done in  essentially *closed form* by means of the **shrinkage operation**.
>
>-- [[Convex Optimization Algorithms by Bertsekas]] pp 330


## Two-Step Approach


>[!important] 
>One way to view the proximal gradient update is to decompose it into two steps
>- **Alternates gradient step** on $f$: $$z_{k} = x_{k} - \alpha_{k}\;\nabla f(x_{k})$$
>- **Proximal step** on $h$: $$x_{k+1} \in \arg\min_{x \in \mathbb{R}^{n}}\left\{ h(x) + \frac{1}{2\alpha_{k}}\lVert x- z_{k} \rVert^2 \right\} $$
>  
>That is, it can be viewed as the **method of alternates gradient steps** on $f$ **with proximal steps** on $h$

- [[Gradient Projection Method]]



-----------
##  Recommended Notes and References

- [[Approximation Method for Optimization]]
- [[Convex Optimization Problem]]
- [[Convex Function]]

- [[Convex Optimization Algorithms by Bertsekas]] pp 330