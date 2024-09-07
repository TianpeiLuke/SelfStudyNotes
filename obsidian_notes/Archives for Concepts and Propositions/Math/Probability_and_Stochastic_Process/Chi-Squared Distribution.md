---
tags:
  - concept
  - math/probability
  - statistics/estimation
  - statistics/inference
  - statistics/bayesian
keywords:
  - chi_squared_distribution
topics:
  - probability
name: Chi-Squared Distribution
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Chi-Squared Distribution

>[!important] Definition
>A random variable $X\in [0,\infty)$ is from the **$\chi^2$-distribution** (**chi-squared distribution**) with $k$ **degree of freedom** if it is the *sum* of *squares* of  $k$ *independent standard normal random variables*.
>
>That is, let $Z_{i} \sim \mathcal{N}(0,1)$ be $k$ i.i.d. random variables, then 
>$$
>X = \sum_{i=1}^{k} Z_{i}^2 \sim \chi^2(k).
>$$
>
>The p.d.f. of $\chi^2(k)$ is 
>$$
>p(x; k) := \frac{1}{\Gamma(k /2) 2^{k / 2}}\,x^{k/2 - 1}\, e^{-x / 2}
>$$
>for $x \in [0,\infty),$ and $k \in \mathbb{N}.$

### Support

>[!important] Definition
>The **support** for Gamma distribution is $$(0, \infty).$$

### Mean, Variance

>[!important] Definition
>The **mean** of $X \sim \chi^2(k)$ is $$\mathbb{E}_{ p }\left[  X \right] = k.$$
>
>The **n-th moment** of $X$ is $$\mathbb{E}_{ p }\left[  X^n \right] = \theta^n\,\frac{\Gamma(k / 2 + n)}{\Gamma(k / 2)}.$$
>
>The **variance** of $X \sim \chi^2(k)$ is $$\text{Var}(X) = 2k.$$


### Moment Generating Function

>[!important] Definition
>The **moment generating function** of $X \sim \chi^2(k)$ is 
>$$
>M_{X}(t) = \mathbb{E}_{ p }\left[  e^{t X} \right] =  \left(1 - 2 t\right)^{-k / 2} \quad \text{ if }t < \frac{1}{2}.
>$$
>
>The **logarithmic moment generating function** is $$\psi_{X}(t) = -\frac{k}{2}\,\log \left(1 - 2 t\right)\quad \text{ if }t < \frac{1}{2}.$$


## Explanation



## Gamma Distribution

>[!important]
>$\chi^2$-distribution is a special case of **Gamma distribution**.
>$$
>\chi^2(k) = \Gamma \left(\alpha = \frac{k}{2}, \theta = 2 \right)
>$$
>where $\theta$ is the *rate parameter*.

- [[Gamma Distribution]]

## Exponential Family

>[!important] 
>We can reformulate the Gamma distribution in the **natural parameterization** of *exponential family*
>$$
>\begin{align*}
> p(x; k) &= \exp \left( \left( \frac{k}{2}-1 \right)\,\log(x) - \frac{x}{2} - \frac{k}{2} \log(2)  - \log \left(\Gamma(k / 2)\right)  \right) \\[5pt]
> &:= \exp \left( \left\langle \xi , T(x) \right\rangle  - A(\xi)\right) 
>\end{align*}
>$$
>where
>$$
>\begin{align*}
>\xi &= \left( \left( \frac{k}{2}-1 \right), -\frac{1}{2} \right)^{T} \\[5pt]
>T(x) &= (\log(x), x)^{T}  \\[5pt]
>A(\xi) &= - \frac{k}{2} \log(2)  - \log \left(\Gamma(k / 2)\right) \\[5pt]
>&= (\xi_{1} +1)\,\log(-\xi_{2}) - \log\Gamma(\xi_{1} + 1)  
>\end{align*}
>$$

- [[Exponential Family of Distributions]]




## Sub-Exponential, Sub-Gamma Random Variables

- [[Sub-Exponential Random Variables]]
- [[Sub-Gamma Random Variables]]



-----------
##  Recommended Notes and References


- [[Gaussian Random Variable]]
- [[Chi-Squared-Test]]


- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]


- [[Mathematical Statistics by Shao]] pp 20- 22, 23, 25,  27
- Wikipedia [Chi-squared_distribution](https://en.wikipedia.org/wiki/Chi-squared_distribution)