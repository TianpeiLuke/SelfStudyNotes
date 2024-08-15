---
tags:
  - concept
  - math/probability
  - math/stochastic_process
keywords:
  - optional_stopping
  - optional_sampling_theorem
  - optional_sampling
topics:
  - stochastic_process
  - probability
name: Doob's Optional Sampling Theorem
date of note: 2024-05-15
---

## Theorem

>[!important]
>**Name**: Doob's Optional Sampling Theorem

>[!important] Doob's Optional Sampling Theorem
>Let $\set{(X_n, \mathscr{F}_n), n \ge 0}$ be a **martingale** and let $S, T$ be $\set{\mathscr{F}_n, n \ge 0}$-**stopping time** *bounded* by constant $c$, with 
>$$
>S \le T \le c, \;\text{a.s.},
>$$ 
>then the following functional equation holds
>$$
> \begin{align}
> \mathbb{E}\left[ X_T | \mathscr{F}_{S} \right] = X_S, \quad \text{a.s.} 
> \end{align}
>$$  
>where
>$$ 
> \begin{align*}
> \mathscr{F}_{S} := \set{A \in \mathscr{F}: A\cap \set{S \le n} \in \mathscr{F}_{n}, \quad n=0,1,\ldots }
> \end{align*}
>$$ 

- [[Martingale]]
- [[Stopping Time of Filtration]]

>[!important] 
>- If $\set{(X_n, \mathscr{F}_n), n \ge 0}$ be a **sub-martingale**, then the above equation becomes inequality
>$$
>  \mathbb{E}\left[ X_T | \mathscr{F}_{S} \right] \le X_S, \quad \text{a.s.} 
>$$
>- If $\set{(X_n, \mathscr{F}_n), n \ge 0}$ be a **super-martingale**, 
>$$
>  \mathbb{E}\left[ X_T | \mathscr{F}_{S} \right] \ge X_S, \quad \text{a.s.} 
>$$  

- [[Sub-Martingale]]
- [[Super-Martingale]]

## Explanation

>[!info]
>The above Doob's Optional Sampling Theorem implies [[Weak Optional Sampling Theorem]]. 
>
>See that 
>$$
>\mathbb{E}\left[ X_{T} \right] =  \mathbb{E}\left[ \mathbb{E}\left[ X_T | \mathscr{F}_{S} \right]   \right] = \mathbb{E}\left[ X_{S} \right]
>$$



-----------
##  Recommended Notes and References




- [[Probability and Measure by Billingsley]]
- [[A Probability Path by Resnick]]