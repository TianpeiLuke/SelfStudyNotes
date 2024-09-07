---
tags:
  - concept
  - math/probability
  - statistics/estimation
  - statistics/inference
  - statistics/bayesian
keywords:
  - gamma_distribution
topics:
  - probability
name: Gamma Distribution
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Gamma Distribution

>[!important] Definition
>The **Gamma distribution** is a *two-parameter family* of continuous probability distribution.
>
>There are *two equivalent parametrization* of Gamma distribution:
>- **shape, scale parametrization**: 
>	- A random variable $X \in (0, \infty)$ follows the **Gamma distribution** with **shape parameter** $k >0$ and **scale parameter** $\theta >0$ if the p.d.f. of $X$ is given by $$p(x; k, \theta) := \frac{1}{\Gamma(k)\,\theta^{k}}\,x^{k - 1}\,e^{- x/\theta}$$ where $\Gamma(x)$ is the **Gamma function**.
>	- $X \sim \Gamma(k, \theta)$
>- **shape, rate parametrization**: 
>	- A random variable $X \in (0, \infty)$ follows the **Gamma distribution** with **shape parameter** $\alpha >0$ and **rate parameter** $\beta >0$ if the p.d.f. of $X$ is given by $$p(x; \alpha, \beta) := \frac{\beta^{\alpha}}{\Gamma(\alpha)}\,x^{\alpha - 1}\,e^{- \beta x}$$
>	- $X \sim \Gamma(\alpha, \beta)$
>	- Note that $$\beta = \frac{1}{\theta}$$

- [[Probability Density Function of Random Variable]]
- [[Parametric Models]]


### Support

>[!important] Definition
>The **support** for Gamma distribution is $$(0, \infty).$$

### Mean, Variance

>[!important] Definition
>The **mean** of $X \sim \Gamma(\alpha, \beta) \equiv \Gamma(k, \theta)$ is $$\mathbb{E}_{ p }\left[  X \right] = \frac{\alpha}{\beta} = k\theta.$$
>
>The **n-th moment** of $X$ is $$\mathbb{E}_{ p }\left[  X^n \right] = \theta^n\,\frac{\Gamma(k + n)}{\Gamma(k)}.$$
>
>The **variance** of $X \sim \Gamma(\alpha, \beta) \equiv \Gamma(k, \theta)$ is $$\text{Var}(X) = \frac{\alpha}{\beta^2}  = k\theta^2.$$


### Moment Generating Function

>[!important] Definition
>The **moment generating function** of $X \sim \Gamma(\alpha, \beta) \equiv \Gamma(k, \theta)$ is 
>$$
>M_{X}(t) = \mathbb{E}_{ p }\left[  e^{t X} \right] = \left(1 - \frac{t}{\beta}\right)^{-\alpha} \equiv \left(1 - \theta t\right)^{-k} \quad \text{ if }t < \beta = \frac{1}{\theta}.
>$$
>
>The **logarithmic moment generating function** is $$\psi_{X}(t) = -\alpha \log \left(1 - \frac{t}{\beta}\right) \equiv -k\,\log \left(1 - \theta t\right)\quad \text{ if }t < \beta = \frac{1}{\theta}.$$




## Explanation

