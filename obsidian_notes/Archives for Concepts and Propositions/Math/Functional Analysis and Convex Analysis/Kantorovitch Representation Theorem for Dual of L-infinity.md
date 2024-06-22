---
tags:
  - concept
  - math/real_analysis
  - math/functional_analysis
  - math/measure_theory
keywords:
  - kantorovitch_representation
  - dual_l_infinity
topics:
  - real_analysis
  - functional_analysis
  - measure_theory
name: Kantorovitch Representation Theorem for Dual of L-infinity
date of note: 2024-06-20
---

## Concept Definition

>[!important]
>**Name**: Kantorovitch Representation Theorem for Dual of L-infinity

>[!important] Kantorovitch Representation Theorem
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space and $\mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu)$ be the space of **bounded finitely additive signed measures** that are **absolutely continuous** with respect to $\mu$, i.e. 
>$$
>\mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu):= \left\{ \nu \in \mathbb{R}^{\mathscr{F}}: \nu \text{ is fintely additive and }|\nu|(\mathcal{X}) < \infty,\; \nu \ll \mu \right\} 
>$$
>
>For $\nu \in \mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu)$, define $$T_{\nu}: L^{\infty}(\mathcal{X}, \mu) \to \mathbb{R}$$ by $$T_{\nu}(f) := \int_{\mathcal{X}}f\,d\nu$$ for all $f \in L^{\infty}(\mathcal{X}, \mu)$.
>
>Then the map $$T: \nu \mapsto T_{\nu}$$ is an **isometric isomorphism** of normed vector space $\mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu)$ onto the **dual** of $L^{\infty}(\mathcal{X}, \mu)$. That is,
>$$
>\mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu) \simeq \left(L^{\infty}(\mathcal{X}, \mu)\right)^{*}
>$$

^48270b

- [[Dual Normed Space of L-infinity Space]]
- [[Dual Normed Space of Lp Space]]
- [[Isometry and Isometric isomorphism]]
- [[Space of Bounded Signed Measures]]
- [[Absolute Continuity for Measures]]

## Explanation

>[!important]
>**Kantorovitch Representation Theorem** is based on  the following **inequality**
>$$
>\left\lvert \int_{\mathcal{X}} f \; d\nu \right\rvert \le \lVert \nu \rVert_{TV}\; \lVert f \rVert_{\infty}   
>$$ 
>for all $f\in L^{\infty}(\mathcal{X},\mu)$ and $\nu \in \mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu)$ with total variation norm $$\lVert \nu \rVert_{TV} = \lvert \nu \rvert (\mathcal{X}).$$

>[!important]
>Kantorovitch Representation Theorem provides a similar dual mapping as the [[Riesz-Markov Representation Theorem]]


>[!important]
>Kantorovitch Representation Theorem reduces to [[Riesz Representation Theorem for Dual of Lp]] when the measure $\mu$ is **$\sigma$-finite**, i.e.
>$$
>\mu\left(\mathcal{X}\right) = \sum_{i=1}^{\infty}\mu\left(E_{i}\right)
>$$
>where $$\mu\left(E_{i}\right) < \infty.$$


-----------
##  Recommended Notes and References

- [[Lp Space]]
- [[L-infinite Space]]

- [[Space of Functions with Bounded Variation]]
- [[Total Variation of Function]]


- [[Real Analysis by Royden]]  pp 399