---
tags:
  - concept
  - math/probability
  - math/stochastic_process
keywords:
  - gaussian_process
topics:
  - probability
  - stochastic_process
name: Gaussian Process
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Gaussian Process

>[!important] Definition
>Let $T$ be a *metric space*. 
>
>A *stochastic process* $(X_t)_{t \in T}$ is a **Gaussian process** *indexed by* $T$ if for *any finite collection* $\set{t_1 \,{,}\ldots{,}\, t_n} \subset T$, the vector $$(X_{t_1} \,{,}\ldots{,}\, X_{t_n})$$ has a **jointly Gaussian distribution**.


- [[Stochastic Process]]
- [[Finite Dimensional Distribution of Stochastic Process]]
- [[Gaussian Random Vector]]
- [[Gaussian Measure]]
- [[Product Measure on Infinite Product Space]]


>[!info]
>The **existence** of such Gaussian measure $\mathcal{N}$ on $\mathcal{X}^T$ is guaranteed by [[Kolmogorov Extension Theorem in Infinite Product Space]]. 

- [[Product Measure on Infinite Product Space]]



## Explanation

>[!important] Alternative Definition
>A *Gaussian process __indexed__ by $T$* is a **Gaussian random function** on *metric domain* $T \subset \mathbb{R}^d$.
>
>That is, it is a Gaussian random element $X: \Omega \to \mathcal{C}(T)$ such that
>$$
>X_{t}(\omega) := X(\cdot, \omega) \in \mathcal{C}(T)
>$$
>and for any $I \in \mathcal{C}(T)^{*}$,
>$$
>I(X(\cdot, \omega)) \sim \mathcal{N}
>$$

- [[Gaussian Random Function]]
- [[Representation of Gaussian Random Function in Hilbert Space]]

- [[Random Element and Random Variable]]
- [[Canonical Dual Pairing]]
- [[Dual Normed Space and Dual Banach Space]]





-----------
##  Recommended Notes and References

- [[Gaussian Random Vector]]
- [[Gaussian Measure]]
- [[Stochastic Process]]

- [[Gaussian Random Function]]
- [[Representation of Gaussian Random Function in Hilbert Space]]



- [[Probabilistic Graphical Models]]