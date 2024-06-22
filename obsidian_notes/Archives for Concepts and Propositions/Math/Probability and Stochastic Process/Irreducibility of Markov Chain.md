---
tags:
  - concept
  - math/stochastic_process
keywords:
  - irreducibility_markov_chain
topics:
  - stochastic_process
name: Irreducibility of Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Irreducibility of Markov Chain

>[!important] Definition
>Let $(X_{n})$ be a *discrete-time Markov chain* on $\mathcal{X}$. Denote $\mathcal{B}[\mathcal{X}]$ as the *Borel $\sigma$-algebra.*
>
>Given a *Borel measure* $\mu$, the Markov chain $(X_{n})$ with *transition kernel* $K$ is **$\mu$-irreducible** if, for *every* $A \in \mathcal{B}[\mathcal{X}]$, with $\mu(A) > 0$, there *exists* $n$ such that $$K^n(x, A) > 0$$ for all $x\in \mathcal{X}.$
>
>Equivalently, $$\mathcal{P}\left(\tau_{A} < \infty\,|\,X_{0} = x\right) > 0.$$

- [[Chapman-Kolmogorov Equation]]
- [[Markov Transition Kernel and Transition Function]]
- [[Stopping Time of Markov Chain]]
- [[Markov Chain and Markov Process]]
- [[Borel sigma Field]]

>[!important] Definition
>Let $(X_{n})$ be a *discrete-time Markov chain* on $\mathcal{X}$. Denote $\mathcal{B}[\mathcal{X}]$ as the *Borel $\sigma$-algebra.
>
>$(X_{n})$ is called **strongly $\mu$-irreducible** if $n = 1$, i.e. $$K(x, A) > 0$$  for all $x\in \mathcal{X}$ and every $A \in \mathcal{B}[\mathcal{X}]$ with $\mu(A) > 0$.


## Explanation

>[!important] Definition
>A Markov Chain is **irreducible** if it has *only one equivalence class*, i.e. *all* states in $\mathcal{X}$ *communicate to each other*.









-----------
##  Recommended Notes and References

- [[Stopping Time of Markov Chain]]
- [[Number of Passages and Probability of Finite Return]]


- [[Chapman-Kolmogorov Equation]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- [[Borel sigma Field]]

- [[Monte Carlo Statistical Methods by Robert]] pp 213