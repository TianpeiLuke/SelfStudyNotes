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

>[!info]
>The **Poisson distribution** is a discrete probability distribution that expresses the probability of *a given number* of events occurring *in a fixed interval of time* if these events occur with a known *constant mean rate* and *independently* of the time since the last event.




## Maximum Likelihood Estimation


>[!important] 
>The **log-likelihood function** is
>$$
>\log p(k; \lambda) = -\lambda + k\,\log(\lambda) - \log(k!)
>$$

>[!important] 
>Let $X_{i} \sim \text{Poisson}(\lambda)$ be $m$ i.i.d. *Poisson random variables* $i=1\,{,}\ldots{,} m,$ then the **MLE** for parameter $\lambda$ is
>$$
>\hat{\lambda} = \frac{1}{m} \sum_{i=1}^{m}X_{i}
>$$


## Sums of Poisson-Distributed random variables

>[!important] 
>Let $X_{i} \sim \text{Poisson}(\lambda_{i})$ be $m$ **independent** *Poisson random variables* $i=1\,{,}\ldots{,} m,$
>
>Then the **sum** is also a *Poisson-distributed random variable* 
>$$
>\sum_{i=1}^{m}X_{i} \sim \text{Poisson}\left( \sum_{i=1}^{m}\lambda_{i} \right)
>$$


## Exponential Family

>[!important] 
>We can reformulate the Poisson distribution in the **natural parameterization** of *exponential family*
>$$
>\begin{align*}
> p(k; \lambda) &= \exp \left( \log(\lambda)\,k -\lambda\right)\frac{1}{k!} \\[5pt]
> &:= \exp \left( \left\langle \theta(\lambda) , T(k) \right\rangle  - A(\theta)\right)\;h(k)
>\end{align*}
>$$
>where
>$$
>\begin{align*}
>\theta(\lambda) &= \log(\lambda)  \\[5pt]
>T(k) &= k  \\[5pt]
>A(\theta) &= \lambda = \exp \left(\theta\right)
>\end{align*}
>$$
>and
>$$
>h(k) :=  \frac{1}{k!}
>$$
>is the normalization factor for the *counting measure*.

^3043cb


## Sub-Exponential Distribution

>[!important]
>The Bernoulli random variable is a **sub-exponential random variable**. 

- [[Sub-Exponential Random Variables]]
- [[Sub-Gamma Random Variables]]

- [[Bennett Inequality]]
- [[Bernstein Inequality]]

## Gamma Conjugate Prior Distribution


- [[Gamma Distribution]]
- [[Conjugate Prior Distribution for Bayesian Inference]]


## Concentration Inequalities 

- [[Chernoff Bound for Poisson distribution]]




-----------
##  Recommended Notes and References



- [[Exponential Distribution]]

- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]

- [[Mathematical Statistics by Shao]] pp 18
- Wikipedia [Poisson_distribution](https://en.wikipedia.org/wiki/Poisson_distribution)