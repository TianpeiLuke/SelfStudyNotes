---
tags:
  - concept
  - math/probability
  - math/stochastic_process
keywords:
  - optional_stopping
  - optional_sampling_theorem
topics:
  - stochastic_process
  - probability
name: Weak Optional Sampling Theorem
date of note: 2024-05-15
---

## Theorem

>[!important]
>**Name**: Weak Optional Sampling Theorem

>[!important] Weak Optional Sampling Theorem
>Let $\set{(X_n, \mathscr{F}_n), n \ge 0}$ be a **martingale** where 
>$$
>\mathscr{F}_n = \sigma \left(X_{1} \,{,}\ldots{,} \,X_{n}\right)
>$$ 
>and let $T$ be **stopping time** with respect to $\set{\mathscr{F}_n, n \ge 0}$. 
>
>Suppose that **at least one** of the following conditions hold:
>
>- $T \le n_0,\; \text{a.s.}$ for some constant $n_0 >0$;
>- $T < \infty,\; \text{a.s.}$ and $|X_i| \le K$ where $i \le T$.
>
> Then 
>$$ 
> \begin{align*}
> \mathbb{E}\left[ X_{T} \right] &= \mathbb{E}\left[ X_{0} \right].
> \end{align*}
>$$  

- [[Martingale]]
- [[Stopping Time of Filtration]]

>[!important] Weak Optional Sampling Theorem (version 2)
>Let $\set{(X_n, \mathscr{F}_n), n \ge 0}$ be a **martingale** where 
>$$
>\mathscr{F}_n = \sigma \left(X_{1} \,{,}\ldots{,} \,X_{n}\right)
>$$ 
>and let $T$ be **stopping time** with respect to $\set{\mathscr{F}_n, n \ge 0}$. 
>
>Suppose $$\mathbb{E}\left[T \right] < \infty,$$ and there exists $n \ge 0$ and some constant $c$ such that 
>$$
> \begin{align*}
> \mathbb{E}\left[\lvert X_{n+1} - X_n \rvert \;|\; \mathscr{F}_n \right] \le c, \quad \text{a.s.} \; \text{ on }\set{T \ge n}.
> \end{align*}
>$$ 
> 
> Then $$\mathbb{E}\left[ |X_{T}|  \right] < \infty$$ and
>$$ 
> \begin{align*}
> \mathbb{E}\left[ X_{T} \right] &= \mathbb{E}\left[ X_{0} \right].
> \end{align*}
>$$  


## Explanation






-----------
##  Recommended Notes and References

- [[Bandit Algorithms by Lattimore]]
- [[Probability and Measure by Billingsley]]
- [[A Probability Path by Resnick]]