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

- [[Bernoulli Distribution]]

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

>[!info]
>Consider a set of $n$ **binary variables** $Z_{i} \in \left\{  0, 1 \right\}$  (Bernoulli random variable), a *Binomial random variable* $X \sim B(n, p)$ can be seen as the **count** of binary variables **when** $Z_{i} = 1$
>$$
>X = \frac{1}{n} \sum_{i=1}^{n}\mathbb{1}\left\{ Z_{i} = 1 \right\}
>$$

- [[Characteristic Function of Set]]

## Maximum Likelihood Estimation


>[!important] 
>The **log-likelihood function** is
>$$
>\log p(k; n, p) = k\,\log(p) + (n-k)\,\log(1-p)   + \log \left(  {n \choose k} \right)
>$$


>[!important] 
>Let $X_{i} \sim \text{B}(n, p)$ be $m$ i.i.d. Binomial random variables $i=1\,{,}\ldots{,} m,$ then the **MLE** for parameter $p$ is
>$$
>\hat{p} = \frac{1}{n\,m} \sum_{i=1}^{m}X_{i} = \dfrac{\frac{1}{m}\sum_{i=1}^{m}X_{i}}{n}
>$$




## Sum of IID Bernoulli Random Variables

>[!important] 
>Let $Z_{i} \sim \text{Ber}(p)$ be $n$ i.i.d. Bernoulli random variables $i=1\,{,}\ldots{,} n,$ then 
>$$
>X = \sum_{i=1}^{n}Z_{i} \sim B(n, p)
>$$

- [[Bernoulli Distribution]]


## Exponential Family

>[!important] 
>We can reformulate the Binomial distribution in the **natural parameterization** of *exponential family*
>$$
>\begin{align*}
> p(k; p) &= \exp \left( k\,\log(p) + (n-k)\,\log(1-p)   + \log \left(  {n \choose k} \right) \right) \\[5pt]
> &= \exp \left( \log \left( \frac{p}{1- p}\right)\,k + n\,\log(1-p) \right)\,{n \choose k} \\[10pt]
> &:= \exp \left( \left\langle \theta(p) , T(k) \right\rangle  - A(\theta)\right)\;h(k)
>\end{align*}
>$$
>where
>$$
>\begin{align*}
>\theta(p) &= \log \left( \frac{p}{1- p}\right) \\[5pt]
>T(k) &= k  \\[5pt]
>A(\theta) &= n \log \left( 1 + e^{\theta} \right)
>\end{align*}
>$$
>and
>$$
>h(k) := {n \choose k} := \frac{n!}{k! (n-k)!}
>$$
>is the normalization factor for the *counting measure*.

^ddf730


- [[Exponential Family of Distributions]]
- [[Counting Measure]]

## Sub-Gaussian Random Variables

- [[Sub-Gaussian Random Variable]]


## Multi-Dimensional Extension

- [[Multinomial Distribution]]



-----------
##  Recommended Notes and References

- [[Multinomial Distribution]]
- [[Bernoulli Distribution]]
- [[Geometric Distribution]]
- [[Sub-Gaussian Random Variable]]

- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]

- [[Mathematical Statistics by Shao]] pp 18, 44-45
- Wikipedia [Binomial_distribution](https://en.wikipedia.org/wiki/Binomial_distribution)