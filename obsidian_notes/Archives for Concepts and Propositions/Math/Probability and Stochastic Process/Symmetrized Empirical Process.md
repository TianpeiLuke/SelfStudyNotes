---
tags:
  - concept
  - math/stochastic_process
  - statistics/concentration_inequality
  - machine_learning/theory
keywords:
  - symmetrized_empirical_process
topics:
  - stochastic_process
  - concentration_inequality
  - machine_learning_theory
name: Symmetrized Empirical Process
date of note: 2024-06-02
---

## Concept Definition

>[!important]
>**Name**: Symmetrized Empirical Process

>[!important] Definition
>Let $X_1 \,{,}\ldots{,}\, X_n$ be **independent** random variables on $\mathcal{X}$ and $\mathcal{F}$ be a class of *measurable functions* on $\mathcal{X}$. 
>
>Consider the **symmetrized process**
>$$
> \begin{align}
> f \to \mathcal{P}_n^{\epsilon}f := \frac{1}{n}\sum_{i=1}^{n}\epsilon_i f(X_i),  \quad  \forall f \in \mathcal{F}
> \end{align}
>$$  
>where 
>- $\epsilon := (\epsilon_1 \,{,}\ldots{,}\, \epsilon_n)$ are **independent Rademacher random variables** taking values in $\set{-1, +1}$ with *equal probability* and 
>- $\epsilon_i$'s are **independent from** $X  = (X_1 \,{,}\ldots{,}\, X_n)$. 

>[!important] Definition
>The **supremum norm** of **symmetrized process** is defined as
>$$
> \begin{align*}
> \lVert \mathcal{P}_{n}^{\epsilon} \rVert_{\mathcal{F}} := \sup_{f \in \mathcal{F}}\left| \frac{1}{n}\sum_{i=1}^{n}\epsilon_i f(X_i) \right|
> \end{align*}
>$$ 

- [[Rademacher Process]]
- [[Empirical Process and Empirical Measure]]


## Explanation







-----------
##  Recommended Notes and References

- [[Rademacher Process]]
- [[Empirical Process and Empirical Measure]]


- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Understanding Machine Learning by Shalev-Shwartz]]