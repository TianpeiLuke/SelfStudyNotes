---
tags:
  - concept
  - machine_learning/theory
  - math/stochastic_process
  - statistics/concentration_inequality
keywords:
  - rademacher_complexity
topics:
  - machine_learning_theory
  - stochastic_process
  - concentration_inequality
name: Rademacher Complexity
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Rademacher Complexity

>[!important] Definition
>Let $\epsilon := (\epsilon_n: n \ge 1)$ be a sequence of *independent Rademacher random variables* taking values in $\set{-1, +1}$ with *equal probability*. Let $T$ be the index space.
>
>For a collection of vectors $T\subset \mathbb{R}^n$, the **Rademacher complexity** of $T$ is defined as 
>$$
>\mathfrak{R}(T) := \mathbb{E}\left[ \sup_{t \in T}\left\{ \sum_{i=1}^{n}\epsilon_{i}t_{i} \right\}    \right] := \mathbb{E}\left[ \sup_{t\in T}\left\langle  t\,,\,\epsilon    \right\rangle  \right] 
>$$
>where $t := (t_1 \,{,}\ldots{,}\, t_n) \in T$.

^8eafb1


- [[Symmetrized Empirical Process]]
- [[Rademacher Process]]


## Explanation

>[!important] 
>For function class $\mathcal{F}$, the **Rademacher complexity** of $\mathcal{F}$ is defined as 
>$$
>\mathfrak{R}(\mathcal{F}) := \mathbb{E}_{\epsilon, \mathcal{P}}\left[ \sup_{f \in \mathcal{F}}\left\{ \sum_{i=1}^{n}\epsilon_{i}f(X_{i}) \right\}    \right] := \mathbb{E}_{\epsilon, \mathcal{P}}\left[ \sup_{f\in \mathcal{F}}\left\langle  f(X)\,,\,\epsilon    \right\rangle  \right] 
>$$

- [[Empirical Rademacher Complexity]]


## Inequalities


- [[Contraction Principle for Symmetrized Empirical Process]]
- [[Talagrand Contraction Principle]]
- [[Symmetrization Inequalities for Empirical Process]]



-----------
##  Recommended Notes and References


- [[Gaussian Complexity Gaussian Width]]

- [[Rademacher Process]]
- [[Empirical Process and Empirical Measure]]
- [[Contraction Principle for Symmetrized Empirical Process]]
- [[Symmetrized Empirical Process]]


- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]

- [[Concentration Inequalities by Boucheron]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[Foundations of Machine Learning by Mohri]] pp 34
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]