---
tags:
  - concept
  - math/probability
keywords:
  - de_moivre_laplace_theorem
topics:
  - probability
name: De Moivre–Laplace Theorem
date of note: 2024-06-04
---

## Concept Definition

>[!important]
>**Name**: De Moivre–Laplace Theorem

>[!important] De Moivre–Laplace Theorem
>Let $(X_{i}, i\ge 1 )$ be a sequence of **independent** **Bernoulli random variable**, taking values in $\left\{ 1, 0 \right\}$ with probability $p$ and $q= 1-p.$
>
>Let $S_{n}$ be the number of successes in $n$ Bernoulli trials, i.e. $$S_{n} = \sum_{j=1}^n X_{j}$$
>
>Then 
>$$
> \frac{S_{n} - np}{\sqrt{ n p\,q }} \stackrel{d}{\rightarrow} \mathcal{N}(0, 1)
>$$

- [[Central Limit Theorem]]


>[!important] De Moivre–Laplace Theorem (Equivalent Form)
>Let $(X_{i}, i\ge 1 )$ be a sequence of **independent** **Bernoulli random variable**, taking values in $\left\{ 1, 0 \right\}$ with probability $p$ and $q= 1-p.$
>
>Let $S_{n}$ be the number of successes in $n$ Bernoulli trials, i.e. $$S_{n} = \sum_{j=1}^n X_{j}$$
>
>Then for all $-\infty < a < b < +\infty$,
>$$
>\begin{align*}
>\lim_{ n \to \infty } \mathcal{P}\left( \frac{S_{n} - np}{\sqrt{ n p q }} \in (a, b)\right) = \frac{1}{\sqrt{ 2\pi }} \int_{a}^{b}\exp \left( - \frac{t^2}{2} \right) dt.
>\end{align*}
>$$


## Explanation

>[!important]
>The *De Moivre–Laplace Theorem* is the first version of **central limit theorem**.


>[!info]
>The second version is the equivalent version of the first, given by [[Portmanteau Theorem]] as
>$$
>\lim_{ n \to \infty } \mathcal{P}\left( \frac{S_{n} - np}{\sqrt{ n p q }} \in (a, b)\right) = \lim_{ n \to \infty } \left[ \mathcal{P}\left( \frac{S_{n} - np}{\sqrt{ n p q }} < b \right) - \mathcal{P}\left( \frac{S_{n} - np}{\sqrt{ n p q }} < a \right) \right] 
>$$





-----------
##  Recommended Notes and References



- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]