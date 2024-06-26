---
tags:
  - concept
  - math/stochastic_process
  - math/probability
  - math/functional_analysis
  - statistics/concentration_inequality
  - machine_learning/theory
keywords:
  - vc_class
topics:
  - stochastic_process
  - concentration_inequality
  - probability
  - functional_analysis
  - machine_learning_theory
name: Vapnik-Chervonenkis Class
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: Vapnik-Chervonenkis Class


>[!important] Definition
>A collection of *functions* $\mathcal{F}$ is a **Vapnik-Cervonenkis class** ($\mathcal{F}$ is **$VC$**) if its *VC dimension* is *finite*. 
>
>That is, 
>$$\text{VC-dim}(\mathcal{F}) < \infty$$ 

- [[Restriction of Function Class to Data]]
- [[Shattering of Data by Function Class]]
- [[VC Dimension]]

>[!important] Definition (Set Family)
>A *family of sets* $\mathscr{F}$ is a **Vapnik-Cervonenkis class** ($\mathscr{F}$ is **$VC$**) if its *VC dimension* is *finite*. 
>
>That is, 
>$$\text{VC-dim}(\mathscr{F}) < \infty$$ 

- [[Intersection of Set Family to Set]]
- [[Shattering of Set by Set Family]]


## Explanation

>[!info]
>$$
>\text{VC-dim}(\mathcal{F}) < \infty \; \iff \; (\exists\, \mathcal{D} \subset \mathcal{X})\; \; \mathcal{F}_{\mathcal{D}} \subsetneq \{ 0, 1 \}^\mathcal{D}\, \land \, |\mathcal{D}| < \infty
>$$

- [[Restriction of Function Class to Data]]

>[!info]
>$$
>\text{VC-dim}(\mathscr{F}) < \infty \; \iff \; (\exists\, C)\; \; |\mathscr{F}\cap C| = 2^{|C|}  \, \land \, |C| < \infty
>$$

- [[Intersection of Set Family to Set]]

## Empirical Process as VC Class


- [[Concepts and Inequalities for Empirical Process]]
- [[Empirical Process and Empirical Measure]]
- [[Glivenko-Cantelli Class]]

>[!important]
>If a class of **boolean functions** $\mathcal{F}$ is a **Vapnik-Chervonenkis Class**, then $\mathcal{F}$ is **Glivenko-Cantelli class.**

- [[Glivenko-Cantelli Class]]





-----------
##  Recommended Notes and References

- [[Restriction of Function Class to Data]]
- [[Shattering of Data by Function Class]]
- [[VC Dimension]]


- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]