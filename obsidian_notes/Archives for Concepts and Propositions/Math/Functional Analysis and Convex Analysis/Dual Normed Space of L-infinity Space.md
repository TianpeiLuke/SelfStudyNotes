---
tags:
  - concept
  - math/functional_analysis
  - math/real_analysis
keywords:
  - Lp_space
  - dual_normed_space
topics:
  - functional_analysis
  - real_analysis
name: Dual Space of Lp Space
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Dual of $L^{\infty}$ Space

![[Kantorovitch Representation Theorem for Dual of L-infinity#^48270b]]


>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space and $\mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu)$ be the space of **bounded finitely additive signed measures** that are **absolutely continuous** with respect to $\mu$, i.e. 
>$$
>\mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu):= \left\{ \nu \in \mathbb{R}^{\mathscr{F}}: \nu \text{ is fintely additive and }|\nu|(\mathcal{X}) < \infty,\; \nu \ll \mu \right\} 
>$$
>
>Then the **dual normed space** of $L^{\infty}(\mathcal{X}, \mu)$ is *isometric isomorphic* to $\mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu)$
>$$
>\mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu) \simeq \left(L^{\infty}(\mathcal{X}, \mu)\right)^{*}
>$$

^e574fa

- [[Kantorovitch Representation Theorem for Dual of L-infinity]]
- [[Isometry and Isometric isomorphism]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Lp Space]]

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space. 
>
>If $\mu$ is a **$\sigma$-finite measure**, then the **dual space** of $L^{\infty}(\mathcal{X}, \mu)$ is *isometric isomorphic* to $L^1(\mathcal{X}, \mu)$.
>$$L^1(\mathcal{X}, \mu) \simeq \left(L^{\infty}(\mathcal{X}, \mu)\right)^{*}$$

- [[Finite and sigma-Finite Measure]]
- [[Dual Normed Space of Lp Space]]

## Explanation

>[!important]
>$$
>L^1(\mathcal{X},  \mu) \subset \left(L^1(\mathcal{X}, \mu)\right)^{* *} \equiv \left(L^{\infty}(\mathcal{X},  \mu)\right)
>$$
>
>This is isomorphic to the following relation
>$$
>\mathcal{CA}(\mathcal{X}, \mathscr{F})  \subset \mathcal{BA}(\mathcal{X}, \mathscr{F})
>$$





## Representation

- [[Kantorovitch Representation Theorem for Dual of L-infinity]]







-----------
##  Recommended Notes and References

- [[Jordan Decomposition Theorem and total variation measure]]
- [[Total Variation between Measures]]

- [[Dual Normed Space of Lp Space]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Vector Space over a Field]]
- [[Banach Space]]

- [[Absolutely Convergent Integration]]
- [[Measurable Function]]
- [[Measure Space and Countably Additive Measure]]


- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Real Analysis by Royden]] pp 404
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)