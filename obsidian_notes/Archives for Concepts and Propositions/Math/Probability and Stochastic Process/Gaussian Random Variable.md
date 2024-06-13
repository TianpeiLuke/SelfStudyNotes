---
tags:
  - concept
  - math/probability
keywords:
  - gaussian_distribution
  - gaussian_variable
topics:
  - probability
name: Gaussian Random Variable
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Gaussian Random Variable

>[!important] Definition
>Let $(\mathbb{R}, \mathcal{B}(\mathbb{R}))$ be a *measurable space*, where $\mathcal{B}(\mathbb{R})$ is the *Borel $\sigma-$algebra* on $\mathbb{R}$. 
>
>A real-valued random variable $X$ is **Normally distributed** or **Gaussian** with expectation $\mu \in \mathbb{R}$ and variance $\sigma^2 > 0$, if its **distribution density** with respect to *Lebesgue measure*  is 
>$$
> \begin{align*}
> p(x) &= \frac{1}{\sqrt{2\pi\sigma^{2}}}\exp \left( -\frac{(x - \mu)^{2}}{2\sigma^{2}} \right).
> \end{align*} 
>$$ 
>
>We say that $X \sim \mathcal{N}(\mu, \sigma^2)$.


- [[Probability Distribution of Random Variable]]
- [[Density and Probability Density]]

>[!important]
>We call the measure $\mathcal{N}$ with Gaussian density as **Gaussian measure.**
>$$
>d\mathcal{N}(x) := \frac{1}{\sqrt{2\pi\sigma^{2}}}\exp \left( -\frac{(x - \mu)^{2}}{2\sigma^{2}} \right) dx
>$$

>[!important] Definition
>Denote the **cumulative distribution function** of *standard Normal distribution*:
>$$
> \begin{align*}
> \Phi(x) &= \int_{-\infty}^{x}\frac{1}{\sqrt{2\pi}}\exp \left(-\frac{t^2}{2}\right)dt := \int_{-\infty}^{x}p(t) dt
> \end{align*}
>$$  
>where $p(x) = (\Phi(x))'$ is the *probability density function* of *standard normal distribution*. 
>
>$\Phi^{-1}(x)$ is the **quantile function** of **normal distribution**.



## Explanation

>[!info]
>The 1-dimensional Gaussian distribution is a **Borel measure** on the *real line.* 

>[!info]
>The Gaussian measure $d\mathcal{P}_{\mathcal{N}} \ll dx$ is *absolutely continuous* with respect to Lebesgue measure.

- [[Lebesgue Measure]]
- [[Absolute Continuity for Measures]]


>[!info]
>The **density function** defined above with respect to *the Lebesgue measure* on real line.
>$$
>d\mathcal{P}_{\mathcal{N}} = \frac{1}{\sqrt{2\pi\sigma^{2}}}\exp \left( -\frac{(x - \mu)^{2}}{2\sigma^{2}} \right)dx
>$$



## Concentration of Gaussian Measure

- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]




-----------
##  Recommended Notes and References

