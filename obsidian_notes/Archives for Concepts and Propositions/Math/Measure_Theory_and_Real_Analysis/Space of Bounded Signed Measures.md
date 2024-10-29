---
tags:
  - concept
  - math/measure_theory
  - math/functional_analysis
keywords:
  - bounded_finite_additive_signed_measure
topics:
  - measure_theory
  - functional_analysis
name: Space of Bounded Finitely Additive Signed Measure
date of note: 2024-06-20
---

## Concept Definition

>[!important]
>**Name**: Space of Bounded Finitely Additive Signed Measure

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F})$ be a *measurable space* and the set function $\nu : \mathscr{F} \to \mathbb{R}$ be **finitely additive**. For any $E \in \mathscr{F}$, the **total variation** of $\nu$ over $E$, $\lvert \nu \rvert(E)$ is given by 
>$$
>\lvert \nu \rvert\,(E) := \sup\left\{ \sum_{k=1}^{n}\lvert \nu\left(E_{k}\right) \rvert:\;\; \bigcup_{k=1}^{n}E_{k} \subseteq E   \right\} 
>$$
>We call $\nu$ a **bounded finitely additive signed measure** if $\lvert \nu \rvert (\mathcal{X}) < \infty.$ 
>
>We define the **total variation of** $\nu$ as $$\lVert \nu \rVert := \lvert \nu \rvert\,(\mathcal{X}).$$

^d5ec0e

- [[Finitely Additive Measure]]
- [[Jordan Decomposition Theorem and total variation measure]]
- [[Signed Measure]]
- [[Total Variation between Measures]]
- [[Total Variation of Function]]


>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F})$ be a *measurable space* and $\mathscr{F}$ be a **Boolean algebra**.
>
>The space of all **bounded finitely additive signed measures** $\nu$ is called the **BA space** and is denoted as  $\mathcal{BA}(\mathcal{X}, \mathscr{F})$, i.e.
>$$
> \mathcal{BA}(\mathcal{X}, \mathscr{F}) := \left\{ \nu \in {\mathbb{R}}^{\mathscr{F}}: \nu \text{ finitely additive and } \lvert \nu \rvert (\mathcal{X}) < \infty \right\}. 
>$$ 

^aaf5b8

- [[Boolean Algebra]]

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F})$ be a *measurable space* and $\mathscr{F}$ be a **$\sigma$-algebra**.
>
>The space of all **bounded countably additive signed measures** $\mu$ is called the **CA space** and is denoted as  $\mathcal{CA}(\mathcal{X}, \mathscr{F})$, i.e.
>$$
> \mathcal{CA}(\mathcal{X}, \mathscr{F}) := \left\{ \mu \in {\mathbb{R}}^{\mathscr{F}}: \mu \text{ countably additive and } \lvert \mu \rvert (\mathcal{X}) < \infty \right\}. 
>$$ 

- [[sigma Algebra]]
- [[Measure Space and Countably Additive Measure]]

>[!important] Definition
>Suppose $\mathcal{X}$ is a *locally compact Hausdorff (LCH) space*. Let  $(\mathcal{X}, \mathscr{F})$ be a *measurable space* and $\mathscr{F}$ be a **Borel $\sigma$-algebra**.
>
>The space of all **bounded Radon (regular Borel) signed measures** $\mu$ is called the **RCA space** and is denoted as  $\mathcal{RCA}(\mathcal{X}, \mathscr{F})$, i.e.
>$$
> \mathcal{RCA}(\mathcal{X}, \mathscr{F}) := \left\{ \mu \in {\mathbb{R}}^{\mathscr{F}}: \mu \text{ Radon measure and } \lvert \mu \rvert (\mathcal{X}) < \infty \right\}. 
>$$ 

^73c68c

- [[Locally Compact Hausdorff Space]]
- [[Inner Regularity]]
- [[Radon Measure]]


## Explanation


## Banach Space

>[!important]
>- The BA space $\mathcal{BA}(\mathcal{X}, \mathscr{F})$ is a **Banach space** with respect to the **total variation norm** $$\lVert \nu \rVert := |\nu|(\mathcal{X}).$$
>- The CA space $\mathcal{BA}(\mathcal{X}, \mathscr{F})$ is a **Banach space** and it is a **closed subspace** of BA space
>- The RCA space $\mathcal{RCA}(\mathcal{X}, \mathscr{F})$ is a **Banach space** and it is a **closed subspace** of CA space
>  
>We have  $$\mathcal{RCA}(\mathcal{X}) \subset \mathcal{CA}(\mathcal{X}) \subset \mathcal{BA}(\mathcal{X})$$

- [[Banach Space]]

## Dual Space

- [[Dual Normed Space of L-infinity Space]]
- [[L-infinite Space]]



-----------
##  Recommended Notes and References


- [[Kantorovitch Representation Theorem for Dual of L-infinity]]
- [[Dual Normed Space of L-infinity Space]]

- [[Jordan Decomposition Theorem and total variation measure]]
- [[Signed Measure]]

- [[Radon Measure]]

- [[Riesz-Markov Representation Theorem]]
- [[L-infinite Space]]

- [[Finitely Additive Measure]]
- [[Measure Space and Countably Additive Measure]]

- [[Real Analysis by Royden]] pp 404
- [Ba_space](https://en.wikipedia.org/wiki/Ba_space)