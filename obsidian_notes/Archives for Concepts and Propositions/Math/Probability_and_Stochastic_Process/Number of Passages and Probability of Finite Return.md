---
tags:
  - concept
  - math/stochastic_process
  - machine_learning_models/mc
keywords:
  - first_hitting_time
  - stopping_time
  - Markov_Chain
topics:
  - stochastic_process
name: Number of Passages in State of Markov Chain
date of note: 2024-05-24
---

## Concept Definition

>[!important]
>**Name**: Number of Passages in State of Markov Chain

>[!important] Definition
>Let $\{(X_{n}, \mathscr{F}_{n}), n\ge 0\}$ be a *Markov chain* of random variables on measurable space $(\Omega, \mathscr{F})$. 
>
>Consider $A \in \mathscr{F}$. We define **the number of passages** of $(X_{n})$ **at** $A$ as
>$$
>\eta_{A} := \sum_{n=1}^{\infty}\mathbb{1}\left(X_{n} \in A\right).
>$$

^830eef

- [[Markov Chain and Markov Process]]
- [[Stopping Time of Markov Chain]]


>[!important] Definition
>Of particular importance are related quantities:
>- the **average number of passages** in $A$: 
>$$
>\mathbb{E}\left[\eta_{A} \, |\, X_{0}= x\right]
>$$
>- the **probability of return to** $A$ in a **finite time of steps**:
>$$
>\mathcal{P}\left\{ \eta_{A} < + \infty  | X_{0}= x\right\} 
>$$ 

^3ca5c2



## Explanation





-----------
##  Recommended Notes and References

- [[Stopping Time of Markov Chain]]

- [[Markov Chain and Markov Process]]
- [[Filtration]]


- [[Probability and Measure by Billingsley]]
- [[Monte Carlo Statistical Methods by Robert]]
