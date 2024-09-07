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






## Explanation



## Gamma Distribution

>[!important]
>$\chi^2$-distribution is a special case of **Gamma distribution**.
>$$
>\chi^2(k) = \Gamma \left(\alpha = \frac{k}{2}, \theta = 2 \right)
>$$
>where $\theta$ is the *rate parameter*.

- [[Gamma Distribution]]


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


- [[Mathematical Statistics by Shao]] pp 20, 23, 25,  27
- Wikipedia [Chi-squared_distribution](https://en.wikipedia.org/wiki/Chi-squared_distribution)