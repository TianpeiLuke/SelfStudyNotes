---
tags:
  - concept
  - math/differential_geometry
  - math/riemannian_geometry
keywords:
  - exponential_map
  - geodesic_curve
  - riemannian_manifold
topics:
  - differential_geometry
  - riemannian_geometry
name: Exponential Map via Geodesic on Riemannian Manifold
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Exponential Map via Geodesic on Riemannian Manifold

>[!important] Definition
>Let $(\mathcal{M}, g)$ be a *Riemannian* or *pseudo-Riemannian manifold*, endowed with its *Levi-Civita connection* $\nabla$.
>
>For each initial point $p\in \mathcal{M}$, and each initial velocity vector $v\in T_{p}\mathcal{M}$, denote $$\gamma_{v}: J \to \mathcal{M}$$ as the *unique maximal geodesic* on $M$.
>
>
>-  Define the **domain** of the **exponential map** as a subset of tangent bundle $\mathcal{E} \subseteq  T\mathcal{M}$, given by 
>$$
> \begin{align*}
> \mathcal{E} := \left\{ v \in T\mathcal{M}: \gamma_v\text{ is defined on an interval containing [0,1]} \right\} ,
> \end{align*}
>$$ 
>- Define the **exponential map** $$\exp: \mathcal{E} \rightarrow \mathcal{M}$$ by $$  \begin{align*} \exp(v)  &= \gamma_{v}(1)\end{align*}$$ 
>- For each $p \in \mathcal{M}$, the **restricted exponential map** at $p$, denoted by $\exp_p$, is the *restriction* of $\exp$ to the set $$\mathcal{E}_p = \mathcal{E} \cap T_{p}\mathcal{M}.$$

- [[Tangent Bundle]]
- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Levi Civita Connection and Riemannian Connection]]
- [[Maximal Geodesic and Geodesic Segment]]
- [[Geodesic on Manifolds]]
- [[Riemannian Metric and Riemannian Manifold]]


## Explanation


![[exp_map.png]]



## Exponential Map on Lie Group

![[Exponential Map of Lie Group and Matrix Lie Group#^c127f2]]

- [[Exponential Map of Lie Group and Matrix Lie Group]]
- [[Lie Group]]
- [[Lie Algebra as Vector Space with Lie Bracket]]

![[Exponential Map of Lie Group and Matrix Lie Group#^910d1c]]

- [[Matrix Exponential]]

![[Covariant Derivative from Parallel Transport#^6bab4a]]

- [[Covariant Derivative from Parallel Transport]]
- [[Lie Derivative of Vector Field]]


-----------
##  Recommended Notes and References


- [[Maximal Integral Curve of Vector Field]]
- [[Parameterized Curve on Manifold]]
- [[Parallel Transport of Tensor Field along Curve]]

- [[Retraction on Smooth Manifold]]




- [[Introduction to Riemannian Manifolds by Lee]] pp 127 - 131
- [[Introduction to Smooth Manifolds by Lee]] pp 518 - 519