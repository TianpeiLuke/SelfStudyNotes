---
tags:
  - concept
  - math/probability
  - probabilistic_graphical_models/theory
keywords:
  - gaussian_measure
  - conditional_independence
  - independent
topics:
  - probability
name: Independence in Gaussian Distribution
date of note: 2024-07-25
---

## Concept Definition

>[!important]
>**Name**: Independence in Gaussian Distribution

![[Gaussian Random Vector#^a97326]]


>[!important] Theorem
>Let $(X_{1} \,{,}\ldots{,}\,X_{d})$ have a **joint normal distribution** $\mathcal{N}(\mu, \Sigma)$.
>
>Then $X_{i}$ and $X_{j}$ are **independent** *if and only if* $$\Sigma_{i,j} = 0.$$

## Conditional Independence in Gaussian 

>[!important] Theorem
>Let $X := (X_{1} \,{,}\ldots{,}\,X_{d})$ have a **joint normal distribution** $\mathcal{N}(\mu, \Sigma)$, and let $\Theta = \Sigma^{-1}$ be the **precision matrix**.
>
>Then $X_{i}$ and $X_{j}$ are **conditional independent** given $X - \left\{ X_{i}, X_{j} \right\}$ *if and only if* $$\Theta_{i,j} = 0.$$
>
>That is $$\mathcal{P} \vDash (X_{i} \perp X_{j} \,|\,\mathcal{X} - \left\{ X_{i}, X_{j} \right\})\; \iff \; \Theta_{i,j} = 0.$$

- [[Conditional Independence]]


## Explanation





-----------
##  Recommended Notes and References


- [[Conditional Independence]]
- [[Independence of Events]]
- [[Independent Random Variables]]



- [[Gaussian Random Vector]]
- [[Gaussian Measure]]
- [[Gaussian Graphical Model and Gaussian Markov Random Field]]

