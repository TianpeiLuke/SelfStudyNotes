---
tags:
  - concept
  - math/stochastic_process
  - math/functional_analysis
keywords:
  - resolvent
  - transition_function
  - Transition_Kernel
  - markov_process
topics:
  - stochastic_process
  - functional_analysis
name: Resolvant associated with Transition Kernel
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Resolvent associated with Transition Kernel

>[!important] Definition
>A **resolvent** associated with *the transition kernel* $K$ is a *kernel* of the form
>$$
>K_{\epsilon}\left(x, A\right) := (1- \epsilon)\;\sum_{i=0}^{\infty}\epsilon^i\;K^i(x, A)
>$$
>where $\epsilon\in (0,1)$.

- [[Markov Transition Kernel and Transition Function]]
- [[Chapman-Kolmogorov Equation]]






## Explanation

>[!important]
>Given an initial distribution $\pi$, we can associate with the **kernel** $K_{\epsilon}$ a **chain** $(X_{n}^{\epsilon})$ which formally corresponds to a **subchain** *of the original chain* $(X_{n})$, where the indices in the subchain are *generated from* **a geometric distribution** with *parameter* $1 - \epsilon$.



-----------
##  Recommended Notes and References

- [[Resolvent Operator and Spectrum of Linear Operator]]


- [[Markov Chain and Markov Process]]


- Oksendal, B. (2013). _Stochastic differential equations: an introduction with applications_. Springer Science & Business Media pp 143
- [[Monte Carlo Statistical Methods by Robert]] pp 211