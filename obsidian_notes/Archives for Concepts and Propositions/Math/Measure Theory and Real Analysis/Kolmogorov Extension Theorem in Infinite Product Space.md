---
tags:
  - concept
  - math/real_analysis
  - math/measure_theory
  - math/probability
  - math/topology
keywords:
  - kolmogorov_extension_theorem
topics:
  - measure_theory
  - real_analysis
  - probability
  - topology
name: Kolmogorov Extension Theorem
date of note: 2024-05-25
---

## Concept Definition

>[!important]
>**Name**: Kolmogorov Extension Theorem

>[!important] Kolmogorov Extension Theorem
>Let $((\mathcal{X}_{t},\mathscr{B}_{t}), \mathscr{T}_{t})_{t\in T}$ be a *family* of *measurable spaces* $(\mathcal{X}_{t},\mathscr{B}_{t})$, equipped with a *topology* $\mathscr{T}_{t}$. 
>
>For each **finite** $S \subset T$,  let $\mu_{S}$ be an **inner regular probability measure** on $\mathscr{B}_{S} := \prod_{t\in S}\mathscr{B}_{t}$ with the *product topology* $\mathscr{T}_{S} := \prod_{t\in S}\mathscr{T}_{t},$ obeying the **compatibility condition** $$\pi_{R \leftarrow S, *}(\mu_{S}) = \mu_{R}$$ whenever $R \subset S \subset T$ are two **nested finite subsets** of $T$. Here $$\pi_{R \leftarrow S}: \left(\prod_{t\in S}\mathcal{X}_{t}, \mathscr{B}_{S}\right) \to  \left(\prod_{t\in R}\mathcal{X}_{t}, \mathscr{B}_{R}\right)$$ is a **measurable canonical projection function,** and $\pi_{R \leftarrow S, *}(\mu_{S})$  is the *pushforward measure* of $\mu_{S}$ by $\pi_{R \leftarrow S}.$
>
>Then there exists a **unique probability measure** $\mu_{T}$ on $$\mathscr{B}_{T} := \prod_{t\in T}\mathscr{B}_{t}$$ with the property that $$\pi_{S, \#}(\mu_{T}) = \mu_{S}$$ for *all* **finite** $S \subset T$.

- [[Introduction to Measure Theory by Tao]]  pp 199
- [[Probability Space]]
- [[Inner Regularity]]
- [[Product sigma-Algebra]]
- [[Finite and sigma-Finite Measure]]
- [[Arbitrary Cartestian Products]]
- [[Canonical Projection]]
- [[Push-forward Measure and Push-forward Operator]]
- [[Tychonoff Theorem and Product of Compact Space]]
- [[Product Topology]]

- We rephrase the above theorem in concrete form

>[!important] Kolmogorov Extension Theorem (Kolmogorov Existence Theorem)
> 


- [[Probability and Measure by Billingsley]] pp 486

## Explanation

>[!important]
>The **Kolmogorov extension theorem** is a **fundamental tool** in the foundations of probability theory, as it allows one to construct a *probability space* to hold a variety of **random processes** $(X_{t})_{t\in T}$.

- [[Stochastic Process]]

>[!important]
>The **Kolmogorov extension theorem** can be used to rigorously construct a process for **Brownian motion**, known as the **Wiener process.**

- [[Brownian Motion Wiener Process]]

>[!important]
>The common use of *Kolmogorov extension theorem* is to construct product measure on **infinite product space.**

- [[Product Measure on Infinite Product Space]]

## Proof


- [[Axiom of Choice]]
- [[Heine-Borel Theorem on Compactness in Finite Dimension Space]]
- [[Hahn-Kolmogorov Extension of Pre-measure]]













-----------
##  Recommended Notes and References

- [[Probability Space]]
- [[Inner Regularity]]
- [[Product sigma-Algebra]]

- [[Product Topology]]
- [[Arbitrary Cartestian Products]]
- [[Canonical Projection]]
- [[Tychonoff Theorem and Product of Compact Space]]
- [[Hahn-Kolmogorov Extension of Pre-measure]]


- [[Finite and sigma-Finite Measure]]
- [[sigma Algebra]]
- [[Measure Space and Countably Additive Measure]]



- [[Introduction to Measure Theory by Tao]]  pp 199
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Probability and Measure by Billingsley]] pp 486
- [[A Probability Path by Resnick]]
