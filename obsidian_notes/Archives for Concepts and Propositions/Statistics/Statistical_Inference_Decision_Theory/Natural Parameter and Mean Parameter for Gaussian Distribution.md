---
tags:
  - concept
  - probabilistic_graphical_models/models
  - math/probability
  - statistics/estimation
keywords:
  - natural_parameterization
  - mean_parameterization
topics:
  - probability
  - probabilistic_graphical_model
  - statistics/estimation
name: Natural Parameter and Mean Parameter for Gaussian Distribution
date of note: 2024-08-28
---

## Concept Definition

>[!important]
>**Name**: Natural Parameter and Mean Parameter for Gaussian Distribution

![[Gaussian Random Vector#^a97326]]

![[Gaussian Graphical Model#^162c43]]

### Natural Parameters

>[!important] Definition
>The *multivariate Gaussian distribution* $\mathcal{N}(\mu, \Sigma)$ has the **natural paramterization**
>$$
>p(x; \theta, \Theta) := \exp \left(\left\langle  \theta\,,\, x  \right\rangle + \left\langle  \Theta\,x\,,\, x \right\rangle - Z(\theta, \Theta) \right)
>$$
>where the **natural parameters** $(\theta, \Theta) = \omega(\mu, \Sigma)$ 
>$$
>\begin{align*}
> \Theta &= -\frac{1}{2} \Sigma^{-1}\\[5pt]
> \theta &= \Sigma^{-1}\mu
>\end{align*}
>$$
>- The **log-partition function** is $$Z(\theta, \Theta) = \frac{1}{2}\left\{n \log(2\pi) - \frac{1}{2}\left\langle  \Theta^{-1}\theta\,,\, \theta \right\rangle -\log \left[  (-2)^{n} \det \left\lvert  \Theta \right\rvert\right] \right\}$$
>- The **sufficient statistics** for $\Theta$ and $\theta$ are 
>  $$
> \begin{align*}
> XX^{T} & \leftrightarrow \Theta \\[5pt]
> X & \leftrightarrow \theta
>\end{align*}
> $$ 
>
>- The **inverse** of mapping, $\omega^{-1}$, is defined as
>$$
>\begin{align*}
> \Sigma &= -\frac{1}{2} \Theta^{-1}\\[5pt]
> \mu &= -\frac{1}{2} \Theta^{-1}\theta
>\end{align*}
>$$

- [[Gaussian Random Vector]]
- [[Gaussian Graphical Model]]
- [[Canonical Form of Gaussian Graphical Model]]

### Mean Parameters




## Explanation





-----------
##  Recommended Notes and References


- [[Canonical Form of Gaussian Graphical Model]]
- [[Gaussian Random Vector]]
- [[Gaussian Graphical Model]]
- [[Gaussian Process]]
- [[Inverse Covariance Estimation]]



- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]

