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

### Discrete State Markov Chain

>[!important] Definition
>Let $(X_{n})$ be a *Markov chain* with *discrete state* $\mathcal{X}$.
>
>A $\mathcal{X}$-valued Markov chain with *transition kernel* $K$ satisfies the **detailed balance equation** if there exists a function $f$ satisfying 
>$$
> K(y, x)f(y) = K(x, y)f(x)
>$$ 
>for every $x, y \in \mathcal{X}$.


- [[Markov Transition Kernel and Transition Function]]

### Harris Chain


>[!important] Definition (Uncountable State)
>Let $(X_{n})$ be a *Harris chain* with *uncountable state* $\mathcal{X}$.
>
>$(X_{n})$ satisfies the **detailed balance equation** if there exists a *positive measure* $\nu$ satisfying
>$$
> \begin{align}
> \nu(dx)\,K(x, dy) &=  \nu(dy)\,\,K(y, dx).
> \end{align}
>$$  

- [[Invariant Measure and Stationary Distribution]]



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

## Global Balance Equation

- [[Global Balance Equation for Invariant Measure]]



-----------
##  Recommended Notes and References

- [[Global Balance Equation for Invariant Measure]]

- [[Invariant Measure and Stationary Distribution]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Probability and Measure by Billingsley]]
- [[Monte Carlo Statistical Methods by Robert]]
- Wikipedia [Balance_equation](https://en.wikipedia.org/wiki/Balance_equation)