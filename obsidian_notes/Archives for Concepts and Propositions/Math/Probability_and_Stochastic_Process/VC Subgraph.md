---
tags:
  - concept
  - math/stochastic_process
  - math/probability
  - math/functional_analysis
  - statistics/concentration_inequality
  - machine_learning/theory
keywords: 
topics:
  - stochastic_process
  - concentration_inequality
  - probability
  - functional_analysis
  - machine_learning_theory
name: VC Graph
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: VC Subgraph

![[Hypograph or Subgraph of Function#^8d272c]]

>[!important] Definition
>A class of functions $\mathcal{F}$ is **VC subgraph** if the class of *subgraphs* $\text{hyp}(f)$ for $f\in \mathcal{F}$, 
>$$\mathscr{F} = \set{\text{hyp}(f) : f \in \mathcal{F}},$$
> is *VC class*.

- [[Hypograph or Subgraph of Function]]
- [[Vapnik-Chervonenkis Class]]
- [[Intersection of Set Family to Set]]
- [[Shattering of Set by Set Family]]
- [[VC Dimension]]


## Explanation

>[!info]
>$$
>\mathcal{F} \text{ has VC Subgraph } \; \iff \; (\exists\, C)\; \; |\mathscr{F}\cap C| = 2^{|C|}  \, \land \, |C| < \infty
>$$






-----------
##  Recommended Notes and References

- [[Hypograph or Subgraph of Function]]
- [[Vapnik-Chervonenkis Class]]
- [[Intersection of Set Family to Set]]
- [[Shattering of Set by Set Family]]
- [[VC Dimension]]


- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]