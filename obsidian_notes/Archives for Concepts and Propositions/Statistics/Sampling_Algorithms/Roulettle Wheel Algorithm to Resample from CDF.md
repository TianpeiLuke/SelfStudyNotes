---
tags:
  - concept
  - statistics/monte_carlo_simulation
  - evolutionary_computation
keywords:
  - roulettle_wheel_algorithm
topics:
  - statistics/monte_carlo
name: Roulettle Wheel Algorithm to Sample with CDF
date of note: 2024-08-28
---

## Concept Definition

>[!important]
>**Name**: Roulettle Wheel Algorithm to Resample with CDF

>[!important] Definition
>The simplest way of achieving the *sampling* from given selection probability is known as the **roulette wheel algorithm**.
>
>The **roulette wheel algorithm** is described as below
>- *Require*: a *cumulative distribution* $F$ where $$F(i) = \sum_{j=1}^{i}P(j)$$
>- *Require*: the parent population $$\mathcal{S} := \left\{ x_{1} \,{,}\ldots{,}\, x_{\mu}\right\} $$
>- *Require*: the size of *resampled population* $\lambda$
>- $\mathcal{M} = \emptyset$
>- For $k=1\,{,}\ldots{,}\,\lambda$:
>	- Generate a random number $$r\sim \text{Uniform}[0,1]$$
>	- **Estimating the quantile function of C.D.F.** $$i = F^{-1}(r) := \inf\left\{i: F(i) \ge r \right\}$$
>		- Set $i=1$  
>		- While $F(i) < r$
>			- $i \leftarrow i+1$
>	- Include $x_{i}$ into the **resampled population** $$\mathcal{M} \leftarrow \mathcal{M} \cup \left\{ x_{i} \right\}$$
>- *Return* resampled population $\mathcal{M}$

^a9dfe5

- [[Quantile Function]]
- [[Multinomial Distribution]]
- [[Cumulative Distribution Function of Random Variable]]


## Explanation





-----------
##  Recommended Notes and References


- [[Bootstrap Method]]
- [[Parent Selection for Evolutionary Computation]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Quantile Function]]

- [[Monte Carlo and Applications]]
- [[Accept-Reject Sampling]]
- [[Particle Filter or Sampling-Importance-Resampling]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 302
- [[Introduction to Evolutionary Computing by Eiben]] pp 80 - 87
- [[An Introduction to Bootstrap by Efron]]
- [[Monte Carlo Statistical Methods by Robert]]