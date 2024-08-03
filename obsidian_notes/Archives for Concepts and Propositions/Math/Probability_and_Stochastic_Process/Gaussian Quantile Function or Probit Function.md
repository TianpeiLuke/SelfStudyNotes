---
tags:
  - concept
  - math/probability
  - statistics/concentration_inequality
  - math/stochastic_process
keywords:
  - gaussian_cumulative_distribution
  - gaussian_quantile_function
topics:
  - probability
  - concentration_inequality
name: Gaussian Quantile Function
date of note: 2024-06-09
---

## Concept Definition

>[!important]
>**Name**: Gaussian Quantile Function

![[Quantile Function#^700c00]]


>[!important] Definition
>The **Gaussian quantile function** or **probit function** or **normal quantile** is the *quantile function* associated with the *standard normal distribution*, denoted as $\text{probit}(p)$, i.e.
>$$
>\text{probit}(p) = \Phi^{-1}(p), \quad p\in (0,1)
>$$

- [[Quantile Function]]
- [[Gaussian Cumulative Distribution Function]]
- [[Gaussian Random Variable]]

>[!important]
>The **probit function** can be obtained by *inverse of error function*
>$$
>\Phi^{-1}(p) = \sqrt{ 2 }\; \text{erf}^{-1}(2p - 1).
>$$

## Explanation


## Ordinary Differential Equation

>[!important]
>Let $w(p): = \Phi^{-1}(p)$. The normal quantile can be described by an *nonlinear ordinary differential equation*
>$$
> \frac{d^2}{dp^2} w =  w\,\left( \frac{d}{dp}w  \right)^2
>$$

- [[Ordinary Differential Equations]]


## Gaussian Isoperimetric Function

![[Gaussian Isoperimetric Function#^fcd238]]


- [[Gaussian Isoperimetric Function]]




-----------
##  Recommended Notes and References

- [[Gaussian Cumulative Distribution Function]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Gaussian Measure]]
- [[Gaussian Random Variable]]

- [[Gaussian Isoperimetric Function]]

- [[Gaussian Concentration Theorem]]
- [[Gaussian Isoperimetric Function]]


- [[Concentration Inequalities by Boucheron]]
- [[Monte Carlo Statistical Methods by Robert]]
- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]