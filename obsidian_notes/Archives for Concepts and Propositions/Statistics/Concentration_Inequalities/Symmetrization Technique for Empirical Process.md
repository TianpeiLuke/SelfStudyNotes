---
tags:
  - concept
  - math/stochastic_process
  - statistics/concentration_inequality
  - machine_learning/theory
keywords:
  - symmetrization_empirical_process
topics:
  - stochastic_process
  - concentration_inequality
  - machine_learning_theory
name: Symmetrization Technique for Empirical Process
date of note: 2024-06-02
---

## Concept Definition

>[!important]
>**Name**: Symmetrization Technique for Empirical Process

>[!important] Definition
>The techinque that replaces the empirical process $$\left(\mathcal{P}_{n} - \mathcal{P}\right)f$$ by the **symmetrized version** $$\mathcal{P}_n^{\epsilon}f$$  is called **symmetrization**. 

>[!important]
>The idea is that, for *fixed* $(X_1 \,{,}\ldots{,}\, X_n)$, the **symmetrized empirical measure** $$\mathcal{P}_n^{\epsilon}f := \frac{1}{n}\sum_{i=1}^{n}\epsilon_i f(X_i)$$  is a **Rademacher process**, hence a **sub-Gaussian process**.

- [[Symmetrized Empirical Process]]
- [[Empirical Process and Empirical Measure]]
- [[Rademacher Process]]
- [[Sub-Gaussian Process]]


## Explanation





- [[Symmetrization Inequalities for Empirical Process]]
- [[Contraction Principle for Symmetrized Empirical Process]]
- [[Talagrand Contraction Principle]]
- [[Rademacher Complexity]]



-----------
##  Recommended Notes and References

- [[Rademacher Process]]
- [[Empirical Process and Empirical Measure]]


- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Understanding Machine Learning by Shalev-Shwartz]]