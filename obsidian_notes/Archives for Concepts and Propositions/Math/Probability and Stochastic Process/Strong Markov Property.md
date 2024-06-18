---
tags:
  - concept
  - math/stochastic_process
  - machine_learning_models/mc
keywords:
  - Markov_Chain
  - strong_markov_property
topics:
  - stochastic_process
name: Strong Markov Property
date of note: 2024-05-24
---

## Concept Definition

>[!important]
>**Name**: Strong Markov Property

>[!important] Definition
>Let $\{(X_{n}, \mathscr{F}_{n}), n\ge 0\}$ be a *Markov chain* of random variables on measurable space $(\Omega, \mathscr{F})$. 
>
>$(X_{n})$ satisfies the **strong Markov property** if for every initial distribution $\mathcal{P}_{0}$ and every **stopping time** $\zeta$ which is *almost surely finite,*
>$$
>\mathbb{E}_{0}\left[h\left(X_{\zeta+1}, X_{\zeta+2}, \ldots \right) | x_{1} \,{,}\ldots{,}\,x_{\zeta} \right] = \mathbb{E}_{x_{\zeta}}\left[h\left(X_{1}, X_{2}, \ldots \right) \right]
>$$ 

- [[Markov Chain and Markov Process]]
- [[Stopping Time of Markov Chain]]

>[!important] Definition
>A *Markov process* $\left\{\Omega, \mathscr{F}, \mathscr{F}_{t}^s, X_{t}, \mathcal{P}_{x,s}  \right\}$ with transition probability $p$ is said to have **the strong Markov property** if for every $X\in \mathcal{X}$ and for every real-valued *stopping time* $\zeta$,
>$$
>\mathcal{P}_{x,s}\left( X(t+ \zeta) \in A \,|\, \mathscr{F}_{\zeta}^{s} \right) = p(A,\, t+\zeta,\, X(\zeta),\, \zeta) \quad \text{a.s.}
>$$

- Friedman, A. (1975). *Stochastic differential equations and applications*. pp 25.
- [[Markov Transition Kernel and Transition Function]]

## Explanation


>[!important]
>Compare to the **(weak) Markov property**, the strong Markov property also conditioning on **stopping time** $(\zeta = n)$;

- [[Markov Chain and Markov Process]]
- [[Stopping Time of Markov Chain]]







-----------
##  Recommended Notes and References

- [[Stopping Time of Markov Chain]]

- [[Markov Chain and Markov Process]]
- [[Filtration]]


- [[Probability and Measure by Billingsley]]
- [[Monte Carlo Statistical Methods by Robert]]
