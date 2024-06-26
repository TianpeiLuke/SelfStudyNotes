---
tags:
  - concept
  - math/stochastic_process
keywords:
  - ergodicity
  - ergodic_theorem
  - harris_recurrent
  - Markov_Chain
topics:
  - stochastic_process
name: Ergodic Theorem for Harris Recurrent Markov Process
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Ergodic Theorem for Harris Recurrent Markov Process

### Discrete State Markov Chain


>[!important] Ergodic Theorem (Number of Passages)
>Let $(X_{n})$ be a Markov chain with *countable state* $\mathcal{X}$.
>
>Suppose that $(X_{n})$ is **irreducible** with transition kernel $K$.
>
>Then for any *initial distribution* $X_{0} \sim \mu$, the number of passages of $(X_{n})$ at state $x\in \mathcal{X}$ 
>$$
>\lim_{ n \to \infty } \frac{1}{n}\sum_{k=1}^{n}\mathbb{1}\{X_{k} = x\}  =  \frac{1}{\mathbb{E}\left[  \tau_{x} | X_{0} \sim  \mu \right]}, \text{ a.s.}
>$$

- [[Characteristic Function of Set]]
- [[Simple Integral of Simple Functions]]
- [[Stopping Time of Markov Chain]]
- [[Irreducibility of Markov Chain]]
- Norris, J. R. (1998). _Markov chains_ (No. 2). Cambridge university press. pp 53


>[!info]
>By [[Kac Theorem on Markov Chain]]. we see that if  *invariant measure $\pi$ exists* (i.e. the chain is **irreducible positive recurrent**)
>$$
>\lim_{ n \to \infty } \frac{1}{n}\sum_{k=1}^{n}\mathbb{1}\{X_{k} = x\}  =  \frac{1}{\mathbb{E}\left[  \tau_{x} | X_{0} \sim \mu \right]} = \pi(x), \text{ a.s.}
>$$

- [[Kac Theorem on Markov Chain]]

>[!important] Ergodic Theorem (Discrete State)
>Let $(X_{n})$ be a Markov chain with *countable state* $\mathcal{X}$.
>
>Suppose that $(X_{n})$ is **irreducible**, **positive recurrent** having **invariant measure** $\pi$ and transition kernel $K$.
>
>Then for any *bounded function* $f: \mathcal{X} \to \mathbb{R}$, 
>$$
>\lim_{ n \to \infty } \frac{1}{n}\sum_{k=1}^{n}f(X_{k})  = \sum_{x\in \mathcal{X}}\pi(x)\,f(x) := \mathbb{E}_{ \pi }\left[  f(X) \right], \text{ a.s.}
>$$

- [[Positive Recurrent Markov Chain]]
- [[Irreducibility of Markov Chain]]
- [[Invariant Measure and Stationary Distribution]]
- Norris, J. R. (1998). _Markov chains_ (No. 2). Cambridge university press. pp 53

### Harris Chain

>[!important] Ergodic Theorem (Harris Recurrent)
>Let $(X_{n})$ be a Markov chain with *possible uncountable state* $\mathcal{X}$.
>
>If $(X_{n})$ has a **$\sigma$-finite invariant measure** $\pi$, the following two statements are **equivalent**:
>- The Markov chain $(X_{n})$ is **Harris recurrent**.
>- If $f, g \in L^1(\mathcal{X}, \pi)$ with $$\int_{\mathcal{X}}g\,d\pi \neq 0$$ then $$\lim_{ n \to \infty } \frac{\frac{1}{n}\sum_{k=1}^{n}f(X_{k})}{\frac{1}{n}\sum_{k=1}^{n}g(X_{k})} = \frac{\int_{\mathcal{X}}f\,d\pi}{\int_{\mathcal{X}}g\,d\pi}, \text{ a.s.}$$

>[!info]
>Choose $g = 1$, we have
>$$
>\lim_{ n \to \infty } \frac{1}{n}\sum_{k=1}^{n}f(X_{k})  = \mathbb{E}_{ \pi }\left[  f(X) \right], \text{ a.s.}
>$$

- [[Finite and sigma-Finite Measure]]
- [[Ergodic Theorem]]

## Explanation

>[!important]
>The **Ergodic Theorem** is a **generalization** of the **Strong Law of Large Numbers (SLLN)** for Markov chains, where $(X_{1}, X_{2} \,{,}\ldots{,}\,)$ are *not independent* but has a *stationary distribution* that is independent from the initial state distribution.

- [[Kolmogorov Strong Law of Large Numbers]]

>[!important]
>The *Ergodic theorem* states that when reaching to **equilibrium**, 
>- a **Markov process** $(X_{n}, X_{n+1} \,{,}\ldots{,}\,)$ behaves *similarly* to an **empirical process** even if they are not independent.
>- A collection of Markov chain samples in **stationary status** behaves as they are **independent identically distributed** samples as the *previous status* does not affect the *distribution of the next status*.
>- The **convergence of samples** from Markov chain to its **mean** is guaranteed.
>- we can expect the concentration effect of Markov chain as  


>[!important]
>The concept of **ergodic Markov chain** requires additional condition for **aperiodic** but this condition is **unnecessary** for *erogdic theorem* to hold.  
>
>The ergodicity of *Markov chain* is **stronger** than the ergodicity of *shift transformation*. 

- [[Aperiodic Markov Chain]]
- [[Ergodic Markov Chain and Asymptotic of Transition Kernel]]
- [[Ergodic Transformation]]

## Measure Preserving Transformation

>[!important]
>We can prove the above theorem using the general [[Ergodic Theorem]] where the measure preserving transformation is **the Markov shift**
>$$
>T(z_{1}, z_{2} \,{,}\ldots{,}\,) = (z_{2} \,{,}\ldots{,}\,)
>$$ 
>Note that $T$ is **ergodic** if the Markov chain is **irreducible**.

- [[Measure Preserving Transformation in Markov Chain]]




-----------
##  Recommended Notes and References

- [[Harris Recurrent Set and Harris Recurrent Markov Chain]]
- [[Ergodic Markov Chain and Asymptotic of Transition Kernel]]

- [[Ergodic Theorem]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]


- [[Monte Carlo Statistical Methods by Robert]] pp 241
- Wikipedia [Ergodicity](https://en.wikipedia.org/wiki/Ergodicity)