>[!quote]
>The distribution has important applications in various fields, including **econometrics**, **Bayesian statistics**, life testing. 
>- In econometrics, the $(k, \theta)$ *parameterization* is common for modeling **waiting times**, such as the time until death, where it often takes the form of an [Erlang distribution](https://en.wikipedia.org/wiki/Erlang_distribution "Erlang distribution") for **integer** $k$ values. 
>- Bayesian statistics prefer the $(\alpha, \beta)$ *parameterization*, utilizing the gamma distribution as a **conjugate prior** for several *inverse scale parameters*, facilitating analytical tractability in posterior distribution computations.


## Examples

>[!example]
>The **$\chi^2$-distribution** is a special case of Gamma distribution.
>$$
>\chi^2(k) = \Gamma \left(\alpha = \frac{k}{2}, \theta = 2 \right)
>$$
>when 
>- **shape parameter** $$\alpha = \frac{k}{2}$$ 
>-  **scale parameter** $$\theta = 2 = \frac{1}{\beta}$$ 

- [[Chi-Squared Distribution]]

>[!example]
>The **exponential distribution** is a special case of Gamma distribution.
>$$
>Exp(\lambda) = \Gamma \left(\alpha = 1, \beta = \lambda \right)
>$$
>when 
>- **shape parameter** $$\alpha = 1$$ 
>-  **rate parameter** $$\beta = \lambda$$ 

- [[Exponential Distribution]]

## Sum of IID Exponential Distribution

>[!important]
>Let $Z_{i} \sim Exp(\lambda)$ be $n$ *i.i.d.* random variables, then
>$$
>X = \sum_{i=1}^{n}Z_{i} \sim \Gamma\left(\alpha = n, \beta = \lambda \right).
>$$

## Sum of Independent Gamma Distribution

>[!important]
>Let $Z_{i} \sim \Gamma(k_{i}, \theta)$ be $n$ *independent* random variables, with common *scale* $\theta$ , then
>$$
>X = \sum_{i=1}^{n}Z_{i} \sim \Gamma\left( \sum_{i=1}^{n}k_{i}, \theta\right).
>$$

## Scaling

>[!important]
>Let $X \sim \Gamma(k, \theta) \equiv \Gamma(\alpha, \beta)$ be Gamma random variables, then
>$$
>c X \sim \Gamma\left(k, c \theta\right) \equiv \Gamma\left(\alpha, \frac{\beta}{c}\right) .
>$$


## Maximum Likelihood Estimation


>[!important] 
>The **log-likelihood function** is
>$$
>\log p(x; k, \theta) = (k-1)\,\log(x) - \frac{x}{\theta} - k \log(\theta)  - \log \left(\Gamma(k)\right) 
>$$
>or
>$$
>\log p(x; \alpha, \beta) = (\alpha-1)\,\log(x) - \beta x + \alpha \log(\beta)  - \log \left(\Gamma(\alpha)\right) 
>$$



## Exponential Family

>[!important] 
>We can reformulate the Gamma distribution in the **natural parameterization** of *exponential family*
>$$
>\begin{align*}
> p(x; k, \theta) &= \exp \left( (k-1)\,\log(x) - \frac{x}{\theta} - k \log(\theta)  - \log \left(\Gamma(k)\right)  \right) \\[5pt]
>&\equiv \exp \left( (\alpha -1)\,\log(x) - \beta x  + \alpha \log(\beta)  - \log \left(\Gamma(\alpha)\right)  \right) \\[5pt]
> &:= \exp \left( \left\langle \xi , T(x) \right\rangle  - A(\xi)\right) 
>\end{align*}
>$$
>where
>$$
>\begin{align*}
>\xi &= \left( (k-1), -\frac{1}{\theta} \right)^{T} \\[5pt]
>T(x) &= (\log(x), x)^{T}  \\[5pt]
>A(\xi) &= - k \log(\theta)  - \log \left(\Gamma(k)\right) \\[5pt]
>&= (\xi_{1} +1)\,\log(-\xi_{2}) - \log\Gamma(\xi_{1} + 1)  
>\end{align*}
>$$
>or
>$$
>\begin{align*}
> \eta  &= \left( (\alpha-1), - \beta \right)^{T} \\[5pt]
>T(x) &= (\log(x), x)^{T}  \\[5pt]
>A(\eta) &= \alpha \log(\beta)  - \log \left(\Gamma(\alpha)\right)  \\[5pt]
>&= (\eta_{1} +1)\,\log(-\eta_{2}) - \log\Gamma(\eta_{1} + 1)  
>\end{align*}
>$$


- [[Exponential Family of Distributions]]

## Sub-Exponential / Sub-Gamma Random Variables

>[!important]
>The Gamma random variable is a **sub-gamma random variable**. 

- [[Sub-Exponential Random Variables]]
- [[Sub-Gamma Random Variables]]

- [[Bennett Inequality]]
- [[Bernstein Inequality]]

## Concentration Inequalities 

- [[Bennett Inequality]]
- [[Bernstein Inequality]]


## Conjugate Prior

>[!important]
>The gamma distribution is the **conjugate prior** for the **precision** $$\frac{1}{\sigma^2}$$ of the *normal distribution* $\mathcal{N}(\mu, \sigma^2)$ with *known* mean $\mu$.

- [[Conjugate Prior Distribution for Bayesian Inference]]



-----------
##  Recommended Notes and References


- [[Chi-Squared Distribution]]
- [[Sub-Exponential Random Variables]]
- [[Sub-Gamma Random Variables]]

- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]
- Wikipedia [Gamma_distribution](https://en.wikipedia.org/wiki/Gamma_distribution)