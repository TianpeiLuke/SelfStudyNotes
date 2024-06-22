---
tags:
  - concept
  - math/real_analysis
  - math/functional_analysis
  - math/measure_theory
keywords:
  - riesz_representation_theorem
  - dual_normed_space
  - Lp_space
topics:
  - real_analysis
  - functional_analysis
  - measure_theory
name: Riesz Representation Theorem for Dual of Lp
date of note: 2024-06-20
---

## Concept Definition

>[!important]
>**Name**: Riesz Representation Theorem for Dual of $L^p$

>[!important] Riesz Representation Theorem ($L^p$ space)
> Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a **$\sigma$-finite measure space**, $1\le p < \infty$, and $q$ is **Hölder conjugate** to $p$, i.e. $$\frac{1}{p} + \frac{1}{q} = 1.$$
> 
> For $f\in L^{q}(\mathcal{X}, \mu)$, define $T_{f}: L^{p}(\mathcal{X}, \mu) \to \mathbb{R}$ as 
>$$
> T_{f}(g) := \int_{\mathcal{X}}\,f\,g\,d\mu, \quad \forall g\in L^{p}(\mathcal{X}, \mu).
>$$
>That is, $T_{f} \in \left(L^{p}(\mathcal{X}, \mu)\right)^{*}.$
>
>Then $$T: f \mapsto T_{f}$$ is an **isometric isomorphism** of $L^{q}(\mathcal{X}, \mu)$ onto $\left(L^{p}(\mathcal{X}, \mu)\right)^{*}.$

^b582b1

- [[Finite and sigma-Finite Measure]]
- [[Lp Space]]
- [[Dual Normed Space of Lp Space]]
- [[Hölder Inequality]]
- [[Isometry and Isometric isomorphism]]


## Explanation

>[!important]
>The condition on $(\mathcal{X}, \mathscr{F}, \mu)$ being a **$\sigma$-finite measure space** is critical. 


>[!important]
>Using $$\left\langle  f\,,\,g    \right\rangle_{L^1(\mathcal{X}, \mu)} := \int_{\mathcal{X}} f\,g\,d\mu,$$ we have
>$$
>\Phi: f \mapsto \left\langle  \cdot\,,\, f   \right\rangle_{L^{1}(\mathcal{X}, \mu)}
>$$
>is an **isometric isomorphism** of $L^{q}(\mathcal{X}, \mu)$ onto $\left(L^{p}(\mathcal{X}, \mu)\right)^{*}.$

>[!important] 
>For $p = 2$, we have [[Riesz Representation Theorem]] for **Hilbert space** $L^{2}(\mathcal{X}, \mu)$.
>
>Note that [[Riesz Representation Theorem]] applies to **any Hilbert space** which is broader than this theorem.

- [[Riesz Representation Theorem]]




-----------
##  Recommended Notes and References

- [[Lp Space]]
- [[Vitali Covering]]

- [[Uniform Integrable Family of Functions]]

- [[Real Analysis by Royden]]  pp 399