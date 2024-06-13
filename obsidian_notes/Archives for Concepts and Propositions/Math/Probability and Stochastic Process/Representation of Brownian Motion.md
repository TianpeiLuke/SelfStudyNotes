---
tags:
  - concept
  - math/stochastic_process
keywords:
  - brownian_motion
  - karhunen_loeve_expansion
topics:
  - stochastic_process
name: Expansion of Brownian Motion
date of note: 2024-06-05
---

## Concept Definition

>[!important]
>**Name**: Expansion of Brownian Motion


![[Haar Wavelet Function#^e6b662]]

- [[Haar Wavelet Function]]

![[Schauder Function#^8d5f5c]]

- [[Schauder Function]]



>[!important] Proposition
>Let $\{ \xi_{n}, n \ge 0 \}$ be a sequence of *i.i.d. $\mathcal{N}(0,1)$ random variables.* $\{ s_{k} \}_{k=0}^{\infty}$ be the sequence of **Schauder functions.**
>
>Then
>$$
>W(\omega, t) = \sum_{k=0}^{\infty}\xi_{k}(\omega)\;s_{k}(t).
>$$
>**converge uniformly** for all $t\in [0,1]$  and for $\omega\in \Omega$ **almost surely**.
>
>Furthermore, 
>- $(W(\omega, t), t \in [0,1])$ is a **Brownian motion**.
>- for $\omega\in \Omega$ **almost surely**, *the sample path* $$t \to W(\omega, t)$$ is **continuous** $\mathcal{C}[0,1].$

- [[Introduction to Stochastic Differential Equations by Evans]]

>[!important]
>This construction above is called the **Lévy construction** of Brownian motion.
>
>The expansion 
>$$
>W(\omega, t) = \sum_{k=0}^{\infty}\lambda_{k}\,\xi_{k}(\omega)\;s_{k}(t).
>$$
>is also called **Haar–Schauder expansion**.

- [[Lectures on Gaussian Processes by Lifshits]] pp 103
- This is different from the **Karhunen-Loève Expansion** [[Representation of Gaussian Random Function in Hilbert Space]]



>[!important]
>The covariance function of this random function 
>$$
>\begin{align*}
>K(t, s) &= \mathbb{E}\left[W(\cdot, t)\,W(\cdot, s)\right]\\
>&= \mathbb{E}\left[\sum_{k=0}^{\infty}\xi_{k}(\omega)\;s_{k}(t) \sum_{k=0}^{\infty}\xi_{k}(\omega)\;s_{k}(s)\right]\\
>&= \sum_{k=0}^{\infty}\,s_{k}(t)s_{k}(s) \\
>&= \min\{ s, t \}
>\end{align*} 
>$$





## Explanation





-----------
##  Recommended Notes and References

- [[Brownian Motion Wiener Process]]
- [[Gaussian Random Function]]
- [[Representation of Gaussian Random Function in Hilbert Space]]


- [[Introduction to Stochastic Differential Equations by Evans]]