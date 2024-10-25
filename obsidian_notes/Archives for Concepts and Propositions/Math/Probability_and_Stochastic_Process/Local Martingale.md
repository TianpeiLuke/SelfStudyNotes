---
tags:
  - concept
  - math/stochastic_process
keywords:
  - local_martingale
topics:
  - stochastic_process
name: Local Martingale
date of note: 2024-06-18
---

## Concept Definition

>[!important]
>**Name**: Local Martingale

>[!important] Definition
>An *adapted process* $(X_{t}, t\ge 0)$ is called a **local martingale** if there *exists* a sequence of *stopping times* $\{ \tau_{n} \}$, such that 
>- $\tau_{n} \to \infty$ as $n\to \infty$;
>- and for *each* $n$, the *stopped process* $$X_{t \wedge \tau_{n}}$$ is *uniformly integrable martingale* in $t$


- [[Adapted Stochastic Process and Non-anticipating Process]]
- [[Uniform Integrable Stochastic Process]]
- [[Local Property of Stochastic Process and Localizing Sequence]]
- [[Stopping Time of Filtration]]
- [[Martingale]]


- [[Introduction to Stochastic Calculus by Klebaner]] pp 195


## Explanation



## Uniformly Integrable Martingale

>[!important] Theorem
>A **local martingale** $X$ is a **uniformly integrable martingale** *if and only if* it is of **Dirichlet class**.

- [[Dirichlet Class of Stochastic Process]]


## Quadratic Variation

- [[Quadratic Variation and Covariation of Stochastic Process]]

## Stochastic Integration

>[!important]
>An **Itô integral** $$\int_{0}^{t}X_{s}dW_{s}$$ is a **local martingale**.
>
>For every *stopping time* $\tau_{n}$, 
>$$
>\int_{0}^{\tau_{n} \wedge t}X_{s}dW_{s} := \int_{0}^{t}\mathbb{1}\left\{s \le \tau_{n} \right\}X_{s}\,dW_{s}
>$$
>is **uniformly integrable**.

- [[Stopping Time and Stochastic Integral]]
- [[Ito Stochastic Integration]]




-----------
##  Recommended Notes and References

- [[Brownian Motion Wiener Process]]

- [[Adapted Stochastic Process and Non-anticipating Process]]
- [[Uniform Integrable Stochastic Process]]
- [[Local Property of Stochastic Process and Localizing Sequence]]
- [[Stopping Time of Filtration]]
- [[Martingale]]


- [[Introduction to Stochastic Calculus by Klebaner]]