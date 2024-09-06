---
tags:
  - concept
  - math/probability
  - statistics/estimation
  - statistics/inference
  - statistics/bayesian
keywords:
  - poisson_distribution
topics:
  - probability
name: Poisson Random Variable
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Poisson Random Variable

>[!important] Definition
>A discrete random variable $X \in \{ 0, 1\,{,}\ldots{,}\, \}$ is said to have **Poisson distribution** with parameter $\lambda >0$, if the *probability mass function* is given by
>$$
>p(k; \lambda) := \mathcal{P}(X = k) =  \frac{1}{k!}\lambda^k e^{-\lambda}
>$$
>where $k \in \{ 0,1 \,{,}\ldots{,}\, \}.$ It is denoted as $Poisson(\lambda).$
>
>The probability mass function for Poisson distribution is a *probability density function* with respect to *counting measure* $\# \in \{0, 1, \,{,}\ldots{,}\, \}$

- [[Probability Density Function of Random Variable]]
- [[Counting Measure]]

### Support

>[!important] Definition
>The **support** for Poisson distribution is $$\{ 0,1 \,{,}\ldots{,}\, \} = \mathbb{N}.$$

### Mean, Variance

>[!important] Definition
>The **mean** of $X \sim Poisson(\lambda)$ is $$\mathbb{E}_{ p }\left[  X \right] = \lambda.$$
>
>The **2nd moment** of $X$ is $$\mathbb{E}_{ p }\left[  X^2 \right] = \lambda^2 + \lambda.$$
>
>The **variance** of $X \sim Poisson(\lambda)$ is $$\text{Var}(X) = \lambda.$$


### Moment Generating Function

>[!important] Definition
>The **moment generating function** of $X \sim Poisson(\lambda)$ is 
>$$
>M_{X}(t) = \mathbb{E}_{ p }\left[  e^{t X} \right] = e^{\lambda (e^{t} - 1)} = \exp \left(\lambda \left(\exp(t) - 1\right)\right).
>$$
>
>The **logarithmic moment generating function** is $$\psi_{X}(t) = \lambda\,(e^{t} - 1).$$



## Explanation


## Sub-Exponential Distribution

>[!important]
>The Bernoulli random variable is a **sub-exponential random variable**. 

- [[Sub-Exponential Random Variables]]
- [[Sub-Gamma Random Variables]]

- [[Bennett Inequality]]
- [[Bernstein Inequality]]



## Concentration Inequalities 

- [[Chernoff Bound for Poisson distribution]]




-----------
##  Recommended Notes and References



- [[Exponential Random Variable]]

- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]
- Wikipedia [Poisson_distribution](https://en.wikipedia.org/wiki/Poisson_distribution)