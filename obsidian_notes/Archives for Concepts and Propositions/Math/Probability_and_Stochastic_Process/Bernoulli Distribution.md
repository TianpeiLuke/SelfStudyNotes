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

### Support

>[!important] Definition
>The **support** for Bernoulli distribution is $$\{ 0 ,1 \}$$


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



## Maximum Likelihood Estimation

>[!important]
>The **log-likelihood function** is 
>$$
>\log p(x; p) = x \log p  + (1- x) \log (1- p)
>$$


>[!important]
>The **MLE** of parameter $p$ for a set of i.i.d. Bernoulli random variables $X_{i}, i=1\,{,}\ldots{,}\,n$ is the sample mean $$\hat{p} = \frac{1}{n}\sum_{i=1}^{n}X_{i}.$$

## Exponential Family

>[!important] 
>We can reformulate the Bernoulli distribution in the **natural parameterization** of *exponential family*
>$$
>\begin{align*}
> p(x; p) &= \exp \left( x \log p  + (1- x) \log (1- p) \right) \\[5pt]
> &= \exp \left( \log \left( \frac{p}{1- p} \right)\,x  + \log (1-p)\,\right) \\[5pt]
> &:= \exp \left( \left\langle \theta(p) , T(x) \right\rangle - A(\theta) \right) \\[5pt]
>\end{align*}
>$$
>where
>$$
>\begin{align*}
>\theta(p) &= \log \left( \frac{p}{1- p} \right) \\[5pt]
>T(x) &= x \\[5pt]
>A(\theta) &= \log \frac{1}{1- p} = \log \left( 1 + e^{\theta} \right).
>\end{align*}
>$$

^b7be16


- [[Exponential Family of Distributions]]
- [[Generalized Linear Models]]
- [[Logistic Regression]]

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


- [[Generalized Linear Models]]
- [[Binomial Distribution]]
- [[Sub-Gaussian Random Variable]]

- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]

- [[Mathematical Statistics by Shao]] pp 122
- Wikipedia [Bernoulli_distribution](https://en.wikipedia.org/wiki/Bernoulli_distribution)