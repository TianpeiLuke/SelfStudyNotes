---
tags:
  - concept
  - math/probability
  - statistics/concentration_inequality
  - math/stochastic_process
keywords:
  - gaussian_cumulative_distribution
topics:
  - probability
  - concentration_inequality
name: Gaussian Cumulative Distribution Function
date of note: 2024-06-09
---

## Concept Definition

>[!important]
>**Name**: Gaussian Cumulative Distribution Function

>[!important] Definition
>The **cumulative distribution function (C.D.F.)** for **standard normal random variable** $\mathcal{N}(0,1)$  is defined as
>$$
>\Phi(x) = \frac{1}{\sqrt{ 2\pi }} \int_{-\infty}^{x} e^{- t^2/2}dt
>$$

- [[Cumulative Distribution Function of Random Variable]]
- [[Gaussian Random Variable]]

>[!important] Definition
>The **error function** $\text{erf}(x)$ is the probability of a standard normal random variable $X\sim \mathcal{N}\left( 0, \frac{1}{2} \right)$ *failing in the range* of $[-x, +x]$ 
>$$
>\text{erf}(x) := \mathcal{P}_{\mathcal{N}}(X \in [-x, x]) = \frac{1}{\sqrt{ \pi }}\int_{-x}^{x}\,e^{-t^2}dt
>$$



>[!important]
>The following equation holds between **c.d.f.** of $\mathcal{N}(\mu, \sigma^2)$ and the **error function** $$\Phi \left( \frac{x - \mu}{\sigma} \right) = \frac{1}{2}\left[ 1 + \text{erf}\left( \frac{x - \mu}{\sigma\,\sqrt{ 2 }} \right) \right] $$
>or
>$$\Phi \left( x \right) = \frac{1}{2}\left[ 1 + \text{erf}\left( \frac{x}{\sqrt{ 2 }} \right) \right] $$

## Property

>[!important] Proposition
>The **graph** of the standard normal cumulative distribution function $\Phi$ has **$2$-fold rotational symmetry** around the point $(0,1/2)$:
>$$
>\Phi(-x) = 1 - \Phi(x).
>$$



## Explanation



## Quantile Function

- [[Gaussian Quantile Function or Probit Function]]



-----------
##  Recommended Notes and References

- [[Gaussian Quantile Function or Probit Function]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Gaussian Measure]]
- [[Gaussian Random Variable]]

- [[Gaussian Isoperimetric Function]]
- [[Gaussian Concentration Theorem]]



- [[Concentration Inequalities by Boucheron]]
- [[Monte Carlo Statistical Methods by Robert]]
- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]