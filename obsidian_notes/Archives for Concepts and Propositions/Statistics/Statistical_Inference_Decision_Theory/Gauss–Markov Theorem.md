---
tags:
  - concept
  - statistics/estimation
keywords:
  - gauss_markov_theorem
topics:
  - statistics
name: Gauss–Markov theorem
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Gauss–Markov Theorem

![[Linear Regression#^24812d]]

![[Linear Regression#^b406ef]]


>[!important] Gauss-Markov Theorem
>Suppose that $$y = X\beta + \epsilon$$ is from a **linear regression model**, where the noise term $$\mathbb{E}\left[ \epsilon \right] = 0, \;\;  \mathbb{E}\left[ \epsilon\,\epsilon^{T} \right] = \Sigma \succ 0$$ has **zero mean** and covariance $\Sigma$. 
>
>The **linear minimum-variance unbiased estimate (UMVUE)** of $\beta$ is
>$$
>\hat{\beta} = \left( X^{T}\Sigma^{-1}\,X\right)^{-1}\,X^{T}\,\Sigma^{-1}\,y
>$$
>with corresponding **error covariance** 
>$$
>\hat{\Sigma} =  \mathbb{E}\left[( \hat{\beta} - \beta )\,( \hat{\beta} - \beta )^{T}\right] = \left( X^{T}\Sigma^{-1}\,X\right)^{-1}.
>$$
>
>In other word, for any *unbiased linear estimator* $\beta'$ of $\beta$, the variance of estimate of $y$ is larger than that of the LSE
>$$
>\text{Var}(X \hat{\beta}) \le \text{Var}(X\beta').
>$$
>- equivalently, the error covariance $$\mathbb{E}\left[( \hat{\beta} - \beta )\,( \hat{\beta} - \beta )^{T}\right]  \preceq \mathbb{E}\left[\left( \beta' - \beta \right)\,\left( \beta' - \beta \right)^{T}\right]$$

^2d98dc

- [[Uniformly Minimum Variance Unbiased Estimation]]
- [[Best Linear Unbiased Prediction]]
- [[Linear Regression]]
- [[Least Square Estimation]]
- [[Best Linear Unbiased Prediction]]

## Explanation

>[!info]
>**Gauss-Markov theorem** states that **least square estimator** has **uniformly minimum variance** among **unbiased estimator** for linear regression model.
>



## Least Square Estimation

![[Least Square Estimation Solution and Geometric Interpretation#^17b91f]]

- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]



-----------
##  Recommended Notes and References


- [[Point Estimator]]
- [[Best Linear Unbiased Prediction]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 189
- [[Elements of Statistical Learning by Hastie]]
- [[Optimization by Vector Space Methods by Luenberger]] pp 86

- Wikipedia [Gauss-Markov theorem](https://en.wikipedia.org/wiki/Gauss%E2%80%93Markov_theorem)