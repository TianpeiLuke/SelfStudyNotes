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
>**Name**:  Dual of $L^p$ Space

![[Riesz Representation Theorem for Dual of Lp#^b582b1]]


>[!important] Definition
> Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a **$\sigma$-finite measure space**, $1\le p < \infty$, and $q$ is **Hölder conjugate** to $p$, i.e. $$\frac{1}{p} + \frac{1}{q} = 1.$$
> 
> The **dual normed space** of  $L^{p}(\mathcal{X}, \mu)$ is *isometric isomorphic* to $L^q(\mathcal{X}, \mu)$
> $$
> L^{q}(\mathcal{X}, \mu) \simeq \left(L^{p}(\mathcal{X}, \mu)\right)^{*}.
> $$ 

^709202

- [[Finite and sigma-Finite Measure]]
- [[Riesz Representation Theorem for Dual of Lp]]
- [[Isometry and Isometric isomorphism]]
- [[Lp Space]]


## Explanation

>[!important]
>The condition on **$\sigma$-finiteness** of measure space is critical. 
>
>For instance, with **$\sigma$-finite** $(\mathcal{X}, \mathscr{F}, \mu)$,  
> $$
> L^{1}(\mathcal{X}, \mu) \simeq \left(L^{\infty}(\mathcal{X}, \mu)\right)^{*}.
> $$ 
> 
>But in general, without this additional assumption
>$$
>\mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu) \simeq \left(L^{\infty}(\mathcal{X}, \mu)\right)^{*}
>$$
>where $\mathcal{BFA}(\mathcal{X}, \mathscr{F}, \mu)$ is the space of **bounded finitely additive signed measures** that are **absolutely continuous** with respect to $\mu$,

- [[Space of Bounded Signed Measures]]
- [[Kantorovitch Representation Theorem for Dual of L-infinity]]



## Representation


- [[Riesz Representation Theorem for Dual of Lp]]


## Dual Space of $L^{\infty}$ 

- [[Kantorovitch Representation Theorem for Dual of L-infinity]]



-----------
##  Recommended Notes and References


- [[Isometry and Isometric isomorphism]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Lp Space]]
- [[Banach Space]]

- [[Riesz Representation Theorem for Dual of Lp]]
- [[Riesz Representation Theorem]]

- [[Finite and sigma-Finite Measure]]


- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Real Analysis by Royden]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)