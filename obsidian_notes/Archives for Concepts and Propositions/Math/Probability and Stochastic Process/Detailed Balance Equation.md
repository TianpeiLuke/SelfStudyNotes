---
tags:
  - concept
  - math/stochastic_process
keywords:
  - detailed_balance_equation 
  - Markov_Chain
topics:
  - stochastic_process
name: Detailed Balance Equation for Invariant Measure
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Detailed Balance Equation for Invariant Measure

>[!important] Definition
>A $\mathcal{X}$-valued Markov chain with *transition kernel* $K$ satisfies the **detailed balance equation** if there exists a function $f$ satisfying 
>$$
> K(y, x)f(y) = K(x, y)f(x)
>$$ 
>for every $x, y \in \mathcal{X}$.

- [[Markov Transition Kernel and Transition Function]]


## Explanation

>[!important]
>The balance condition express an **equilibrium** in the **flow** of *the Markov chain*, namely that the *probability* of **being in $x$** and **moving to** $y$ is the **same** as the *probability* of **being in $y$** and **moving back** to $x$. 
>
>When $f$ is a **density**, it also implies that the chain is **reversible**.


## Reversible Chain

>[!important] Theorem
>Suppose that a *Markov chain* with *transition function* $K$ satisfies the **detailed balance condition** with $\pi$ a **probability density function**. 
>
>Then: 
>- The *density* $\pi$ is the **invariant density** of the *chain*. 
>- The chain is **reversible**.

- [[Time-Reversible Markov Chain]]
- [[Invariant Measure and Stationary Distribution]]



-----------
##  Recommended Notes and References


- [[Invariant Measure and Stationary Distribution]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Probability and Measure by Billingsley]]
- [[Monte Carlo Statistical Methods by Robert]]
- Wikipedia [Detailed_balance](https://en.wikipedia.org/wiki/Detailed_balance)