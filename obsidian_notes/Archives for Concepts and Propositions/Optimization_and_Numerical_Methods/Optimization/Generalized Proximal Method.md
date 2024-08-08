---
tags:
  - concept
  - optimization/algorithm
keywords:
  - generalized_proximal_method
topics:
  - optimization
name: Generalized Proximal Method
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Generalized Proximal Method

![[Proximal Algorithm#^258191]]

>[!important] Definition
>Consider **non-convex** *optimization* problem
>$$
>\min_{x \in \mathbb{R}^{n}} f(x)
>$$
>where $f: \mathbb{R}^{n} \to (-\infty, \infty]$.
>
>The **generalized proximal algorithm** solves the following problem at each iteration $k$
>$$
> x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{ f(x) + D_{k}(x, x_{k}) \right\} 
>$$
>where $D_{k}: \mathbb{R}^{n} \times \mathbb{R}^n \to (-\infty, +\infty]$ is a **regularization term**.

- [[Proximal Algorithm]]
- [[Regularization in Optimization]]
- [[Follow-The-Regularized-Leader Algorithm]]

## Explanation

>[!quote]
>We may also consider in principle the application of the approach to a **nonconvex cost function** $f$ as well. Its *behavior*, however, in this case may be **complicated** and/or **unreliable**, as indicated in Fig. 6.6.4. An  important question is **whether the minimum** in the proximal iteration (6.148) is **attained** *for all* $k$; if $f$ is not assumed convex, this is not automatically guaranteed, even if $D_{k}$ is *quadratic*. ... To simplify the presentation, we will implicitly assume the *attainment of the minimum* throughout our discussion; it is guaranteed for example if $f$ is *closed proper convex*, and $D_{k}(\cdot, x_{k})$ is *closed and coercive* (satisfies $D_{k}(x,x_{k}) \to \infty$ as $\lVert x \rVert \to \infty$), and its *effective  domain* intersects with $\text{dom}(f)$ for all $k$ (cf. Prop. 3.2.3 in Appendix B).
>
>-- [[Convex Optimization Algorithms by Bertsekas]] pp 385


## Stabilization Property



## Variants

- [[Entropy Minimization Algorithm]]
- [[Bregman Distance Minimization]]
- [[Majorization-Minimization Algorithm]]
- [[Mirror Descent Algorithm]]


-----------
##  Recommended Notes and References

- [[Gradient Descent Algorithm]]


- [[Convex Optimization Algorithms by Bertsekas]] pp 382