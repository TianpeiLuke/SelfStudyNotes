---
tags:
  - concept
  - math/functional_analysis
  - math/probability
  - math/stochastic_process
keywords:
  - invariant_measure
  - stationary_distribution
topics:
  - stochastic_process
  - functional_analysis
name: Invariant Measure and Stationary Distribution
date of note: 2024-06-05
---

## Concept Definition

>[!important]
>**Name**: Invariant Measure and Stationary Distribution





## Markov Process

>[!important] Definition
>A *$\sigma$-finite measure* $\pi$ is **invariant** for the *transition kernel* $K$ (and *for the associated chain*)  if
>$$
>\pi(A) := \int_{\mathcal{X}}K(x, A)\;\pi(dx),\; \quad \forall A\in \mathcal{B}[\mathcal{X}].
>$$
>
>An invariant measure is also called a **stationary distribution** or **invariant distribution**.

- [[Integral Operator associated with Transition Kernel]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- [[Finite and sigma-Finite Measure]]

## Explanation

>[!info]
>For a Markov chain $X_{n}$ with invariant distribution $\pi$,   $$X_{0} \sim \pi \implies X_{n}\sim \pi.$$
>
>Thus the Markov chain is **stationary in distribution.**

- [[Stationary Process]]




-----------
##  Recommended Notes and References

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]


- [[Hilbert Space]]
- [[Complete Orthonormal Basis of Hilbert Space]]

- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Real Analysis by Royden]]

- [[Monte Carlo Statistical Methods by Robert]]
- [[Probability and Measure by Billingsley]]

