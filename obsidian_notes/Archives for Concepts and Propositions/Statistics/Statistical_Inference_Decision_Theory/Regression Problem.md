---
tags:
  - concept
  - statistics/estimation
  - statistics/inference
keywords:
  - regression_problem
topics:
  - statistics/estimation
  - statistics/inference
name: Regression Problem
date of note: 2024-06-11
---

## Concept Definition

>[!important]
>**Name**: Regression Problem

![[Statistical Estimation Problem#^994e95]]

>[!important] Definition
>A  **regression problem** studies the relationship between 
>- the **response variables**  $Y\in \mathbb{R}$ and 
>- the **covariate variables** $X := (X^{1} \,{,}\ldots{,}\,X^{d})\in \mathbb{R}^{d}.$
>
>The goal is to find a function $r\in \mathcal{H} \subset \left\{ r:\mathbb{R}^d \to \mathbb{R} \right\}$ such that the **mean squared error** is minimized
>$$
> \min_{r\in \mathcal{H}} \mathbb{E}_{ \mathcal{P} }\left[ \lVert Y - r(X) \rVert_{2}^2  \right]
>$$
>where $(X, Y)\sim \mathcal{P}$ for some distribution $\mathcal{P}$.

^cae88d

- [[Minimum Mean Square Estimation]]
- [[Statistical Estimation Problem]]
- [[Parametric Models]]

>[!info]
>The minimum mean squared estimator is the **conditional mean estimator**
>$$
>r(X) :=  \mathbb{E}\left[ Y | X \right]
>$$

- [[Minimum Mean Square Estimation]]
- [[Conditional Expectation]]

## Explanation


## Linear Regression

- [[Linear Regression]]
- [[Least Square Estimation]]



-----------
##  Recommended Notes and References

- [[Least Square Estimation]]

- [[Maximum Likelihood Estimation]]
- [[Generalized Linear Models]]
- [[Parametric Models]]
- [[Empirical Risk Minimization]]
- [[Statistical Decision Problem]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]

- [[Elements of Statistical Learning by Hastie]]
- [[All of Statistics A Concise Course by Wasserman]] pp 208
- [[Mathematical Statistics by Shao]] 