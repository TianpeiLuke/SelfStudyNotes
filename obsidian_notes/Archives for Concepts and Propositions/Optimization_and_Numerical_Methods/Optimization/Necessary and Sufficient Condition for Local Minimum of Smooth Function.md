---
tags:
  - concept
  - optimization/theory
  - optimization/convex_optimization
keywords:
  - necessary_condition_optimality
  - sufficient_condition_optimality
  - convex_function
topics:
  - optimization
name: Necessary and Sufficient Condition for Local Minimum of Smooth Function
date of note: 2024-06-29
---

## Concept Definition

>[!important]
>**Name**: Necessary and Sufficient Condition for Local Minimum of Smooth Function

### First-Order and Second-Order Necessary Condition

>[!important] Proposition
>Let $f: \mathbb{R}^n \to \mathbb{R}$ be *continuous differentiable* function in an open set $S \subset \mathbb{R}^n$ containing $x^{*}$.
>
>
>- **First-Order Necessary Condition**: If vector $x^{*}$ is an **unconstrained local minimum** of $f$  then 
>$$
>\nabla f(x^{*}) = 0.
>$$ 
>
>- **Second-Order Necessary Condition:**  If, in addition, $f$ is **twice continuously differentiable** within $S$, then
>$$
>\nabla^2 f(x^{*}) \succeq 0,
>$$

^da6d0c


- [[Gradient of Smooth Map]]
- [[Positive Semidefinite Transformation]]
- [[Nonlinear Programming by Bertsekas]] pp 13

>[!info] Proof
>Consider $g(t) = f(x^{*}+ t\,v)$. By definition of *local minimum*,  *directional derivative* along any  direction $v$
>$$
>D_{v}f(x^{*}) := \lim_{ t \to 0 } \frac{f(x^{*}+ t\,v) - f(x^{*})}{t} = \left\langle  v\,,\,\nabla f(x^{*})    \right\rangle \ge 0
>$$
>Thus, let $v := -v$
>$$
>\left\langle  -v\,,\,\nabla f(x^{*}) \right\rangle \ge 0 \implies \left\langle v\,,\,\nabla f(x^{*}) \right\rangle \le 0.
>$$
>Therefore $$\left\langle v\,,\,\nabla f(x^{*}) \right\rangle = 0.$$
>
>For second continuous differentiable $f$, use the Taylor expansion
>$$
>f(x^{*}+ t\,v) - f(x^{*}) = \left\langle  v\,,\, \nabla f(x^{*})     \right\rangle + \frac{t^2}{2} v^T \nabla^2 f(x^{*})\,v + o(t^2)
>$$
>Apply the first-order necessary condition, for any $v$,
>$$
>\lim_{ t \to 0 } \frac{f(x^{*}+ t\,v) - f(x^{*})}{t^2} = \frac{1}{2}v^T \nabla^2 f(x^{*})\,v + \lim_{ t \to 0 }\frac{o(t^2)}{t^2}  = \frac{1}{2}v^T \nabla^2 f(x^{*})\,v \ge 0.
>$$
>Therefore $\nabla^2 f(x^{*})$ is **positive semi-definite**.

- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]
- [[Tangent Space Definition and Development]]
- [[Positive Semidefinite Operator]]

### Convexity

>[!important] Proposition
>Let $f: \mathcal{X}\to \mathbb{R}$ be **convex** function in a **convex subset** $\mathcal{X} \subset \mathbb{R}^n$ containing $x^{*}$.
>
>
>- If vector $x^{*}$ is an **unconstrained local minimum** of $f$  then $x^{*}$ is  also an **unconstrained global minimum**.
>- If $f$ is **strictly convex**, then there exists **at most one** *global minimum*.
>
>- If $f$ is **convex** and $\mathcal{X}$ is open,  then
>$$
>\nabla f(x^{*}) = 0,
>$$
>is both **necessary** and **sufficient condition** for $x^{*} \in \mathcal{X}$ to be a *global minimum* of $f$.

- [[Convex Set]]
- [[Unconstrained Global Minimization]]
- [[Stationary Point and Singular Point of Smooth Function]]
- [[Convex Optimization Problem]]
- [[Nonlinear Programming by Bertsekas]] pp 14

### Sufficient Conditions

>[!important] Proposition
>Let $f: \mathbb{R}^n \to \mathbb{R}$ be *twice differentiable* function in an open set $\mathcal{S}$.
>
>Suppose a vector $x^{*}$ is a **stationary point** of $f$ i.e. $$\nabla f(x^{*}) = 0$$ and the **Hessian** of $f$ is **positive definite**
>$$
>\nabla^2 f(x^{*}) \succ 0,
>$$ 
>then $x^{*}$ is a **strict local minimum** of $f$.
>
>In particular, there exists some scalar $\lambda >0$ and $\epsilon >0$ such that 
>$$
>f(x) \ge f(x^{*}) + \frac{\lambda}{2}\lVert x - x^{*} \rVert^2, \quad \forall x\in B_{\epsilon}(x^{*}). 
>$$

- [[Positive Semidefinite Transformation]]
- [[Positive Semidefinite Operator]]
- [[Strongly Convex Function]]

## Explanation


## Functional Extension

- [[Necessary Condition for Relative Extremum of Functional]]




-----------
##  Recommended Notes and References

- [[Unconstrained Local Minimization]]
- [[Unconstrained Global Minimization]]
- [[Stationary Point and Singular Point of Smooth Function]]

- [[Karush-Kuhn-Tucker Optimality Condition]]

- [[Nonlinear Programming by Bertsekas]] pp 13 - 16
- [[Numerical Optimization by Nocedal]] pp 14 - 16, 325
