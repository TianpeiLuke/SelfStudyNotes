---
tags:
  - concept
  - math/stochastic_process
  - math/probability
keywords:
  - stopping_time
topics:
  - probability
  - stochastic_process
name: Stopping Time and Stochastic Integral
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Stopping Time and Stochastic Integral


>[!important] Definition
>If $X\in \mathbb{L}^2(0,T)$, and $\tau$ is a *stopping time* with respect to *filtration* $\left\{ \mathcal{F}_{t}, t\ge 0 \right\}$ where $$\mathcal{F}_{t} :=  \sigma(W_{s}, s\le t)$$ and $0 \le \tau \le T$, we define 
>$$
>\int_{0}^{\tau}X_{s}dW_{s} := \int_{0}^{T}\mathbb{1}\left\{s \le \tau \right\}X_{s}\,dW_{s}.
>$$

- [[Stopping Time of Filtration]]
- [[Stochastic Differential Equations]]
- [[Martingale]]
- [[Filtration]]
- [[Random Element and Random Variable]]


## Explanation



## Properties

>[!important] Proposition
>Let $X\in \mathbb{L}^2(0,T)$ and $\tau$ be a **stopping time** with $0 \le \tau \le T.$
>
>Then
>- **Centered**: $$\mathbb{E}\left[  \int_{0}^{\tau}X\,dW \right] = 0.$$
>- **Itô Isometry**: $$\mathbb{E}\left[  \left(\int_{0}^{\tau}X\,dW\right)^2 \right] = \mathbb{E}\left[  \int_{0}^{\tau}X^2\,dt \right].$$

- [[Introduction to Stochastic Differential Equations by Evans]] pp 105

>[!info]
>We can see that since $\tau$ is stopping time, $\mathbb{1}\{ t \le \tau  \}\in \mathbb{L}^2(0,T)$, by *property of Itô integral*:
>$$
>\mathbb{E}\left[  \int_{0}^{\tau}X\,dW \right] = \mathbb{E}\left[  \int_{0}^{T}\mathbb{1}\{ t \le \tau  \}X\,dW \right] = 0
>$$
>and
>$$
>\begin{align*}
>\mathbb{E}\left[  \left(\int_{0}^{\tau}X\,dW\right)^2 \right] &= \mathbb{E}\left[  \left(\int_{0}^{T}\mathbb{1}\{ t \le \tau  \}X\,dW \right)^2 \right]\\
>&= \mathbb{E}\left[  \int_{0}^{T}\left(\mathbb{1}\{ t \le \tau  \}X\,\right)^2 dt \right]\\
>&= \mathbb{E}\left[  \int_{0}^{\tau}X^2 dt \right]
>\end{align*}
>$$




-----------
##  Recommended Notes and References

- [[Infinitesimal Generator of Stochastic Differential Equation]]
- [[Infinitesimal Generator of Brownian Motion and Laplacian]]


- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]

- [[Probability and Measure by Billingsley]]
- [[A Probability Path by Resnick]]