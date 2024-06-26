---
tags:
  - concept
  - math/stochastic_process
keywords:
  - white_noise_process
topics:
  - stochastic_process
name: White Noise Process
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: White Noise Process





## Explanation

>[!important]
>A white noise process $(\mathcal{W}_{t})$ should have the following properties
>1. for $t \neq s$, $$\mathcal{W}_{s} \perp \mathcal{W}_{t}$$ are *statistically independent*.
>2. $(\mathcal{W}_{t})$ is **stationary**, i.e. the joint distribution $$\mathcal{P}\left(\mathcal{W}_{t+1} \,{,}\ldots{,}\,\mathcal{W}_{t+n}\right)$$ does not depends on $t$
>3. **zero mean** $$\mathbb{E}\left[  \mathcal{W}_{t} \right] = 0$$
>   
>However, **no proper stochastic process satisfies all three conditions**.
>
>We have to define a *generalized stochastic process* as a random generalized function on **the space of tempered distributions** $\mathscr{S}'([0, \infty))$
>$$
>W: \Omega \to \mathscr{S}'([0, \infty))
>$$
>

- Oksendal, B. (2013). _Stochastic differential equations: an introduction with applications_. Springer Science & Business Media. (pp. 21)
- [[Space of Tempered Distributions]]



>[!example]
>One form of white noise is the **generalized mean-square derivative** of the **Brownian motion**.

- [[Brownian Motion Wiener Process]]


## White Noise Process on Space of Signed Measures

- [[Wiener Measure as Random Finitely Additive Measures]]



-----------
##  Recommended Notes and References

- [[Brownian Motion Wiener Process]]
- [[Gaussian Process]]

- [[Itô Stochastic Integration]]


- [[Wasserstein Distance]]
- [[Wasserstein Space]]

- [[Introduction to Stochastic Differential Equations by Evans]]
- Oksendal, B. (2013). _Stochastic differential equations: an introduction with applications_. Springer Science & Business Media.