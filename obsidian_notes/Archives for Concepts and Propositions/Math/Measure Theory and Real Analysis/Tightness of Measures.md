---
tags:
  - concept
  - math/measure_theory
  - math/probability
  - math/functional_analysis
keywords:
  - tight_family_measures
topics:
  - measure_theory
  - probability
  - functional_analysis
name: Tightness of Measures
date of note: 2024-06-21
---

## Concept Definition

>[!important]
>**Name**: Tightness of Measures

>[!important] Definition
>Let $\mathcal{X}$ be a *Hausdorff space* and $\mathscr{F}$ be the *Borel $\sigma$-algebra* on $\mathcal{X}.$  
>
>A collection $\{ \mu_{n} \}$ of *(signed) Borel measures* defined on $\mathscr{F}$ is called **tight** (or **uniformly tight**) if, for any $\epsilon >0$, there exists some **compact subset** $C_{\epsilon} \subset \mathcal{X}$ such that *for all $n$*,
>$$
> |\mu_{n}|\left(\mathcal{X} \setminus C_{\epsilon}\right) < \epsilon
>$$
>where $|\mu_{n}|$ is the **total variation** of  $\mu_{n}$.


- [[Borel Measure]]
- [[Borel sigma Field]]
- [[Compactness]]
- [[Jordan Decomposition Theorem and total variation measure]]
- [[Space of Bounded Signed Measures]]
- [[Hausdorff Space]]

>[!important] Definition (Probability Measure)
>Let $\mathcal{X}$ be a *Hausdorff space* and $\mathscr{F}$ be the *Borel $\sigma$-algebra* on $\mathcal{X}.$  
>
>A collection $\{ \mu_{n} \}$ of **probability measures** defined on $\mathscr{F}$ is called **tight** (or **uniformly tight**) if, for any $\epsilon >0$, there exists some **compact subset** $C_{\epsilon} \subset \mathcal{X}$ such that *for all $n$*,
>$$
> \mu_{n}\left(C_{\epsilon}\right) > 1- \epsilon.
>$$


- [[Probability Space]]
- [[Probability and Measure by Billingsley]] pp 380



## Explanation

>[!important]
>**Tightness** is a generalization of **inner regularity** to a collection of measures.
>
>If there exists *only one measure* $\mu$ for a **tight sequence of measures**, this measure $\mu$ is **inner regular**.

- [[Inner Regularity]]


## Weak Convergence

>[!important] Theorem
>Let $(\Omega, \mathscr{F})$ be a Hausdorff measurable space. 
>
>If a collection $\{ \mu_{n} \}$ of **probability measures** defined on $\mathscr{F}$ is **tight**, then there exists a *subsequence* $$\{\mu_{n_{k}}\} \subset \{ \mu_{n} \}$$ and a **probability measure** $\mu$ on $\mathscr{F}$ such that 
>$$
>\mu_{n_{k}} \stackrel{d}{\longrightarrow} \mu.
>$$

- [[Probability and Measure by Billingsley]] pp 380
- [[Convergence in Distribution]]
- [[Helly Selection Theorem]]

## Metrizable Compact Space


>[!important]
>If $\mathcal{X}$ is a  **compact metrizable space**, then every collection of  *Borel measures* on $\mathcal{X}$ is **tight**.

- [[Metrizable Space]]
- [[Compactness]]
- [[Second Countablity]]





-----------
##  Recommended Notes and References

- [[Inner Regularity]]
- [[Tightness of Integrable Functions]]

- [[Convergence in Distribution]]
- [[Weak Convergence in Banach Space]]


- [[Gaussian Measure]]

- [[Jordan Decomposition Theorem and total variation measure]]
- [[Space of Bounded Signed Measures]]

- [[Borel Measure]]
- [[Borel sigma Field]]
- [[Hausdorff Space]]
- [[Topology of Set]]


- [[A Probability Path by Resnick]] pp 309
- [[Probability and Measure by Billingsley]] pp 380
- [[Lectures on Gaussian Processes by Lifshits]]


- Wikipedia [Tightness_of_measures](https://en.wikipedia.org/wiki/Tightness_of_measures)