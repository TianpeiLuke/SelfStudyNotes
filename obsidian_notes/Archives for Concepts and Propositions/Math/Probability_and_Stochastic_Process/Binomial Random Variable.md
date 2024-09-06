---
tags:
  - concept
  - math/probability
  - statistics/estimation
  - statistics/inference
  - statistics/bayesian
keywords:
  - binomial_distribution
topics:
  - probability
name: Binomial Random Variable
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Binomial Random Variable

>[!important] Definition
>A discrete random variable $X \in \{ 0,\,1 \,{,}\ldots{,}\, n\}$ follows the **binomial distribution** with parameter $n\in \mathbb{N}$ and $p\in [0,1]$, if the *probability mass function* is given by 
>$$
>p(k; n, p) = \mathcal{P}(X = k) = {n \choose k}\,p^{k}\,(1- p)^{n - k} :=  \frac{n!}{k! (n-k)!}\,p^{k}\,(1- p)^{n - k}
>$$
>where $k = 0,\,1 \,{,}\ldots{,}\,n$.
>
>It is denoted as $B(n, p).$

- [[Bernoulli Random Variable]]

### Support

>[!important] Definition
>The **support** for binomial distribution is $$\{ 0 ,1 \,{,}\ldots{,}\,n \} = [n]$$



### Mean and Covariance

>[!important] Definition
>The **mean** of  of $$X \sim B(n; p)$$ is $$\mathbb{E}_{ p }\left[  X \right] = n p.$$ 
>
>The **variance** of $X$ is $$\text{Var}(X) = n\,p(1 - p).$$
>

### Moment Generating Functions

>[!important] Definition
>The **moment generating function** of $X \sim  B(n; p)$ is 
>$$
>M_{X}(t) = \mathbb{E}_{ p }\left[  e^{t\, X} \right] = \left(1 - p + p\,e^{t}\right)^{n}.
>$$
>




## Explanation





## Sum of IID Bernoulli Random Variables

- [[Bernoulli Random Variable]]


## Sub-Gaussian Random Variables

- [[Sub-Gaussian Random Variable]]


## Multi-Dimensional Extension

- [[Multinomial Random Variable]]



-----------
##  Recommended Notes and References

- [[Multinomial Random Variable]]
- [[Bernoulli Random Variable]]
- [[Geometric Random Variable]]
- [[Sub-Gaussian Random Variable]]

- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]

- Wikipedia [Binomial_distribution](https://en.wikipedia.org/wiki/Binomial_distribution)