---
tags:
  - concept
  - statistics/estimation
  - statistics/inference
keywords:
  - linear_regression
topics:
  - statistics/estimation
  - statistics/inference
name: Linear Regression
date of note: 2024-06-11
---

## Concept Definition

>[!important]
>**Name**: Linear Regression

![[Regression Problem#^cae88d]]


>[!important] Definition
>A **linear regression model** assumes that the conditional expectation of *response* $Y$ given *covariates* $X := (X^1 \,{,}\ldots{,}\,X^{d})$ is *linear*. 
>
>That is
>$$
> r(X) = \mathbb{E}_{ \mathcal{P} }\left[Y | X  \right] = \sum_{i=1}^{d}\beta_{i}\,X^{i} + \beta_{0}
>$$

- [[Least Square Estimation]]

>[!important] Definition
>A **linear regression model** can be represented as the following equation:
>$$
>Y = \sum_{i=1}^{d}\beta_{i}\,X^{i} + \beta_{0} + \epsilon,
>$$
>where the *noise term* $\epsilon \sim \mathcal{N}(0, \sigma^2)$ and the noise is *statistically independent* from the *covariates* $$\epsilon \perp (X^1 \,{,}\ldots{,}\,X^{d}).$$
>- The **coefficient** $\hat{\beta}_{j}$ represents the *additional contribution* of $X^{j}$ on $Y$, *after* $X^{j}$ has been *adjusted* for $(X^1 \,{,}\ldots{,}\,X^{j-1}, X^{j+1} \,{,}\ldots{,}\,X^{d}).$

^24812d

- [[Gaussian Random Variable]]
- [[Gaussian Random Vector]]

>[!important]
>For $d=1$, the *linear regression* model is 
>$$
>Y = \beta_{1}\,X  + \epsilon
>$$
>We describe it as **"regression of $Y$ on $X$"** or **regress $Y$ on $X$.**


## Explanation

>[!info]
>We can relax the above independent assumption. Instead of assuming independence, we assume that 
>$$
>\epsilon |X \sim \mathcal{N}(0, \sigma^2) \implies Y|X \sim \mathcal{N}(\mu, \sigma^2)
>$$

## I.I.D Samples and Compact Representation

>[!important] Definition
>Let $\left\{ (X_{s}, Y_{s}),\; s=1\,{,}\ldots{,}\,m \right\}$ be a set of $m$ i.i.d. random variables from some distribution $\mathcal{P}$. 
>
>Assume that $Y_{s}$ given $X_{s}$ is represented by a **linear regression model**
>$$
>Y_{s} = \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0} + \epsilon_{s},\; \quad s=1 \,{,}\ldots{,}\,m.
>$$
>where $(\epsilon_{s})_{1}^{m}$ are all i.i.d. with $\mathcal{N}(0,\sigma^2)$

^b406ef

>[!important] Definition
>Denote 
>- $Y := (Y_{1} \,{,}\ldots{,}\,Y_{m})\in \mathbb{R}^{m}$,  
>- $$X = \left[ \begin{array}{ccccc}X_{1}^{1}& X_{1}^{2}& \ldots & X_{1}^{d} & 1\\ X_{2}^{1}& X_{2}^{2}& \ldots & X_{2}^{d}& 1 \\ \ldots & \ldots & \ldots & \ldots & \ldots \\ X_{m}^{1}& X_{m}^{2}& \ldots & X_{m}^{d} & 1  \end{array} \right]\in \mathbb{R}^{m\times (d+1)},$$ and 
>- $\beta = (\beta_{1} \,{,}\ldots{,}\,\beta_{d}, \beta_{0})\in \mathbb{R}^{d+1}$
>- $\epsilon = (\epsilon_{1} \,{,}\ldots{,}\,\epsilon_{m})\in \mathbb{R}^{m}$
>
>The above **linear regression model** can be represented in **compact form** as
>$$
>Y = X\,\beta + \epsilon
>$$

^8d6149

## Multiple Regression

>[!important] Definition
>Assume $Y =(Y^1 \,{,}\ldots{,}\,Y^m)\in \mathbb{R}^m$ is a **vector response**.
>
 >For each response variable, the **linear regression model** can be represented as 
>$$
>Y^{j} = \sum_{i=1}^{d}\beta_{i}^{j}\,X^{i} + \beta_{0}^{j} + \epsilon^{j}, \quad j=1 \,{,}\ldots{,}\,m
>$$ 
>where $\epsilon^j | X \sim \mathcal{N}(0, \sigma_{j}^2)$ and $(\epsilon^1 \,{,}\ldots{,}\,\epsilon^{m})$ are *conditional independent*. 
>
>In compact form, it is written as
>$$
>Y = X\,\beta + \epsilon
>$$
>This model is called the **multiple regression model**.

- [[Conditional Independence]]

## Least Square Estimate

![[Least Square Estimation#^9775a7]]

- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]

![[Least Square Estimation Solution and Geometric Interpretation#^c0f78a]]


## Generalized Linear Model

- [[Generalized Linear Models]]
- [[Logistic Regression]]



-----------
##  Recommended Notes and References

- [[Regression Problem]]
- [[Maximum Likelihood Estimation]]
- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Generalized Linear Models]]



- [[Elements of Statistical Learning by Hastie]]
- [[All of Statistics A Concise Course by Wasserman]] pp 210 
- [[Mathematical Statistics by Shao]] 
- [[Elements of Statistical Learning by Hastie]] pp 43 - 56
- [[Deep Learning Foundations and Concepts by Bishop]] pp 112 - 120
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 65 - 71