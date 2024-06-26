---
tags:
  - concept
  - machine_learning/theory
  - math/stochastic_process
  - statistics/concentration_inequality
keywords:
  - empirical_rademacher_complexity
topics:
  - machine_learning_theory
  - stochastic_process
  - concentration_inequality
name: Rademacher Complexity
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Empirical Rademacher Complexity

>[!important] Definition
>Let $\mathcal{F}$ be a family of functions on $\mathcal{X}$ and $\mathcal{D} = (X_1 \,{,}\ldots{,}\, X_n)$ a fixed **sample** of size $n$ with elements in $\mathcal{X}$. 
>
>Then, the **empirical Rademacher complexity** of $\mathcal{F}$ *with respect to the sample* $\mathcal{D}$ is defined as:
>$$
> \begin{align}
> \widehat{\mathfrak{R}}_{\mathcal{D}}(\mathcal{F})&= \mathbb{E}_{ \epsilon }\left[ \sup_{f \in \mathcal{F}}\frac{1}{n}\sum_{i=1}^{n}\epsilon_{i}f(X_i) \right]   = \mathbb{E}_{ \epsilon }\left[ \sup_{f \in \mathcal{F}} \mathcal{P}_n^{\epsilon}f  \right]
> \end{align}
>$$ 
> where $\epsilon := (\epsilon_1 \,{,}\ldots{,}\,\epsilon_n)$ are *independent uniform random variables* taking values in $\set{-1, +1}$. The random variables $\epsilon_i$ are called *Rademacher variables*.

- [[Rademacher Complexity]]
- [[Rademacher Process]]
- [[Empirical Process and Empirical Measure]]



## Explanation

![[Rademacher Complexity#^8eafb1]]

>[!important]
>For any integer $n \ge 1$, the **Rademacher complexity** of $\mathcal{F}$ is defined as the *expectation* of *the empirical Rademacher complexity* over *all samples* $\mathcal{D}_n$ of size $n$ drawn according to $\mathcal{P}_{n} = \otimes_{i=1}^n\mathcal{P}_i$:
>$$
> \begin{align*}
> \mathfrak{R}_{n}(\mathcal{F}) &= \mathbb{E}_{ \mathcal{D}_{n} \sim \mathcal{P}_{n} }\left[  \widehat{\mathfrak{R}}_{\mathcal{D}_n}(\mathcal{F}) \right].
> \end{align*}
>$$ 

- [[Rademacher Complexity]]


-----------
##  Recommended Notes and References



- [[Rademacher Process]]
- [[Empirical Process and Empirical Measure]]

- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]

- [[Concentration Inequalities by Boucheron]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]