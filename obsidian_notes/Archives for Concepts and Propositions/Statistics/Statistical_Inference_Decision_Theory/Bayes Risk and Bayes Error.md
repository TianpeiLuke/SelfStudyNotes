---
tags:
  - concept
  - statistics/estimation
  - math/probability
  - machine_learning/theory
keywords:
  - bayes_risk
  - bayes_error
topics:
  - statistics/estimation
  - machine_learning_theory
name: Bayes Risk and Bayes Error
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Bayes Risk and Bayes Error

![[Statistical Decision Problem#^1e4cc1]]

![[Statistical Decision Problem#^e4b559]]

![[Statistical Decision Problem#^36cede]]


>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be a measurable space. The population $\mathcal{P} \in \mathscr{P}$. 
>
>Suppose the *family of distributions* $\mathscr{P}$  is a *measurable space* $(\mathscr{P}, \mathcal{F}_{\mathscr{P}})$ and $\Pi$ is a *probability measure* on $(\mathscr{P}, \mathcal{F}_{\mathscr{P}})$.
>
>The **Bayes risk** of a decision rule $T: \mathcal{X} \to \mathcal{A}$ with respect to $\Pi$ is defined as
>$$
>r_{T}(\Pi) = \int_{\mathscr{P}}\,R_{T}(\mathcal{P})\,d\Pi(\mathcal{P}).
>$$
>or
>$$
>r_{T}(\Pi) = \int_{\mathscr{P}}\,\int_{\Omega} L(\mathcal{P}, T(x))\,d\mathcal{P}_{X}(x)\,d\Pi(\mathcal{P}).
>$$



- [[Statistical Decision Problem]]
- [[Measure Space and Countably Additive Measure]]
- [[Probability Space]]


## Explanation






-----------
##  Recommended Notes and References


- [[Bayes Estimator]]
- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 12o