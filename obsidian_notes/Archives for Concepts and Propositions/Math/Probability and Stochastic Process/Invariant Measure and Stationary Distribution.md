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

>[!important] Definition
>A *$\sigma$-finite measure* $\pi$ is **invariant** for the *transition kernel* $K$ (and *for the associated chain*)  if
>$$
>\pi(A) := \int_{\mathcal{X}}K(x, A)\;\pi(dx),\; \quad \forall A\in \mathcal{B}[\mathcal{X}].
>$$
>
>An invariant measure is also called a **stationary distribution** or **invariant distribution**.

^56092f

- [[Integral Operator associated with Transition Kernel]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- [[Finite and sigma-Finite Measure]]


>[!important] Definition
>Let $(X_{n})$ be a *$\mu$-irreducible chain*.
>
>If there exists an *invariant probability measure* $\pi$ such that 
>$$
>\pi(B) = \int_{\mathcal{X}}K(x,B)\,\pi(dx),\quad \forall B\in \mathcal{B}(\mathcal{X}),
>$$
>then the chain is **positive**.

- [[Irreducibility of Markov Chain]]

>[!important] Definition
>Let $(X_{n})$ be a *$\mu$-irreducible chain*.
>
>If $(X_{n})$ is *recurrent* but there does not exists a finite invariant measure $\pi$, then the chain is **null recurrent**.

- [[Recurrent Markov Chain]]


## Explanation

>[!info]
>For a Markov chain $X_{n}$ with invariant distribution $\pi$,   $$X_{0} \sim \pi \implies X_{n}\sim \pi.$$
>
>Thus the Markov chain is **stationary in distribution.**

- [[Stationary Process]]

## Functional Analysis

>[!important]
>If $\mu$ is a *positive measure*, by [[Riesz-Markov Representation Theorem]], we can represent
>$$
>\mu\,f := \int_{\mathcal{X}}f(x)d\mu(x).
>$$
>By the definition of transition kernel [[Markov Transition Kernel and Transition Function]],   
>- $\mu\,K$ is a **positive measure** on $\mathcal{B}(\mathcal{X})$ defined as $$\mu\,K (A) := \mu\,K(\cdot, A) = \int_{\mathcal{X}}K(x, A)\,d\mu(x), \quad \forall A\in \mathcal{B}(\mathcal{X}).$$
>- $K\,f$ is a **function** on $\mathcal{X}$ defined as $$K\,f(x) := \int_{\mathcal{X}}\,f(y)\,K(x, dy), \quad \forall x\in \mathcal{X}.$$

- [[Markov Transition Kernel and Transition Function]]
- [[Integral Operator associated with Transition Kernel]]


>[!important] Definition
>Then the **invariant measure**  $\pi$ of **$\mu$-irreducible chain** is defined as the **invariant measure** of transition kernel $K$ 
>$$
>\begin{align*}
> \pi\,K &= \pi.
>\end{align*}
>$$ 
>That is, it is the **left-eigenvector** of transition kernel $K$ associated with **eigenvalue** $\lambda = 1.$ 

- [[Eigenvalue Point Residual Spectrum of Linear Operator]]

>[!important] Definition
>We can define **invariant (measurable) function** of transition $K$ as
>$$
>Kf = f.
>$$
>That is, it is the **right-eigenvector** of transition kernel $K$ associated with **eigenvalue** $\lambda = 1.$ 

- [[Eigenvalue Point Residual Spectrum of Linear Operator]]
- [[Integral Operator associated with Transition Kernel]]


## Recurrence

>[!important] Theorem
>If a Markov chain is **positive**, it is **recurrent**.

## Kac Theorem

- [[Kac Theorem on Markov Chain]]



-----------
##  Recommended Notes and References

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]


- [[Hilbert Space]]
- [[Complete Orthonormal Basis of Hilbert Space]]

- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Real Analysis by Royden]]

- [[Monte Carlo Statistical Methods by Robert]] pp 223
- [[Probability and Measure by Billingsley]]

