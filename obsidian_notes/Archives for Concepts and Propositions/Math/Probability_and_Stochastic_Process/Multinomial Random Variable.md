---
tags:
  - concept
  - math/probability
  - statistics/estimation
  - statistics/inference
  - statistics/bayesian
keywords:
  - multinomial_distribution
topics:
  - probability
name: Multinomial Random Variable
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Multinomial Random Variable

>[!important] Definition
>A $k$-dimensional *non-negative discrete* random vector $$X = (X_{1} \,{,}\ldots{,}\,X_{k}) \in \left\{  (x_{1} \,{,}\ldots{,}\,x_{k}): \sum_{i=1}^{k}x_{i} = n, \; x_{i} \in \mathbb{N}_{+}, i=1 \,{,}\ldots{,}\,k  \right\}$$ is from the **multinomial distribution** with parameters $$p \in \Delta_{k} := \left\{(p_{1} \,{,}\ldots{,}\, p_{k}):\; \sum_{i=1}^{k}p_{i} = 1,\, p_{i} \ge 0\right\},$$ if the *probability mass function* is given by 
>$$
>\begin{align*}
>&p((x_{1} \,{,}\ldots{,}\,x_{k}); n, (p_{1} \,{,}\ldots{,}\, p_{k}) )\\[5pt]
>&= \mathcal{P}\left(X_{1} = x_{1} \,{,}\ldots{,}\, X_{k} = x_{k} \right) \\[5pt]
>&= \left\{ \begin{array}{ll} \dfrac{n!}{x_{1}! \ldots x_{k}!}\;p_{1}^{x_{1}} \,{\times}\ldots{\times}\,p_{k}^{x_{k}} & \text{ if } \sum_{i=1}^{k}x_{i} = n \\[5pt] 0 & \text{ otherwise} \end{array}\right.\end{align*}
>$$
>It is denoted $Multinomial(p_{1} \,{,}\ldots{,}\, p_{k}).$
>
>The **support** of **multinomial distribution**
>$$
>\left\{ (x_{1} \,{,}\ldots{,}\,x_{k}) \in \mathbb{N}^{k}: \sum_{i=1}^{k}x_{i} = n \right\}
>$$


>[!important] Definition
>The **probability mass function** for the **multinomial distribution**  can be expressed using the Gamma function
>$$
>p((x_{1} \,{,}\ldots{,}\,x_{k}); (p_{1} \,{,}\ldots{,}\, p_{k}) )
> = \frac{\Gamma\left(\sum_{i=1}^{k}x_{i} + 1\right)}{\prod_{i=1}^{k}\Gamma(x_{i} + 1)}\,\prod_{i=1}^{k}p_{i}^{x_{i}}
>$$
>for $x:= (x_{1} \,{,}\ldots{,}\,x_{k}) \in \mathbb{N}^{k}.$

### Support

>[!important] Definition
>The **support** for multinomial distribution is $$\left\{  (x_{1} \,{,}\ldots{,}\,x_{k}): \sum_{i=1}^{k}x_{i} = n, \; x_{i} \in \mathbb{N}, i=1 \,{,}\ldots{,}\,k  \right\}  \subset \mathbb{N}^{k} / \{ n \}.$$



### Mean and Covariance

>[!important] Definition
>The **mean** of each *coordinate component* of $$X \sim Multinomial(n; p_{1} \,{,}\ldots{,}\, p_{k})$$ is $$\mathbb{E}_{ p }\left[  X_{i} \right] = n p_{i}, \quad i=1\,{,}\ldots{,}\,k$$ 
>
>The **variance** of each *coordinate component* of $X$ is $$\text{Var}(X_{i}) = n\,p_{i}(1 - p_{i}), \quad i=1\,{,}\ldots{,}\,k$$
>
>The **covariance** between *coordinate components* of $X$ is $$\text{Cov}(X_{i}, X_{j}) = -n\,p_{i}\,p_{j}, \quad i \neq j.$$

>[!important] Definition
>The vector version of mean and covariance
>- The  **mean of random vector** $$\mathbb{E}_{ p }\left[  X \right] = n p.$$
>- The **covariance matrix** of random vector $$\text{Cov}(X, X) = n\,\left(\text{diag}(p) - pp^{T}\right)$$

### Moment Generating Functions

>[!important] Definition
>The **moment generating function** of $X \sim  Multinomial(n; p_{1} \,{,}\ldots{,}\, p_{k})$ is 
>$$
>M_{X}(t) = \mathbb{E}_{ p }\left[  e^{\left\langle  t\,,\, X   \right\rangle} \right] = \left(\sum_{i=1}^{k}p_{i}e^{t_{i}}\right)^{n}.
>$$
>with $t = (t_{1} \,{,}\ldots{,}\,t_{k}).$



## Explanation



## Conjugate Prior

- [[Dirichlet Random Variable]]




-----------
##  Recommended Notes and References


- [[Sub-Gaussian Random Variable]]
- [[Dirichlet Random Variable]]


- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]

- Wikipedia [Multinomial_distribution](https://en.wikipedia.org/wiki/Multinomial_distribution)