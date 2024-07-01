---
tags:
  - concept
  - math/differential_geometry
keywords:
  - tangent_vector
  - curve_on_manifold
  - velocity_curve
topics:
  - differential_geometry
name: Velocity of Smooth Curves
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Velocity of Smooth Curves

![[Parameterized Curve on Manifold#^fa255d]]

>[!important] Definition
>Let $\mathcal{M}$ be a *smooth manifold*.
>
>Given a *smooth curve* $\gamma: J \to \mathcal{M}$, and $t_{0} \in J$, we define the **velocity of $\gamma$ at $t_{0}$**, denoted by $\gamma'(t_{0})$, to be the vector 
>$$
>\gamma'(t_{0}) = d\gamma \left(\frac{d}{dt} \Big|_{t=t_{0}}\right) \in T_{\gamma(t_{0})}\mathcal{M},
>$$
>where $d / dt|_{t_{0}}$ is the *standard coordinate basis vector* in $T_{t_{0}}\mathbb{R}$

^da57a9

- [[Differential of a Smooth Map at Point]]
- [[Tangent Space as Finite Dimensional Vector Space]]

## Explanation


>[!info]
>Another notation of velocity as
>$$
>\dot{\gamma}(t_{0}), \quad \frac{d\gamma}{dt}(t_{0}), \quad \frac{d\gamma}{dt}\Big|_{t=t_{0}}  
>$$

## Derivation Operator

>[!important]
>A velocity of smooth curve is a **tangent vector**. Thus
>$$
>\gamma'(t_{0})\,f = d\gamma \left(\frac{d}{dt} \Big|_{t=t_{0}}\right) f = \frac{d}{dt} \Big|_{t=t_{0}} \left(f \circ \gamma \right) = \left(f \circ \gamma \right)'(t_{0}).
>$$
>
>In other word, $\gamma'(t_{0})$ is a **derivation** at $\gamma(t_{0})$ obtained by taking *derivative of a function along* $\gamma$.

- [[Derivation of Smooth Map at point and Tangent Vector]]
- [[Differential of a Smooth Map at Point]]


## Coordinate Representation

>[!important]
>Let $(U, \varphi)$ be a *smooth chart* with *coordinate functions* $(x^i)$. 
>
>If $\gamma(t_{0})\in U$, we can write the *coordinate representation of* $\gamma$ as $$\gamma(t) := \left(\gamma^1(t) \,{,}\ldots{,}\, \gamma^n(t)\right)$$ for $t$ sufficiently close to $t_{0}$.
>
>Then the **coordinate formula** for the differential yields
>$$
> \gamma'(t_{0}) = \frac{d\gamma^i}{dt}(t_{0})\;\frac{ \partial  }{ \partial x^i } \Big|_{\gamma(t_{0})} 
>$$
>where [[Einstein Summation Convention]] is used.

- [[Coordinate Representation of Differential]]
- [[Coordinate Representation of Tangent Vector]]
- [[Smooth Atlas]]
- [[Smooth Chart and Smooth Coordinate Map]]




-----------
##  Recommended Notes and References

- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Parameterized Curve on Manifold]]
- [[Smooth Manifold]]
- [[Tangent Space Definition and Development]]


- [[Introduction to Smooth Manifolds by Lee]]