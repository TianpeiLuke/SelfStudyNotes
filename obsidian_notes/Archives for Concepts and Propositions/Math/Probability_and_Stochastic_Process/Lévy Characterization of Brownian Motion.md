---
tags:
  - concept
  - math/stochastic_process
keywords:
  - levy_characterization_brownian_motion
topics:
  - stochastic_process
name: Lévy Characterization of Brownian Motion
date of note: 2024-06-18
---

## Concept Definition

>[!important]
>**Name**: Lévy Characterization of Brownian Motion

>[!important] Theorem (Lévy, Martingale)
>Let $(X_{t}, t \ge 0)$ be a **continuous martingale**, i.e. the sample path
>$$
>t \mapsto X_{t}(\omega)
>$$
>is *continuous* for all $\omega\in \Omega,$ and **$X_{0} = 0$**, and suppose that
>$$X_{t}^2 - t$$ is a **martingale.**
>
>Then $X$ is a **Brownian motion**.

^da976c

- [[Continuous Function]]
- [[Martingale]]
- [[Brownian Motion Wiener Process]]
- Rogers, L. C., & Williams, D. (2000). _Diffusions, markov processes, and martingales: Volume 1, foundations_ (Vol. 1). Cambridge university press. pp 2


>[!important] Theorem (Lévy, Local Martingale)
>A *stochastic process* $(X_{t}, t \ge 0)$ with $X_{0} = 0$ is a **Brownian motion** *if and only if* 
>- it is a **continuous local martingale** with
>- **quadratic variation process**
>$$
>\begin{align*}
> \left[ X, X \right](t) = t 
>\end{align*}
>$$

^0e9de9

- [[Stochastic Process]]
- [[Local Martingale]]
- [[Quadratic Variation and Covariation of Stochastic Process]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 203
- [[Stochastic Integral of Brownian Motion]]


## Explanation





-----------
##  Recommended Notes and References


- [[Brownian Motion Wiener Process]]
- [[Quadratic Variation and Covariation of Stochastic Process]]

- [[Continuous Function]]
- [[Stochastic Process]]
- [[Martingale]]


- [[Introduction to Stochastic Calculus by Klebaner]]