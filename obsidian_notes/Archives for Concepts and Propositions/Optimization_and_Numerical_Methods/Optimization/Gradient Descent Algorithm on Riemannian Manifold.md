---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
  - deep_learning/algorithms
keywords:
  - gradient_descent_algorithm
  - smooth_manifold
  - gradient_descent_manifold
topics:
  - optimization
  - optimization/algorithm
name: Gradient Descent Algorithm on Riemannian Manifold
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Gradient Descent Algorithm

### Gradient Descent on Riemannian Manifold

>[!important] Definition
>Let $(\mathcal{M}, g)$ be a *Riemannian manifold* and $R: T\mathcal{M} \to \mathcal{M}$ is the *retraction map* on $\mathcal{M}$.
>
>The **gradient descent algorithm on Riemannian manifold $\mathcal{M}$** works as follows
>1. initiate at $x_{0} \in \mathcal{M}$
>2. for $k=0,1 \,{,}\ldots{,}\,$:
>	1. $$x_{k+1} = R_{x_{k}}\left(-\alpha_{k}\; \nabla f(x_{k})\right)$$
>		- the **step size** $\alpha_{k}>0$

- [[Retraction on Smooth Manifold]]
- [[Riemannian Metric and Riemannian Manifold]]
- [[Gradient of Smooth Map]]


## Explanation


## Gradient Flow on Smooth Manifold

>[!important]
>The **gradient descent** algorithm can be seen as *discretized* version of **gradient flow**
>$$
>\begin{align*}
>&- \alpha \nabla f(x_{k})  = x_{k+1} - x_{k} \\[5pt]
>&\implies -\alpha \nabla f(x(t))dt  = dx(t) \\[5pt]
>& \iff \frac{d}{dt} x(t) = -\alpha \nabla f(x(t))
>\end{align*}
>$$ 

- [[Gradient Flow on Smooth Manifold]]

## Gradient Descent on Euclidean Space


- [[Gradient Descent Algorithm]]
- [[Unconstrained Global Minimization]]
- [[Unconstrained Local Minimization]]
- [[Automatic Differentiation]]
- [[Gradient Flow in Euclidean Space]]


-----------
##  Recommended Notes and References

- [[Iterative Descent]]



- [[Vector Field on Manifold]]
- [[Differential as Covector Field]]
- [[Tangent Bundle]]
- [[Tangent Space Definition and Development]]
- [[Smooth Manifold]]


- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]] pp 22 - 86
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]] pp 57