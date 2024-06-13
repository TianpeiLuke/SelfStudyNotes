---
tags:
  - concept
  - math/stochastic_process
  - statistics/concentration_inequality
  - machine_learning/theory
keywords:
  - rademacher_process
topics:
  - stochastic_process
  - concentration_inequality
  - machine_learning_theory
name: Rademacher Process
date of note: 2024-06-02
---

## Concept Definition

>[!important]
>**Name**: Rademacher Process

>[!important] Definition
>Let $\epsilon := (\epsilon_n: n \ge 1)$ be a sequence of **independent Rademacher random variables** taking values in $\set{-1, +1}$ with *equal probability*. 
>
>For a collection of vectors $T\subset \mathbb{R}^n$, the **Rademacher process** $(R_{t}, t\in T)$ indexed by $T$ is defined as
>$$ 
> \begin{align}
> R_{t} := \left\langle  \epsilon\,,\,t \right\rangle = \sum_{i=1}^{n}\epsilon_i\; t_{i}
> \end{align}
>$$  
>where $t := (t_1 \,{,}\ldots{,}\, t_n).$


- [[Empirical Process and Empirical Measure]]



## Explanation



## Symmetrized Empirical Process

- [[Symmetrized Empirical Process]]
- [[Symmetrization Inequalities for Empirical Process]]
- [[Talagrand Contraction Principle]]

## Rademacher Complexity

- [[Rademacher Complexity]]


-----------
##  Recommended Notes and References



- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Understanding Machine Learning by Shalev-Shwartz]]