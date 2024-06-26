---
tags:
  - concept
  - statistics/estimation
keywords:
  - confidence_interval
topics:
  - statistics
name: Confidence Interval
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Confidence Interval

>[!important] Definition
>A **$(1-\alpha)$ confidence interval** for a parameter $\theta$ is an interval $$C_{n} = (a, b)$$ where
>$$
>a := a\left( X_{1} \,{,}\ldots{,}\, X_{n} \right), \quad b := b\left( X_{1} \,{,}\ldots{,}\, X_{n} \right)
>$$
>are *functions* of i.i.d. random variables such that for any $\theta\in \Theta$,
>$$
>\mathcal{P}_{\theta}\left[ \theta \in C_{n} \right] \ge 1 - \alpha
>$$
>We call $(1-\alpha)$ the **coverage** of the *confidence internal*. 

>[!info]
>In other words, $(a, b)$ traps the parameter $\theta$ with probability $1-\alpha$. 

## Explanation





-----------
##  Recommended Notes and References

- [[Point Estimator]]

- [[Probability Distribution of Random Variable]]
- [[Independent Random Variables]]

- [[All of Statistics A Concise Course by Wasserman]]