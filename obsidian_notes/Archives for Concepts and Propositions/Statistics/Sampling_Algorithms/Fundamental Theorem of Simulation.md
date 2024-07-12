---
tags:
  - concept
  - statistics/monte_carlo_simulation
keywords:
  - fundamental_monte_carlo
topics:
  - statistics/monte_carlo
name: Fundamental Theorem of Monte Carlo
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Fundamental Theorem of Simulation

>[!important] Theorem
>Simulating $$X \sim f(x)$$ is **equivalent** to simulating $$(X, U) \sim \mathcal{U}\left\{ (x,u):  0 < u < f(x) \right\}. $$ where $\mathcal{U}(A)$ s the *uniform distribution* over set $A$ and the random variable $U$ is called an **auxiliary variable**.
>
>In other word, if $f$ is a *p.d.f.* of random variable $X$, we can write
>$$
>f(x) = \int_{0}^{f(x)}du.
>$$
>Thus $f$ is the **marginal density** of the *joint distribution* $$(X, U) \sim \mathcal{U}\left\{ (x,u):  0 < u < f(x) \right\}. $$


- [[Hypograph or Subgraph of Function]]
- [[Probability Density Function of Random Variable]]
- [[Fubini Theorem]]
- [[Monte Carlo Statistical Methods by Robert]] pp 47

>[!important] Corollary
>Let $X \sim f(x)$ and let $g(x)$ be a *density function* that satisfies 
>$$f(x) \le M g(x)$$ for some constant $M > 1$. 
>
>Then, to simulate $$X \sim f(x),$$ it is **sufficient** to 
>1. generate $$Y \sim g$$
>2. generate $$U|Y=y \sim \mathcal{U}(0, Mg(y))$$ 
>
>until $0 < u <f(y).$

^46dad7

- [[Accept-Reject Sampling]]

## Explanation

>[!info]
>we can generate from the joint distribution of $(X, U)$ by just generating **uniform random variables** on the **constrained set**
>$$\left\{ (x,u):  0 < u < f(x) \right\}$$

>[!info]
>Moreover, since the **marginal distribution** of $X$ is the original **target distribution**, $f$, by generating a uniform variable on $\left\{ (x,u):  0 < u < f(x) \right\}$, we have *generated a random variable from* $f$. And this generation was produced **without using $f$** other than through the calculation of $f(x)$.




-----------
##  Recommended Notes and References



- [[Markov Chain Monte Carlo Methods]]


- [[Monte Carlo Statistical Methods by Robert]]
- [[Monte Carlo Strategies in Scientific Computing by Liu]]
- Wikipedia [Monte_Carlo_method](https://en.wikipedia.org/wiki/Monte_Carlo_method)