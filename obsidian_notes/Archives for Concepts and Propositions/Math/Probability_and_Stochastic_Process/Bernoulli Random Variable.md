---
tags:
  - concept
  - math/probability
  - statistics/estimation
  - statistics/inference
  - statistics/bayesian
keywords:
  - bernoulli_distribution
topics:
  - probability
  - statistics/inference
name: Bernoulli Random Variable
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Bernoulli Random Variable

>[!important] Definition
>A discrete random variable $X\in \{ 0,1 \}$ follows the **Bernoulli distribution** if the probability 
>$$
>\mathcal{P}(X = 1) = p = 1 - \mathcal{P}(X = 0)
>$$
>
>The **probability mass function** (i.e. p.d.f. with respect to discrete measure) is 
>$$
>p(x; p) = p^{x}\,(1- p)^{(1- x)}; \quad x\in \{ 0, 1 \}
>$$
>
>It is denoted as $Ber(p)$

- [[Probability Density Function of Random Variable]]

### Mean, Variance

>[!important] Definition
>The **mean** of $X \sim Ber(p)$ is $$\mathbb{E}_{ p }\left[  X \right] = p$$
>The **2nd moment** is $$\mathbb{E}_{ p }\left[  X^2 \right] = p$$
>
>The **variance** of $X \sim Ber(p)$ is $$\text{Var}(X) = p(1 - p)$$

### Moment Generating Function

>[!important] Definition
>The **moment generating function** of $X \sim Ber(p)$ is 
>$$
>M_{X}(t) = \mathbb{E}_{ p }\left[  e^{t X} \right] = (1- p) + pe^{t}.
>$$
>
>The **logarithmic moment generating function** is $$\psi_{X}(t) = \log \left((1-p) + pe^{t}\right).$$

- [[Moment Generating Function]]


## Explanation


## Sub-Gaussian Distribution

>[!important]
>The Bernoulli random variable is **bounded** thus it is  **sub-Gaussian**. 

- [[Sub-Gaussian Random Variable]]
- [[Sub-Gaussian Norm]]
- [[Hoeffding Inequality]]



## Concentration Inequalities 

- [[Chernoff Bound for Bernoulli distribution]]
- [[Logarithmic Sobolev Inequality for Bernoulli Random Variables]]



-----------
##  Recommended Notes and References


- [[Binomial Random Variable]]
- [[Sub-Gaussian Random Variable]]

- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]

- Wikipedia [Bernoulli_distribution](https://en.wikipedia.org/wiki/Bernoulli_distribution)