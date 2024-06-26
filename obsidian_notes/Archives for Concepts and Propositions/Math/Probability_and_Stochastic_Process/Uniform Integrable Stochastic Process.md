---
tags:
  - concept
  - math/stochastic_process
keywords:
  - uniform_integrable_stochastic_process
topics:
  - stochastic_process
name: Uniform Integrable Stochastic Process
date of note: 2024-06-18
---

## Concept Definition

>[!important]
>**Name**: Uniform Integrable Stochastic Process

>[!important] Definition
>A *stochastic process* $(X_{t})$ is called **uniformly integrable** if 
>$$
>\begin{align*}
> \lim_{ n \to \infty } \sup_{t} \mathbb{E}\left[ \; \lvert X_{t} \rvert\; \mathbb{1}\left\{ \lvert X_{t} \rvert > n  \right\}  \right] = 0
>\end{align*}
>$$
>where the *supremum* is over $[0,T]$ if the process is defined in finite interval, and $[0, \infty)$ if the process is considered over $[0, \infty)$.
>
>That is, $\mathbb{E}\left[ \; \lvert X_{t} \rvert\; \mathbb{1}\left\{ \lvert X_{t} \rvert > n  \right\}  \right] \stackrel{n\to \infty}{\to} 0$ **uniformly** in $t$.

- [[Stochastic Process]]
- [[Uniform Integrable Family of Functions]]

## Explanation

>[!important]


## Local Martingale

- [[Local Martingale]]

## Dirichlet Class

- [[Dirichlet Class of Stochastic Process]]



-----------
##  Recommended Notes and References

- [[Stochastic Process]]
- [[Uniform Integrable Family of Functions]]


- [[Introduction to Measure Theory by Tao]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 185