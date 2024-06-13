---
tags:
  - concept
  - math/differential_geometry
keywords: 
topics:
  - differential_geometry
name: 
date of note: 2024-05-20
---

## Theorem

>[!important]
>**Name**: Divergence Theorem on Riemannian Manifold

>[!important] Lemma
>Let $(M, g)$ be an *oriented Riemannian manifold* with or without boundary. 
>
>Suppose $S \subset M$ is an **immersed hypersurface** with the *orientation* determined by a unit **normal vector field** $N$, and $\tilde{g}$ is the *induced metric* on $S$. 
>
>If $X$ is any *vector field along* $S$, then
>$$
>\iota^{*}\left( \beta(X) \right) = \left\langle X , N \right\rangle_{g}\; dV_{\tilde{g}}. 
>$$


- [[Normal Vector Fields of Submanifold]]
- [[Smooth Immersion]]
- [[Pullback of k-Form]]


>[!important] The Divergence Theorem
>Let $(M, g)$ be an *oriented Riemannian manifold* with boundary. 
>
>For any **compactly supported** *smooth vector field* $X$ on $M$
>$$
>\begin{align*}
>\int_{M} \left( \text{div }X \right)\; dV_{g} = \int_{\partial M}\left\langle X , N \right\rangle_{g}\;dV_{\tilde{g}}\,,
\end{align*}
>$$
 >where $N$ is the **outward-pointing** *unit* **normal vector field** along $\partial M$ and $\tilde{g}$ is the **induced Riemannian metric** on $\partial M$.

- [[Divergence of Vector Field on Riemannian Manifold]]
- [[Stokes Theorem]]


## Explanation


## Proof

>[!info]
>By definition of divergence [[Divergence of Vector Field on Riemannian Manifold]], 
>$$
>\int_{M} \left( \text{div }X \right)\; dV_{g} = \int_{M} d\left( X \mathbin{\lrcorner }\,dV_{g} \right)
>$$

>[!info]
>Then by [[Stokes Theorem]], and the Lemma above
>$$
>\begin{align*}
> \int_{M} d\left( X \mathbin{\lrcorner }\,dV_{g} \right) &=  \int_{\partial M} \iota^{*}\left( X \mathbin{\lrcorner }\,dV_{g} \right) \\
>&= \int_{\partial M} \iota^{*}\left( \beta(X) \right) \\
>&= \int_{\partial M} \left\langle X , N \right\rangle_{g}\; dV_{\tilde{g}}
\end{align*}
>$$
>Thus completes the proof. Q.E.D.



-----------
##  Recommended Notes and References

- [[Stokes Theorem]]
- [[Divergence of Vector Field on Riemannian Manifold]]

- [[Vector Field along Subset of Manifold]]
- [[Normal Space of Submanifold]]
- [[Riemannian Metric and Riemannian Manifold]]

- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]