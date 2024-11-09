---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
keywords:
  - hellinger_distance
topics:
  - information_theory
  - information_geometry
name: Hellinger Distance between Distributions
date of note: 2024-11-07
---

## Concept Definition

>[!important]
>**Name**: Hellinger Distance between Distributions

>[!important] Definition
>if $P$ and $Q$ are *probability measures* on a measurable space $(\Omega, \mathscr{F})$, and $P$ is *absolutely continuous* with respect to $Q$, 
>$$P \ll Q.$$
>
>The **squared Helinger distance** between $P$ and $Q$ is defined by
>$$
>\begin{align*}
>H^2(P, Q) &:= \frac{1}{2}\int_{\Omega}\left(\sqrt{ \frac{dP}{dQ} } - 1\right)^2\,dQ \\[8pt]
>&= \frac{1}{2} \int_{\Omega}\left(\sqrt{ p(x) } - \sqrt{ q(x) }\right)^2\,d\mu \\[8pt]
>&= 1 - \int_{\Omega}\sqrt{ p(x)q(x) }\,d\mu
>\end{align*}
>$$
>where 
>- $p, q$ are p.d.f. of  $P, Q$ with respect to a $\sigma$-finite measure $\mu$, i.e. $$p(x) := \frac{dP}{d\mu}(x), \quad q(x) := \frac{dQ}{d\mu}(x)$$
>- $dP / dQ$ is the *Radon-Nikodym derivative* of $P$ with respect to $Q$.

- [[Radon-Nikodym Derivative]]
- [[Probability Density Function of Random Variable]]
- [[Absolute Continuity for Measures]]


## Explanation


## $f$-divergence and $\alpha$-divergence

![[f-Divergence#^b23587]]

- [[f-Divergence]]
- [[Renyi Divergence and Renyi Entropy]]

![[alpha-Divergence#^59f390]]

- [[alpha-Divergence]]


## Exponential Loss

![[Density Ratio Estimation via Binary Classifiers#^f9387f]]

- [[Exponential Loss Minimization for AdaBoost]]
- [[Density Ratio Estimation via Binary Classifiers]]



-----------
##  Recommended Notes and References



- [[Kullback-Leibler Divergence]]
- [[Divergence Function on Manifold]]

- [[Jensen Inequality]]
- [[Shannon Entropy]]

- [[Statistical Manifold as Parametric Family]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]]  pp 57
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]] pp 490
- Wikipedia [Hellinger_distance](https://en.wikipedia.org/wiki/Hellinger_distance)

