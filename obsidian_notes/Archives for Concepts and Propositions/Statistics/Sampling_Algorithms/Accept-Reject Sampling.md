---
tags:
  - concept
  - statistics/monte_carlo_simulation
keywords:
  - accept_reject_algorithm
topics:
  - statistics/monte_carlo
name: Rejection Sampling
date of note: 2024-07-04
---

## Concept Definition

>[!important]
>**Name**: Rejection Sampling or *Accept-Reject Algorithm*


![[Fundamental Theorem of Simulation#^46dad7]]

>[!important] Definition
>The **Accept-Reject algorithm** for sampling $Y \sim f$ is as follows:
>- Generate $$X \sim g, \quad U \sim \mathcal{U}[0,1]$$
>- **Accept** $Y = X$ If $$U \le \frac{f(X)}{M\,g(X)}$$
>- Otherwise return $1$.

- [[Fundamental Theorem of Simulation]]




## Explanation





-----------
##  Recommended Notes and References

- [[Fundamental Theorem of Simulation]]



- [[All of Statistics A Concise Course by Wasserman]] pp 404
- [[Monte Carlo Strategies in Scientific Computing by Liu]] pp 24 - 25
- [[Monte Carlo Statistical Methods by Robert]] pp 51



- [[Probabilistic Graphical Models by Koller]] pp 491
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 477 - 537
- [[Deep Learning by Goodfellow]] pp 590
- [[Deep Learning Foundations and Concepts by Bishop]] pp 429