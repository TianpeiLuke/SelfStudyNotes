---
tags:
  - concept
  - math/stochastic_process
keywords:
  - ito_integration_step_process
topics:
  - stochastic_process
name: Itô Integration of Step Process
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Itô Integration of Step Process

![[Step Process#^57feed]]

>[!important] Definition
>Let $(X_{t}, t \in [0,T])$ be a *step process* and $(W_{t}, t \in [0,T])$ be *Wiener process*.
>
>Define the **Itô stochastic Integration** of $(X_{t})$ on $[0,T]$ as 
>$$
>\begin{align}
>\int_{0}^{T} X_{t}\;dW := \sum_{i=0}^{n-1}\,X_{i}\left(W_{t_{i+1}} - W_{t_{i}}\right)
>\end{align}
>$$

^9a6b44

- [[Step Process]]
- [[Progressively Measurable Stochastic Process]]
- [[Brownian Motion Wiener Process]]

## Explanation

>[!important]
>By definition, the *stochastic integral* of *(progressively measurable) stochastic process* is a **random variable**.
>$$
>I: \omega \to \int_{0}^{T} X_{t}(\omega)\;dW(\omega) \in \mathbb{R}
>$$

## Properties

>[!important] Proposition
>Let $(X_{t})$ and $(Y_{t})$ be step processes, and $a, b\in \mathbb{R}$
>- **Linearity**: $$\int_{0}^{T} \left(a\,X_{t} + b\,Y_{t}\right)\;dW  = a\,\int_{0}^{T} X_{t}\;dW + b\,\int_{0}^{T} Y_{t}\;dW$$
>- **Centered**: the expectation of *Itô stochastic Integration* is zero, i.e. $$\mathbb{E}\left[  \int_{0}^{T} X_{t}\;dW \right] = 0$$
>- **Itô Isometry**: 
>  $$
>  \mathbb{E}\left[ \left(\int_{0}^{T} X_{t}\;dW \right)^2 \right] = \mathbb{E}\left[  \int_{0}^{T} X^2_{t}\;dt \right]
> $$

- [[Ito Isometry]]
- [[Progressively Measurable Stochastic Process]]
- [[Isometry and Isometric isomorphism]]

>[!info] Proof (part 2)
>$$
>\begin{align*}
>\mathbb{E}\left[  \int_{0}^{T} X_{t}\;dW \right] &= \mathbb{E}\left[  \sum_{i=0}^{n-1}\,X_{i}\left(W_{t_{i+1}} - W_{t_{i}}\right) \right] 
>\end{align*}
>$$
>We note that $(X_{s})$ is **adapted** in $(\mathscr{F}_{s})$ and $\mathscr{F}_{s}$ is **independent** with $(W_{t} - W_{s})$ for any $t >s$, so $X_{i}$ is *independent from* $(W_{t_{i}+1} - W_{t_{i}})$
>$$
>\begin{align*}
>LHS&=  \sum_{i=0}^{n-1}\,\mathbb{E}\left[ X_{i}\right] \;\,\mathbb{E}\left[ \left(W_{t_{i}+1} - W_{t_{i}}\right) \right] \\
>&= 0
>\end{align*}
>$$
>since $W_{t_{i}+1} - W_{t_{i}}$ is zero mean Gaussian.

- [[Adapted Stochastic Process and Non-anticipating Process]]

>[!info] Proof (part 3)
>$$
>\begin{align*}
>\mathbb{E}\left[  \left(\int_{0}^{T} X_{t}\;dW\right)^2 \right] &= \mathbb{E}\left[  \sum_{i=0}^{n-1}\sum_{j=0}^{n-1}\,X_{i}X_{j}\left(W_{t_{i+1}} - W_{t_{i}}\right)\left(W_{t_{j}+1} - W_{t_{j}}\right)  \right] 
>\end{align*}
>$$
>- If $j < i$, then $$(W_{t_{j+1}} - W_{t_{j}}) \perp (W_{t_{i+1}} - W_{t_{i}}).$$ We have
>$$
>\begin{align*}
>&\mathbb{E}\left[X_{i}X_{j}\left(W_{t_{i+1}} - W_{t_{i}}\right)\left(W_{t_{j+1}} - W_{t_{j}}\right)  \right] \\
>&= \underbrace{\mathbb{E}\left[  X_{i}X_{j}\left(W_{t_{i+1}} - W_{t_{i}}\right)\right]}_{<\infty}\; \underbrace{\mathbb{E}\left[ \left(W_{t_{j+1}} - W_{t_{j}}\right)  \right]}_{=0} \\
>&= 0
>\end{align*}
>$$
>
>So
>$$
>\begin{align*}
>\mathbb{E}\left[  \left(\int_{0}^{T} X_{t}\;dW\right)^2 \right] &= \mathbb{E}\left[  \sum_{i=0}^{n-1}\sum_{j=0}^{n-1}\,X_{i}X_{j}\left(W_{t_{i+1}} - W_{t_{i}}\right)\left(W_{t_{j+1}} - W_{t_{j}}\right)  \right] \\
>&= \sum_{i=0}^{n-1} \mathbb{E}\left[ X_{i}^2\left(W_{t_{i+1}} - W_{t_{i}}\right)^2 \right]\\
>&= \sum_{i=0}^{n-1} \mathbb{E}\left[ X_{i}^2\right]\; \mathbb{E}\left[\left(W_{t_{i+1}} - W_{t_{i}}\right)^2 \right]
>\end{align*}
>$$
>
>By property of Wiener process,  $W_{t_{i+1}} - W_{t_{i}} \sim \mathcal{N}(0, t_{i+1} - t_{i})$ so $$\mathbb{E}\left[\left(W_{t_{i+1}} - W_{t_{i}}\right)^2 \right] = t_{i+1} - t_{i}$$
>
>Thus
>$$
>\begin{align*}
>LHS&=  \mathbb{E}\left[\sum_{i=0}^{n-1}  X_{i}^2 (t_{i+1} - t_{i})\right]\;\\
>&= \mathbb{E}\left[\int_{T} X_{t}^2 dt\right]
>\end{align*}
>$$
>Q.E.D.

- [[Brownian Motion Wiener Process]]




-----------
##  Recommended Notes and References

- [[Brownian Motion Wiener Process]]
- [[Gaussian Process]]

- [[Riemann–Stieltjes Integration]]
- [[Simple Integral of Simple Functions]]

- [[Ito Stochastic Integration]]

- [[Introduction to Stochastic Differential Equations by Evans]]