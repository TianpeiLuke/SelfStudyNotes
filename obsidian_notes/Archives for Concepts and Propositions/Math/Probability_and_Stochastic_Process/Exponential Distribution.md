---
tags:
  - concept
  - math/probability
  - statistics/estimation
  - statistics/inference
  - statistics/bayesian
keywords:
  - exponential_distribution
topics:
  - probability
name: Exponential Distribution
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Exponential Distribution

>[!important] Definition
>The **exponential distribution** is a *one-parameter family* of continuous probability distribution.
>
>There are *two equivalent parametrization* of exponential distribution:
>- **rate parametrization**: 
>	- A random variable $X \in (0, \infty)$ follows the **exponential distribution** with **rate parameter** $\lambda >0$ if the p.d.f. of $X$ is given by $$p(x; \lambda) := \lambda\,e^{- \lambda x}$$
>	- Denote $X \sim Exp(\lambda)$
>- **scale parametrization**: 
>	- A random variable $X \in (0, \infty)$ follows the **exponential distribution** with **scale parameter** $\theta >0$ if the p.d.f. of $X$ is given by $$p(x; \theta) := \frac{1}{\theta} e^{- x/\theta}$$ where $\Gamma(x)$ is the **Gamma function**.
>	- $$\theta := \frac{1}{\lambda}.$$
>	- Denote $X \sim Exp(\theta^{-1})$

- [[Probability Density Function of Random Variable]]
- [[Parametric Models]]

### Support

>[!important] Definition
>The **support** for exponential distribution is $$[0, \infty).$$

### Mean, Variance

>[!important] Definition
>The **mean** of $X \sim Exp(\lambda)$ is $$\mathbb{E}_{ p }\left[  X \right] = \frac{1}{\lambda}.$$
>
>The **n-th moment** of $X$ is $$\mathbb{E}_{ p }\left[  X^n \right] = \frac{n!}{\lambda^n}.$$
>
>The **variance** of $X \sim Exp(\lambda)$ is $$\text{Var}(X) = \frac{1}{\lambda^2}.$$


### Moment Generating Function

>[!important] Definition
>The **moment generating function** of $X \sim Exp(\lambda)$ is 
>$$
>M_{X}(t) = \mathbb{E}_{ p }\left[  e^{t X} \right] = \left(1 - \frac{t}{\lambda}\right)^{-1}  \quad \text{ if }t < \lambda.
>$$
>
>The **logarithmic moment generating function** is $$\psi_{X}(t) = - \log \left(1 - \frac{t}{\lambda}\right) \quad \text{ if }t <  \lambda.$$


## Explanation



## Gamma Distribution

>[!info]
>The **exponential distribution** is a special case of Gamma distribution.
>$$
>Exp(\lambda) = \Gamma \left(\alpha = 1, \beta = \lambda \right)
>$$
>when 
>- **shape parameter** $$\alpha = 1$$ 
>-  **rate parameter** $$\beta = \lambda$$ 

- [[Gamma Distribution]]


## Maximum Likelihood Estimation


- [[Maximum Likelihood Estimation]]


## Exponential Family

>[!important] 
>We can reformulate the Gamma distribution in the **natural parameterization** of *exponential family*
>$$
>\begin{align*}
> p(x; \lambda) &= \exp \left( - \lambda x  +  \log(\lambda)  \right) \\[5pt]
> &:= \exp \left( \left\langle \xi , T(x) \right\rangle  - A(\xi)\right) 
>\end{align*}
>$$
>where
>$$
>\begin{align*}
> \xi  &=  -\lambda \\[5pt]
>T(x) &= x \\[5pt]
>A(\xi) &=  - \log(\lambda) = -\log(-\xi)
>\end{align*}
>$$

- [[Exponential Family of Distributions]]


## Sub-Exponential / Sub-Gamma Random Variables

>[!important]
>The exponential random variable is a **sub-gamma random variable**. 

- [[Sub-Exponential Random Variables]]
- [[Sub-Gamma Random Variables]]


## Concentration Inequalities 

- [[Bennett Inequality]]
- [[Bernstein Inequality]]




-----------
##  Recommended Notes and References


- [[Gamma Distribution]]
- [[Poisson Distribution]]


- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]

- [[Mathematical Statistics by Shao]] pp 9, 20
- Wikipedia [Exponential_distribution](https://en.wikipedia.org/wiki/Exponential_distribution)