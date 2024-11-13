---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - deep_learning/generative_models
  - statistics/hypothesis_testing
keywords:
  - chi_squared_divergence
topics:
  - information_theory
  - information_geometry
  - deep_learning/generative_models
  - statistics/hypothesis_testing
name: Chi-squared Divergence
date of note: 2024-11-07
---

## Concept Definition

>[!important]
>**Name**: Chi-squared Divergence or $\chi^2$-divergence

>[!important] Definition
>if $P$ and $Q$ are *probability measures* on a measurable space $(\Omega, \mathscr{F})$, and $P$ is *absolutely continuous* with respect to $Q$, 
>$$P \ll Q.$$
>
>The **$\chi^2$-divergence** or **$\chi^2$-distance** from $Q$ to $P$ is defined as
>$$
>\begin{align*}
> \chi^2\left( P \left\|\right. Q \right) &= \frac{1}{2} \int_{\Omega} \left(\frac{dP}{dQ} - 1\right)^2\,dQ \\[8pt]
> &:= \frac{1}{2} \int_{\Omega} \frac{\left(q(x) - p(x)\right)^2}{q(x)}d\mu
>\end{align*}
>$$
>where 
>- $p, q$ are p.d.f. of  $P, Q$ with respect to a $\sigma$-finite measure $\mu$, i.e. $$p(x) := \frac{dP}{d\mu}(x), \quad q(x) := \frac{dQ}{d\mu}(x)$$
>- $dP / dQ$ is the *Radon-Nikodym derivative* of $P$ with respect to $Q$.

- [[Radon-Nikodym Derivative]]
- [[Probability Density Function of Random Variable]]
- [[Absolute Continuity for Measures]]

### Symmetric $\chi^2$ Distance or Triangle Discrimination Distance

>[!important] Definition
>if $P$ and $Q$ are *probability measures* on a measurable space $(\Omega, \mathscr{F})$, and $P$ is *absolutely continuous* with respect to $Q$, 
>$$P \ll Q.$$
>
>The **symmetric $\chi^2$-divergence** or **triangle discrimination distance** from $Q$ to $P$ is defined as
>$$
>\begin{align*}
> \Delta\left( P \left\|\right. Q \right) &:= \frac{1}{2} \int_{\Omega} \frac{\left(p(x) - q(x)\right)^2}{p(x) + q(x)}d\mu
>\end{align*}
>$$
>where 
>- $p, q$ are p.d.f. of  $P, Q$ with respect to a $\sigma$-finite measure $\mu$, i.e. $$p(x) := \frac{dP}{d\mu}(x), \quad q(x) := \frac{dQ}{d\mu}(x)$$
>- $dP / dQ$ is the *Radon-Nikodym derivative* of $P$ with respect to $Q$.


## Explanation


## f-Divergence

![[f-Divergence#^1543bf]]

- [[f-Divergence]]

## Connection with Least Square Surrogate Loss

![[Density Ratio Estimation via Binary Classifiers#^c559d1]]

- [[Density Ratio Estimation via Binary Classifiers]]
- [[Least Square Estimation]]



-----------
##  Recommended Notes and References


- [[Divergence Function on Manifold]]


- [[Chi-Squared-Test]]
- [[Chi-Squared Distribution]]



- [[Statistical Manifold as Parametric Family]]
- [[Probability Space]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 57
