---
tags:
  - concept
  - statistics/estimation
  - math/probability
keywords:
  - least_square_estimation
  - nonparametric_model
topics:
  - statistics/estimation
name: Non-Parametric Least Square Estimation
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Non-Parametric Least Square Estimation

### Linear Parametric Least Square Estimation

![[Linear Regression#^b406ef]]

![[Linear Regression#^8d6149]]

![[Least Square Estimation#^fe636c]]

- [[Least Square Estimation]]
- [[Linear Regression]]
- [[Maximum Likelihood Estimation]]

### Nonlinear / Non-parametric Least Square Problem

>[!important] Definition
>We can generalize the **least square problem** to general *non-parametric models*. 
>
>Consider a function space $\mathcal{F}$ and a **regression** model as
>$$
>y_{s} = f(x_{s}) + \epsilon_{s}, \quad s=1\,{,}\ldots{,}\,m
>$$
>where $f\in \mathcal{F}$ and $\epsilon_{s}\sim \mathcal{N}(0, \sigma^2)$ are i.i.d..
>
>The **non-parametric least square estimation** problem is to find the optimal $\hat{f}\in \mathcal{F}$ such that
>$$
>\hat{f} \in \arg\min_{f\in \mathcal{F}} \; \sum_{s=1}^{m}\lVert y_{s} - f(x_{s}) \rVert_{2}^2 
>$$

^01d861

- [[Nonparametric Models and Semi-Parametric Models]]
- [[Least Square Estimation]]


### Solution for Non-Parametric Least Square 

>[!important] Definition
>From [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]], the optimal solution $\hat{y}$ that minimize the squared loss function $$f(\hat{y}) = \ell(\hat{y}, y) = \lVert y - \hat{y} \rVert^2$$ need to satisfies the **secant equations**
>$$
> \nabla^2\,f(\hat{y})\,p = - \nabla f(\hat{y})
>$$


- [[Gradient Descent Algorithm]]
- [[Newton Method]]
- [[Secant Equation and Quasi-Newton Methods]]

## Explanation









-----------
##  Recommended Notes and References

- [[Gauss–Markov Theorem]]
- [[Uniformly Minimum Variance Unbiased Estimation]]

- [[Linear Regression]]
- [[Regression Problem]]
- [[Point Estimator]]


- [[All of Statistics A Concise Course by Wasserman]] pp 211
- [[All of Nonparametric Statistics by Wasserman]] pp 61 - 71
- [[Mathematical Statistics by Shao]] pp 182
- [[Optimization by Vector Space Methods by Luenberger]]  pp 78 - 102
- [[Numerical Optimization by Nocedal]] pp 245
- [[Elements of Statistical Learning by Hastie]] pp 43 - 56