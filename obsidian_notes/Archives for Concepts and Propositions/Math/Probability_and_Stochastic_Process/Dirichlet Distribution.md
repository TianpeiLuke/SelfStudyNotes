---
tags:
  - concept
  - math/probability
  - statistics/estimation
  - statistics/inference
  - statistics/bayesian
keywords:
  - dirichlet_distribution
topics:
  - probability
name: Dirichlet Random Variable
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Dirichlet Random Variable

>[!important] Definition
>A $k$-dimensional *non-negative* random vector $$X = (X_{1} \,{,}\ldots{,}\,X_{k}) \in \Delta_{k-1} := \left\{  (x_{1} \,{,}\ldots{,}\,x_{k}): \sum_{i=1}^{k}x_{i} = 1, \; x_{i} \in [0,1], i=1 \,{,}\ldots{,}\,k  \right\}$$ is from the **Dirichlet distribution** with parameters $$\alpha \in \mathbb{R}_{+}^{k} := \left\{(\alpha_{1} \,{,}\ldots{,}\, \alpha_{k}):\; \alpha_{i} \ge 0\right\},$$ if the *probability density function* with respect to *Lebesgue measure*  is given by 
>$$
>\begin{align*}
>p((x_{1} \,{,}\ldots{,}\,x_{k}); (\alpha_{1} \,{,}\ldots{,}\, \alpha_{k}) ) &= \frac{\Gamma\left(\sum_{i=1}^{k}\alpha_{i} \right)}{\prod_{i=1}^{k}\Gamma(\alpha_{i} )}\,\prod_{i=1}^{k}x_{i}^{\alpha_{i} - 1}
>\end{align*}
>$$
>It is denoted $Dirichlet(\alpha_{1} \,{,}\ldots{,}\, \alpha_{k}).$

- [[Probability Density Function of Random Variable]]
- [[Lebesgue Measure]]

### Support

>[!important] Definition
>The **support** for Dirichlet distribution is **$(k-1)$-dimensional simplex** $$\Delta_{k-1} := \left\{  (x_{1} \,{,}\ldots{,}\,x_{k}): \sum_{i=1}^{k}x_{i} = 1, \; x_{i} \in [0,1], i=1 \,{,}\ldots{,}\,k  \right\}.$$

- [[Generalized Simplex]]


### Mean and Covariance

>[!important] Definition
>The **mean** of each *coordinate component* of $$X \sim Dirichlet(\alpha_{1} \,{,}\ldots{,}\, \alpha_{k})$$ is $$\mathbb{E}_{ p }\left[  X_{i} \right] = \frac{\alpha_{i}}{\sum_{i=1}^{k}\alpha_{i}}, \quad i=1\,{,}\ldots{,}\,k$$ 
>with $$\alpha_{0} := \sum_{i=1}^{k}\alpha_{i}.$$
>
>The **variance** of each *coordinate component* of $X$ is $$\text{Var}(X_{i}) = \frac{\alpha_{i}\left(\alpha_{0}- \alpha_{i}\right)}{\alpha_{0}^2 \left( \alpha_{0} + 1\right)}, \quad i=1\,{,}\ldots{,}\,k$$
>
>The **covariance** between *coordinate components* of $X$ is $$\text{Cov}(X_{i}, X_{j}) = -\frac{\alpha_{i}\alpha_{j}}{\alpha_{0}^2 \left( \alpha_{0} + 1\right)}, \quad i \neq j.$$



## Explanation





-----------
##  Recommended Notes and References


- [[Multinomial Distribution]]
- [[Sub-Gaussian Random Variable]]

- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]


- [[Mathematical Statistics by Shao]] pp 268
- Wikipedia [Dirichlet_distribution](https://en.wikipedia.org/wiki/Dirichlet_distribution)