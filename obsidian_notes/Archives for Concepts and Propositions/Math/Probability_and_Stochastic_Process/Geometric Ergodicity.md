---
tags:
  - concept
  - math/stochastic_process
keywords:
  - geometric_ergodicity
topics:
  - stochastic_process
name: Geometric Ergodicity
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Geometric Ergodicity

![[Positive Recurrent Markov Chain#^17e86b]]


>[!important] Definition
>A Markov chain $(X_{n})$ is said to be **geometrically $h$-ergodic**, with $h \ge 1$ on $\mathcal{X}$, if
>- $(X_{n})$ is **Haris positive**, 
>- with **stationary distribution** $\pi$, 
>- and $(X_{n})$ satisfies $$\mathbb{E}_{ \pi }\left[ h(X)  \right] < \infty,$$
>- and there exists $r_{h} > 1$ such that $$\sum_{n=1}^{\infty}r_{h}^{n}\,\lVert K^{n}(x, \cdot) - \pi \rVert_{h} < \infty, \quad \forall x\in \mathcal{X}.$$
>	- where **$h$-norm** for the *measure* $\mu$ $$\lVert \mu \rVert_{h} := \sup_{|g| \le h} \left\lvert  \int g(x)\,\mu(dx) \right\rvert := \sup_{|g| \le h}\mathbb{E}_{ \mu }\left[  g(X) \right]$$
>  
>The case of $h=1$ corresponds to the **geometrically ergodicity** of $(X_{n})$   

^83bc87

- [[Positive Recurrent Markov Chain]]
- [[Invariant Measure and Stationary Distribution]]
- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]
- [[Total Variation between Measures]]


## Explanation





-----------
##  Recommended Notes and References


- [[Geometric Ergodic Theorem]]


- [[Expectation of Random Variable]]
- [[Measure Space and Countably Additive Measure]]


- [[Monte Carlo Statistical Methods by Robert]] pp 236
