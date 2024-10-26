---
tags:
  - concept
  - optimization
keywords:
  - stationary_point
  - singular_point
topics:
  - optimization
name: Stationary Point and Singular Point of Smooth Function
date of note: 2024-06-29
---

## Concept Definition

>[!important]
>**Name**: Stationary Point and Singular Point of Smooth Function

![[Necessary and Sufficient Condition for Local Minimum of Smooth Function#^da6d0c]]

>[!important] Definition
>Let $f: \mathbb{R}^n \to \mathbb{R}$ be *continuous differentiable* function.
>
>If vector $x^{*}$ is called a **stationary point** if and only if 
>$$
>\nabla f(x^{*}) = 0.
>$$ 

- [[Gradient of Smooth Map]]
- [[Nonlinear Programming by Bertsekas]] pp 6
- [[Tangent Space Definition and Development]]

>[!important] Definition
>Let $f: \mathbb{R}^n \to \mathbb{R}$ be *twice continuous differentiable* function.
>
>If vector $x^{*}$ is called a **singular point** of $f$ if 
>- $x^{*}$ is a *local minimum* of $f$; and 
>- $x^{*}$  does *not* satisfies the *first order* and *second order necessary conditions*. That is
>$$
>\nabla f(x^{*}) \neq 0, \quad \text{ and } \quad \nabla^2 f(x^{*}) \text{ is not positive definite.}
>$$ 
>
>A local minima that is not singular is a **non-singular point** of $f$.

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]
- [[Positive Semidefinite Operator]]

### Smooth Manifold

>[!important] Definition
>Let $\mathcal{M}$ be a **smooth manifold**.
>
>A point $x\in \mathcal{M}$ is a **critical** or **stationary point** for a *smooth map* $f: \mathcal{M} \to \mathbb{R}$ if
>$$
> \frac{d}{dt}\Big|_{t = 0} \left(f \circ \gamma \right) \ge 0
>$$
>for any *curve*  $\gamma: J \to \mathcal{M}$ on $\mathcal{M}$ where $J \subset \mathbb{R}$ is an interval and $\gamma(0) = x.$


- [[Smooth Map between Euclidean Spaces]]
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]] pp 55

## Explanation

>[!info]
>If $x^{*}$ is a **local minimum** of $f$, then $x^{*}$ is a **stationary point.**

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]


-----------
##  Recommended Notes and References


- [[Unconstrained Local Minimization]]
- [[Unconstrained Global Minimization]]

- [[Nonlinear Programming by Bertsekas]] pp 4