---
tags:
  - concept
  - statistics/estimation
keywords:
  - point_estimator
  - bias_estimation
topics:
  - statistics
name: Bias of Point Estimator
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Bias of Point Estimator

>[!info] 
>Let $X_{1} \,{,}\ldots{,}\, X_{n}$ be $n$ independent identically distributed (i.i.d.) random variables from distribution $F$. 
>
>A **point estimator** $\hat{\theta}$ of a parameter $\theta$ is some function $g$ of $X_{1} \,{,}\ldots{,}\, X_{n}$:
>$$
>\hat{\theta}_{n} := g\left( X_{1} \,{,}\ldots{,}\, X_{n} \right)
>$$

- [[Point Estimator]]

>[!important] Definition
>The **bias** of *an estimator* is defined by
>$$
>\text{bias}( \hat{\theta} ) :=  \mathbb{E}_{\theta}[ \,\hat{\theta}\, ] - \theta
>$$
>where 
>$$
>\mathbb{E}_{\theta}[ \,\hat{\theta} \,] := \mathbb{E}_{\mathcal{P}_{\theta}}[\, \hat{\theta} \,]
>$$

>[!important] Definition
>We say that $\hat{\theta}$ is **unbiased** when 
>$$\mathbb{E}_{\theta}[ \,\hat{\theta}\, ] = \theta.$$

## Explanation





-----------
##  Recommended Notes and References


- [[Probability Distribution of Random Variable]]
- [[Independence of Events]]


- [[All of Statistics A Concise Course by Wasserman]]