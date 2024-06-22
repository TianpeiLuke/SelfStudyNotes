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
	- [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]]
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
	- [[Space of Bounded Signed Measures]]
	- [[L-infinite Space]]

![[Kantorovitch Representation Theorem for Dual of L-infinity#^48270b]]

- [[Space of Bounded Signed Measures]]
- [[Kantorovitch Representation Theorem for Dual of L-infinity]]


>[!important]
>$$
>\begin{CD}
> \mathcal{M}(\mathcal{X}) @>\subset>> \mathcal{BA}(\mathcal{X})\\ 
>@VV*V  @VV* V\\ 
> \mathcal{C}_{0}(\mathcal{X}) @>\subset>> L^{\infty}(\mathcal{X}, \mu)
>\end{CD}
>$$ 


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

![[Riesz Representation Theorem#^8d0eaf]]


![[Lax-Milgram Lemma#^d7879a]]

- [[Lax-Milgram Lemma]]

![[Riesz Representation Theorem for Dual of Lp#^b582b1]]

- [[Lp Space]]
- [[Riesz Representation Theorem for Dual of Lp]]
- [[Dual Normed Space of Lp Space]]

>[!important]
>Using $\left\langle  f\,,\,g    \right\rangle_{L^1} := \int f\,g\,d\mu$, we have
>$$
>\Phi: f \mapsto \left\langle  \cdot\,,\, f   \right\rangle_{L^{1}(\mathcal{X}, \mu)}
>$$
>is an **isometric isomorphism** of $L^{q}(\mathcal{X}, \mu)$ onto $\left(L^{p}(\mathcal{X}, \mu)\right)^{*}.$


## Explanation

>[!important]
>The duality principles states that to study the **structure of a space**, it is sometimes easier to explore the **behavior of functions** that *act on this space exclusively*. 
>
>The role of functions is that of a **probing mechanism** and the act of function is close to act of **measurement** in physical world.
>
>The *characteristics* of a space is fully encoded in its **response** to *all possible probing* requests.



-----------
##  Recommended Notes and References



