---
tags:
  - entry_point
  - concept
  - math/functional_analysis
keywords:
  - duality
topics:
  - functional_analysis
name: Duality between Spaces
date of note: 2024-05-16
---

## Concept Definition

### Convex Duality

>[!important] Supporting Hyperplane Theorem
>If $x$ is *not an interior point* of a **convex set** $K$ which *contains interior points*, there is a **closed hyperplane** $H$ *containing* $x$ such that $K$ *lies on* **one side** of $H$.

>[!important]
>The **support functional** of a *convex set* $K$ **completely specifies the set** (to within *closure*}
>$$
> \begin{align*}
> \overline{K} &= \bigcap_{f \in X^{*}}\set{x: f(x) \leq h(f)}.
> \end{align*}
>$$ 
>where $h(f) := \sup_{x \in K}f(x).$


- [[Duality Correspondences of Convex Sets]]
	- [[Hahn-Banach Theorem Geometric Form]]
	- [[Minkowski Functional]]
	- [[Support functional of Convex Set]]
	- [[Supporting Hyperplane of Convex Set]]
	- [[Separation Theorem]]
	- [[Support functional of Convex Set]]


### Duality between Space of Radon Measures and Space of Continuous Functions with Compact Support

>[!important] Theorem
>Let $X$ be a *locally compact Hausdorff (LCH)* space,  $\mathcal{M}(X)$ be the space of **signed Radon measure** on $X$ and $\mathcal{C}_{0}(X)$ be the space of all continuous functions that *vanishes at infinity.* 
>
>For every signed Radon measure $\mu$, define a bounded linear functional on $\mathcal{C}_{0}(X)$, $I_{\mu}: \mathcal{C}_{0}(X) \to \mathbb{R}$ as
> $$
> \begin{align*}
> I_{\mu}(f) &= \int f d\mu. 
> \end{align*}
> $$
>
>Then the map 
>$$
>\mu \rightarrow I_{\mu}
>$$ 
>is an **isometric isomorphism** from $\mathcal{M}(X)$ to $(\mathcal{C}_{0}(X))^{*}$, i.e.
>$$\mathcal{M}(X) \simeq (\mathcal{C}_{0}(X))^{*} $$


- [[Duality of Measure and Functional of Continuous Functions]]
	- [[Borel Measure]]
	- [[Inner Regularity]]
	- [[Outer Regularity]]
	- [[Radon Measure]]
	- [[Summary of Spaces of Continuous Functions]]
	- [[Riesz-Markov Representation Theorem]]


### Self-Duality of Hilbert Space and its Linear Functionals

>[!important] Corollary
>The *canonical map* from $\mathcal{H}$ to its dual $\mathcal{H}^{*}$ 
>$$
>\Phi: x \mapsto \left\langle \cdot \,,\, x   \right\rangle
>$$
>is an **isometric isomorphism**.  That is,  a Hilbert space $\mathcal{H}$ is **isometric isomorphic** to its *dual* $\mathcal{H}^{*}$
>$$
>\mathcal{H} \simeq \mathcal{H}^{*}.
>$$

- [[Hilbert Space]]
- [[Riesz Representation Theorem]]



## Explanation

>[!important]
>The duality principles states that to study the **structure of a space**, it is sometimes easier to explore the **behavior of functions** that *act on this space exclusively*. 
>
>The role of functions is that of a **probing mechanism** and the act of function is close to act of **measurement** in physical world.
>
>The *characteristics* of a space is fully encoded in its **response** to *all possible probing* requests.



-----------
##  Recommended Notes and References

