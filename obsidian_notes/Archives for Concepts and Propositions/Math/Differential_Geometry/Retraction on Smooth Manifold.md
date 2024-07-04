---
tags:
  - concept
  - math/differential_geometry
keywords:
  - retraction_smooth_manifold
topics:
  - differential_geometry
name: Retraction on Smooth Manifold
date of note: 2024-07-01
---

## Concept Definition

>[!important]
>**Name**: Retraction on Smooth Manifold

>[!important] Definition
>A **retraction** on *manifold* $\mathcal{M}$ is a *smooth map*:
>$$R: T\mathcal{M} \to \mathcal{M}: \quad (x, v) \mapsto R_{x}(v)$$ such that each curve $$\gamma(t) := R_{x}(tv)$$ satisfies $$\gamma(0) = x,\; \quad \gamma'(0) = v.$$

- [[Smooth Map]]
- [[Smooth Manifold]]
- [[Tangent Bundle]]

>[!info]
>It is also common to define *retractions* **without referring to curves.**

>[!important] Definition (axiom)
>A **retraction** on *manifold* $\mathcal{M}$ is a *smooth map*:
>$$R: T\mathcal{M} \to \mathcal{M}: \quad (x, v) \mapsto R_{x}(v)$$ such that 
>- $$R_{x}(0) = x,$$
>- $$dR_{x}(0): T_{x}\mathcal{M} \to T_{x}\mathcal{M}$$ is the **identity map**: $$dR_{x}(0)[v] = v.$$


## Explanation

>[!info]
>A **retraction map** $R_{x}(v)$ identifies the **where** a *particle* **arrives** on manifold $\mathcal{M}$  at $t=1$ that **starts at** $x$, with **initial velocity** $v$.

>[!info]
>The curve $\gamma$ **need not to stay on manifold** for all $t$


>[!info]
>A continuous map $\tau: \mathcal{X} \to A \subset \mathcal{X}$ is a **retraction** if 
>$$
> \tau \circ \iota = \text{Id}_{x} 
>$$
>where  the $\iota$ is a **canonical inclusion map.**
>$$\iota : A \xhookrightarrow{}  \mathcal{X} $$

- [[Canonical Inclusion]]

>[!important]
>A (**deformation**) **retraction** is a **homotopy**.

## Equivalence Class of Curves

![[Tangent Vector and Differential via Velocity of Smooth Curves#^673c21]]

![[Tangent Vector and Differential via Velocity of Smooth Curves#^de2033]]





-----------
##  Recommended Notes and References

- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Parameterized Curve on Manifold]]


- [[An Introduction to Optimization on Smooth Manifolds by Boumal]] pp 38