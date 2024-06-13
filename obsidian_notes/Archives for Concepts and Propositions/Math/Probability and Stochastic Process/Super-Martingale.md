---
tags:
  - concept
  - math/probability
  - math/stochastic_process
keywords:
  - super-martingale
topics:
  - probability
  - stochastic_process
name: Super-Martingale
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**:  Super-martingale



>[!important] Definition
>Let $\{X_n, n \ge 0\}$ be a stochastic process on a measure space $(\Omega, \mathscr{F})$, and $\{\mathscr{F}_n, n \ge 0\}$ be a **filtration**.
>
>$\{ (X_n, \mathscr{F}_n),  n \ge 0\}$ is a **super-martingale** *(supermg)* if
> 
> -  $X_n$ is **adapted** in the sense that for each $n$, *$X_n \in \mathscr{F}_n$*;  that is, $X_n$ is **$\mathscr{F}_n$-measurable.**
> -  For $n \ge 0$, $X_n \in L^1(\Omega, \mathscr{F}_{n})$; that is, $X_{n}$ is **absolutely integrable.** 
>   $$\mathbb{E}\left[ \lvert X_{n} \rvert  \right] < \infty, \text{ for } n \ge 0.$$
> - For $0 \le m < n$, the following **inequality** holds
> $$
> \begin{align}
> \mathbb{E}\left[ X_{n} \;|\; \mathscr{F}_{m} \right] &\le X_m, \quad \text{a.s.} 
> \end{align}
> $$

- [[Martingale]]
- [[Filtration]]
- [[Adapted Stochastic Process and Non-anticipating Process]]
- Check on the definition of [[Conditional Expectation]]


>[!info]
>The above condition is equivalent to
>$$
>\int_{A} X_{n}d\mathcal{P} \le \int_{A} X_{m} d\mathcal{P}, \quad A \in \mathscr{F}_{m}
>$$


## Explanation

>[!important]
>This condition states that the *current observation* provides support **from above the future** *conditional expectation*, and the process tends to **decrease in future time**.


>[!info]
>A super-martingale represents an **unfair game**, when $X_{n}$ is the loss at time $n$, and the players *guarantee to  __win__* in the long run.
 





-----------
##  Recommended Notes and References

- [[Stochastic Process]]

- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]