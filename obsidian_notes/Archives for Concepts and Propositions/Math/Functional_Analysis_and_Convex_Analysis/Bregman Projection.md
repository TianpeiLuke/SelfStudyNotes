---
tags:
  - concept
  - math/information_theory
  - math/functional_analysis
keywords:
  - bregman_projection
topics:
  - information_theory
  - functional_analysis
name: Bregman Projection
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Bregman Projection

>[!info] 
>Let $f: \mathcal{X} \to \mathbb{R}$ be a *continuous differentiable* and *strictly convex* function defined on a *convex set* $\mathcal{X}$
>
>The **Bregman divergence** associated with $f$ for points $\boldsymbol{x}, \boldsymbol{y} \in \mathcal{X}$  is defined as 
>$$
>\mathbb{D}_{f}\left( \boldsymbol{x} \left\|\right. \boldsymbol{y}\right) = f(\boldsymbol{x}) - f(\boldsymbol{y}) - \left\langle  \nabla f(\boldsymbol{y})\,,\,  \boldsymbol{x} - \boldsymbol{y} \right\rangle  
>$$

>[!important] Definition
>Let $\mathcal{X}$ be a *convex* set and $W \subset \mathcal{X}$ be a subspace of $\mathcal{X}$ and $f: \mathcal{X} \to \mathbb{R}$ be a *continuous differentiable* and *strictly convex* function on $\mathcal{X}$. 
>
>Suppose that $W$ is *convex*. Then the following optimization problem has *a unique solution* (if it exists)
>$$
> \inf_{\boldsymbol{w} \in W}\mathbb{D}_{f}\left( \boldsymbol{w} \left\|\right. \boldsymbol{x} \right),
>$$
>where $\mathbb{D}_{f}\left( \boldsymbol{x} \left\|\right. \boldsymbol{y}\right)$ is the *Bregman divergence*.
>
>The unique solution is called **the Bregman projection** of $\boldsymbol{x}$ onto the subset $W$.

- [[Bregman Divergence]]
- [[Convex Set]]


## Explanation



## Properties












-----------
##  Recommended Notes and References

- [[Pythagorean Theorem and Parallelogram Law]]
- [[Bregman Divergence]]

- Wikipedia [Bregman divergence](https://en.wikipedia.org/wiki/Bregman_divergence)
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]