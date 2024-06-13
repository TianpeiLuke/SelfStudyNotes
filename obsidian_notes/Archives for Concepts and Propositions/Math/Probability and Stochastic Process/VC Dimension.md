---
tags:
  - concept
  - math/stochastic_process
  - machine_learning/theory
  - statistics/concentration_inequality
keywords:
  - vc_dimension
topics:
  - machine_learning_theory
  - stochastic_process
  - concentration_inequality
name: VC Dimension
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Vapnik-Chervonenkis (VC) Dimension


>[!important] Definition
>The **Vapnik-Chervonenkis (VC) dimension** of a function class $\mathcal{F}$, denoted $\text{VC-dim}(\mathcal{F})$ or simply $V(\mathcal{F})$, is the *maximal size* of a set $\mathcal{D} \subset \mathcal{X}$ that can *be shattered by* $\mathcal{F}$.
>
>$$
>\text{VC-dim}(\mathcal{F}) := \sup\left\{ |\mathcal{D}|: \mathcal{F}_{\mathcal{D}} = \{ 0 , 1\}^{\mathcal{D}}, \quad \forall \mathcal{D} \subset \mathcal{X}    \right\} 
>$$
>

- [[Shattering of Data by Function Class]]
- [[Restriction of Function Class to Data]]


>[!info]
>Recall that shattering means that *either the data is too small*, or *the model is too rich*. We do not like either the case.


>[!important]
> If $\mathcal{F}$ can **shatter** sets of **arbitrarily large size** we say that $\mathcal{F}$ has **infinite VC-dimension**.

>[!important] Definition (Set Family)
>The **Vapnik-Chervonenkis (VC) dimension** of a set family $\mathscr{F}$, denoted $\text{VC-dim}(\mathscr{F})$ or simply $V(\mathscr{F})$, is the *maximal size* of a set $C$ that can *be shattered by* $\mathscr{F}$.
>$$
>\text{VC-dim}(\mathscr{F}) := \sup\left\{ |C|: |\mathscr{F} \cap C| = 2^{|C|}  \right\} 
>$$

- [[Shattering of Set by Set Family]]
- [[Intersection of Set Family to Set]]


## Explanation

>[!important]
>The **VC Dimension** measures the **richness** of *the function class* from the perspective of binary representation. 


>[!important]
>The idea of VC dimension is to find the **shortest encoding length** of $\mathcal{F}$ in order to distinguish data.



-----------
##  Recommended Notes and References

- [[Shattering of Data by Function Class]]
- [[Restriction of Function Class to Data]]


- [[Empirical Risk Minimization]]

- [[PAC Learnable]]
- [[Bounded Difference Inequality]]
- [[Understanding Machine Learning by Shalev-Shwartz]]

- [[Empirical Process and Empirical Measure]]