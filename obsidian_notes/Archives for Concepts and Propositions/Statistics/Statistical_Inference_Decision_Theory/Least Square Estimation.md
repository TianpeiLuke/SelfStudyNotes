---
tags:
  - concept
  - statistics/estimation
  - math/probability
keywords:
  - least_square_estimation
topics:
  - statistics/estimation
name: Least Square Estimation
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Least Square Estimation

![[Linear Regression#^b406ef]]

![[Linear Regression#^8d6149]]

>[!important] Definition
>Let $\left\{ (X_{s}, Y_{s}),\; s=1\,{,}\ldots{,}\,m \right\}$ be a set of $m$ i.i.d. random variables from some distribution $\mathcal{P}$. 
>
>Assume that $Y_{s}$ given $X_{s}$ is represented by a **linear regression model**
>$$
>Y_{s} = \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0} + \epsilon_{s},\; \quad s=1 \,{,}\ldots{,}\,m.
>$$
>where $\epsilon_{s}|X_{s} \sim \mathcal{N}(0, \sigma^2)$. This implies that
>$$
>Y_{s}|X_{s} \sim \mathcal{N}\left(\sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0}\;;\; \sigma^2  \right)
>$$
>
>The *log-likelihood function* is
>$$
>\begin{align*}
>\sum_{s=1}^{m}\ell(\beta, \sigma; (X_{s}, Y_{s})) &= \sum_{s=1}^{m}\log p_{X}(X_{s})+ \sum_{s=1}^{m} \log p_{Y|X}(Y_{s}|X_{s}; \beta, \sigma) \\
>&\propto -\frac{1}{2\sigma^2}\; \sum_{s=1}^{m}\left( Y_{s} - \mu_{s}(X_{s}; \beta) \right)^2 - m \log(\sigma)
>\end{align*}
>$$
>where the *conditional mean*
>$$\mu_{s}(X_{s}; \beta)  := \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0}.$$
>
>We call 
>$$
>\ell(\beta, \sigma; (X_{s}, Y_{s})) := -\frac{1}{2\sigma^2}\; \sum_{s=1}^{m}\left( Y_{s} - \mu_{s}(X_{s}; \beta) \right)^2 - m \log(\sigma)
>$$
>the **conditional likelihood function.**

^fe636c

>[!important] Definition
>The **linear least squares estimates (LSE)** are the value $\hat{\beta} := (\hat{\beta}_1 \,{,}\ldots{,}\,\hat{\beta}_d,\,\hat{\beta}_{0})$ that minimize the **residual sum of squares**
>$$
>\hat{\beta} = \arg\min_{\beta} \sum_{s=1}^{m}\left[ Y_{s} - \left( \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0} \right)\right]^2
>$$
>where 
>- the **residual sum of squares** is defined as 
>$$
> RSS := \sum_{s=1}^{m}\hat{\epsilon}_{s}^2 = \sum_{s=1}^{m}\left( Y_{s} - \mu_{s}(X_{s}; \beta) \right)^2;
>$$
>- and the conditional mean is linear
>$$\mu_{s}(X_{s}; \beta)  := \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0}.$$
>

^9775a7


- [[Linear Regression]]
- [[Maximum Likelihood Estimation]]

>[!important] Definition
>The **linear least squares estimation (LSE) problem** can be represented in compact form as
>$$
>\min_{\beta \in \mathbb{R}^{d+1}} \lVert Y - X\,\beta \rVert_{2}^2 
>$$

^f8f306

### Solution of Least Square Estimation

![[Least Square Estimation Solution and Geometric Interpretation#^17b91f]]

- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]

![[Least Square Estimation Solution and Geometric Interpretation#^03c5db]]

### Algorithm to Solve Least Square Estimation

- [[Algorithms for Least Square Estimation Problem]]


## Explanation

>[!info]
>The **least square estimate** is the **maximum likelihood estimation** of **linear regression model** 
>$$
>Y_{s} = \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0} + \epsilon_{s},\; \quad s=1 \,{,}\ldots{,}\,m.
>$$
>where $\epsilon_{s}|X_{s} \sim \mathcal{N}(0, \sigma^2)$ and $(\epsilon_{s})$ are *conditionally independent.* 
>- This implies that $$Y_{s}|X_{s} \sim \mathcal{N}\left(\sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0}\;;\; \sigma^2  \right)$$

^e8b187

## Gauss-Markov Theorem and BLUE

![[Gauss–Markov Theorem#^2d98dc]]

- [[Gauss–Markov Theorem]]
- [[Best Linear Unbiased Prediction]]

## Minimum Variance Unbiased Estimation (MVUE)

>[!info]
>The **Gauss-Markov Theorem** implies that the **least squares estimator** has the **smallest mean squared error** of all **linear estimators** with no bias. 
>
>However, there may well exist a **biased estimator** with smaller mean squared error.

- [[Uniformly Minimum Variance Unbiased Estimation]]

## Nonlinear / Non-parametric Least Square Problem

![[Non-Parametric Least Square Estimation#^01d861]]

- [[Non-Parametric Least Square Estimation]]



-----------
##  Recommended Notes and References

- [[Gauss–Markov Theorem]]
- [[Uniformly Minimum Variance Unbiased Estimation]]

- [[Linear Regression]]
- [[Regression Problem]]
- [[Point Estimator]]


- [[All of Statistics A Concise Course by Wasserman]] pp 211
- [[Mathematical Statistics by Shao]] pp 182
- [[Optimization by Vector Space Methods by Luenberger]]  pp 78 - 102
- [[Numerical Optimization by Nocedal]] pp 245
- [[Elements of Statistical Learning by Hastie]] pp 43 - 56
- [[Matrix Computations by Golub]] pp 303 - 334
- [[Numerical Linear Algebra by Trefethen]] pp 77 - 87
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 65 - 71