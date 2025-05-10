---
tags:
  - concept
  - statistics/inference
  - statistics/estimation
  - optimization/algorithm
  - optimization/linear_optimization
  - optimization/theory
  - statistics/regression
keywords:
  - least_absolute_deviations
  - sparsity
topics:
  - statistics/inference
  - statistics/estimation
  - optimization/theory
  - optimization/algorithm
name: Least Absolute Deviations
date of note: 2024-10-11
---

## Concept Definition

>[!important]
>**Name**: Least Absolute Deviations

![[Linear Regression#^06ce34]]

![[Linear Regression#^24812d]]

- [[Linear Regression]]

>[!important] Definition
>The **least absolute deviations estimates (LAD)**, also known as 
>- **least absolute errors** (**LAE**), 
>- **least absolute residuals** (**LAR**), or 
>- **least absolute values** (**LAV**),  
>
>are the value $\hat{\beta} := (\hat{\beta}_1 \,{,}\ldots{,}\,\hat{\beta}_d,\,\hat{\beta}_{0})$ that minimize the **residual sum of absolute erros**
>$$
>\hat{\beta} = \arg\min_{\beta} \sum_{s=1}^{m}\left\lvert  Y_{s} - \left( \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0} \right)\right\rvert  
>$$
>where 
>- the **residual sum of absolute errors** is defined as 
>$$
> \sum_{s=1}^{m}|\hat{\epsilon}_{s}| = \sum_{s=1}^{m}\left\lvert Y_{s} - \mu_{s}(X_{s}; \beta) \right\rvert ;
>$$
>- and the conditional mean is linear
>$$\mu_{s}(X_{s}; \beta)  := \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0}.$$
>

^5fb0d6


>[!important] Definition
>The **least  absolute deviations (LAD) problem** can be represented in compact form as
>$$
>\min_{\beta \in \mathbb{R}^{d+1}} \lVert y- X\,\beta \rVert_{1} 
>$$
>where $X\in \mathbb{R}^{m\times (d+1)}$ are the *design matrix*.
>- *LAD* solves a **$\ell_{1}$ norm approximation** problem.

^ee1435


## Explanation



## Solution to LAD Problem

![[Least Absolute Deviations Solution via Iterative Re-weighted Least Square#^538310]]

- [[Least Absolute Deviations Solution via Iterative Re-weighted Least Square]]

![[Least Absolute Deviations Solution via Iterative Re-weighted Least Square#^9104d2]]

![[Least Absolute Deviations Solution via Iterative Re-weighted Least Square#^cb93bb]]


## $\ell_{1}$ vs. $\ell_{2}$ Regression Problem

![[Least Square Estimation#^9775a7]]

- [[Least Square Estimation]]





-----------
##  Recommended Notes and References



- [[LASSO and Sparsity-Induced Least Square]]
- [[Laplace Distribution]]


- [[Mathematical Statistics by Shao]] pp 123
- [[Theory of Point Estimation by Lehmann]] pp 484
- [[Convex Optimization by Boyd]] pp 617 - 618