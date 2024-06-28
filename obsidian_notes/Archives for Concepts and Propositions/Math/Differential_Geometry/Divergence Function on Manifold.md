---
tags:
  - concept
  - math/information_theory
  - math/differential_geometry
keywords:
  - divergence_manifold
topics:
  - information_theory
  - differential_geometry
name: Divergence
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Divergence

>[!important] Definition
>Given a *differentiable manifold* $\mathcal{M}$ of dimension $n$, a **divergence** on $\mathcal{M}$ is a $C^{2}$-function $\mathbb{D}: \mathcal{M} \times \mathcal{M} \to [0, \infty)$  satisfying:
> 
>- **Non-Negativity**: $$\mathbb{D}\left( p \left\|\right. q \right)  \geq 0$$ for all $p,q\in \mathcal{M}$;
>- **Positivity**: $$\mathbb{D}\left( p \left\|\right. q \right) = 0$$ if and only if $p=q$;
>- At every point $p\in \mathcal{M}$,  $\mathbb{D}\left( p \left\|\right. p + dp \right)$  is a **positive-definite** *quadratic form* for *infinitesimal displacements* $dp$ from $p$. 
>
>The last property means that divergence defines an **inner product** on the *tangent space* $T_{p}\mathcal{M}$ for every $p\in \mathcal{M}$. Since $\mathbb{D}$ is $C^{2}$ on $\mathcal{M}$, this defines a *Riemannian metric* $g$ on $\mathcal{M}$.

- [[Tangent Space Definition and Development]]
- [[Riemannian Metric and Riemannian Manifold]]

## Explanation



## Properties





-----------
##  Recommended Notes and References

- [[Smooth Manifold]]
- [[Tangent Space Definition and Development]]

- [[Fisher Information]]

- [[f-Divergence]]
- [[Kullback-Leibler Divergence]]

- [[Concepts and Theorems for Riemannian Manifold]]