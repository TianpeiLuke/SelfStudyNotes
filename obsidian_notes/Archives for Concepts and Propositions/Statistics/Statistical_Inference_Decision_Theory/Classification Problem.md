---
tags:
  - concept
  - statistics/estimation
  - statistics/inference
keywords:
  - classification_problem
topics:
  - statistics/estimation
  - statistics/inference
name: Classification Problem
date of note: 2024-06-11
---

## Concept Definition

>[!important]
>**Name**: Classification Problem

![[Statistical Estimation Problem#^994e95]]

>[!important] Definition
>A  **classification problem** studies the relationship between 
>- the **response variables**  $Y\in \{ 1 \,{,}\ldots{,}\, K\}$ and 
>- the **covariate variables** $X := (X^{1} \,{,}\ldots{,}\,X^{d})\in \mathbb{R}^{d}.$
>
>The goal is to find a function $h\in \mathcal{H} \subset \left\{ r:\mathbb{R}^d \to \{ 1 \,{,}\ldots{,}\, K\}\right\}$ such that the **classification loss** is minimized
>$$
> \min_{r\in \mathcal{H}} \mathbb{E}_{ \mathcal{P} }\left[ L(h(X), Y)    \right]
>$$
>where $(X, Y)\sim \mathcal{P}$ for some distribution $\mathcal{P}$.

^cae88d

- [[Empirical Risk Minimization]]
- [[Statistical Estimation Problem]]
- [[Parametric Models]]

## Explanation

- [[Supervised Learning and Unsupervised Learning]]

### Classification Problem

- [[k Nearest Neighbor Classification]]
- [[Logistic Regression]]
- [[AdaBoost Algorithm]]
- [[Support Vector Machine]]
- [[Artificial Neural Network and Deep Learning]]
- [[Conditional Random Field]]
- [[Naive Bayes Model]]


-----------
##  Recommended Notes and References


- [[Regression Problem]]

- [[Parametric Models]]
- [[Empirical Risk Minimization]]
- [[Statistical Decision Problem]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]

- [[Elements of Statistical Learning by Hastie]]
- [[All of Statistics A Concise Course by Wasserman]] pp 208
- [[Mathematical Statistics by Shao]] 