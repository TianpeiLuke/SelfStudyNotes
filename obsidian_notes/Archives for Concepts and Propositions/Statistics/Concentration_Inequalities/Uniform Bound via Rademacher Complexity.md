---
tags:
  - concept
  - statistics/concentration_inequality
  - machine_learning/theory
  - math/stochastic_process
keywords:
  - rademacher_complexity
  - bounded_difference_inequality
topics:
  - concentration_inequality
name: Uniform Bound via Rademacher Complexity
date of note: 2024-07-30
---

## Concept Definition

>[!important]
>**Name**: Uniform Bound via Rademacher Complexity

>[!important] Proposition
>Let $\mathcal{G}$ be a family of functions mapping from $\mathcal{Z}$ to $[0, 1]$. Then, for any $\delta > 0$,  **with probability at least** $1 - \delta$, each of the following holds for *all* $g \in \mathcal{G}$:
>$$
> \begin{align}
>  \mathbb{E}\left[ g(Z) \right] &\le \frac{1}{n}\sum_{i=1}^{n}g(Z_i) + 2 \mathfrak{R}_{n}(\mathcal{G})  + \sqrt{\frac{\log(1 / \delta)}{2n}} 
> \end{align}
>$$ 
> and
>$$ 
> \begin{align}
> \mathbb{E}\left[ g(Z) \right] &\le \frac{1}{n}\sum_{i=1}^{n}g(Z_i) + 2 \widehat{\mathfrak{R}}_{n}(\mathcal{G}) + 3\sqrt{\frac{\log(2 / \delta)}{2n}} 
> \end{align}
>$$ 

^5276e2

- [[Bounded Difference Inequality]]
- [[Symmetrized Empirical Process]]
- [[Talagrand Contraction Principle]]
- [[Symmetrization Inequalities for Empirical Process]]



## Explanation





-----------
##  Recommended Notes and References



- [[Rademacher Complexity]]
- [[Rademacher Process]]
- [[Empirical Process and Empirical Measure]]

- [[Rademacher Complexity Upper Bound for Suprema of Empirical Process]]


- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]