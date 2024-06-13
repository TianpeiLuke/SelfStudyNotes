---
tags:
  - concept
  - math/probability
  - math/stochastic_process
  - statistics/concentration_inequality
keywords:
  - martingale_difference
topics:
  - probability
  - stochastic_process
name: Martingale Differences
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**:  Martingale Differences, *Sub-*Martingale Differences, *Super*-Martingale Differences


>[!important] Definition
>A sequence of random variables $\set{(d_n, \mathscr{F}_n), n \ge 0}$ is a **martingale difference sequence** or a **fair sequence** if
> 
> - $\{ \mathscr{F}_{n}: n \ge 0 \}$ is a **filtration**, i.e. for $n \ge 0$,  $\mathscr{F}_n \subseteq \mathscr{F}_{n+1}$.
> - For $n \ge 0$,  $$d_n \in L_1, \quad d_n \in \mathscr{F}_n;$$ that is, $d_n$ is **absolutely integrable** and **$\mathscr{F}_n$-measurable**.
> - For $j \ge 0$,
>$$ 
> \begin{align*}
> \mathbb{E}\left[ d_{n+1} | \mathscr{F}_n \right]  &= 0
> \end{align*}
>$$ 

- [[Martingale]]

>[!important] Definition
>A sequence of random variables $\set{(d_n, \mathscr{F}_n), n \ge 0}$ is a **sub-martingale difference sequence** or a **sub-fair sequence** if
> 
> - $\{ \mathscr{F}_{n}: n \ge 0 \}$ is a **filtration**, i.e. for $n \ge 0$,  $\mathscr{F}_n \subseteq \mathscr{F}_{n+1}$.
> - For $n \ge 0$,  $$d_n \in L_1, \quad   d_n \in \mathscr{F}_n;$$ that is, $d_n$ is **absolutely integrable** and **$\mathscr{F}_n$-measurable**.
> - For $j \ge 0$,
>$$ 
> \begin{align*}
> \mathbb{E}\left[ d_{n+1} | \mathscr{F}_n \right]  &\le 0
> \end{align*}
>$$ 

- [[Sub-Martingale]]

>[!important] Definition
>A sequence of random variables $\set{(d_n, \mathscr{F}_n), n \ge 0}$ is a **super-martingale difference sequence** or a **super-fair sequence** if
> 
> - $\{ \mathscr{F}_{n}: n \ge 0 \}$ is a **filtration**, i.e. for $n \ge 0$,  $\mathscr{F}_n \subseteq \mathscr{F}_{n+1}$.
> - For $n \ge 0$,  $$d_n \in L_1, \quad   d_n \in \mathscr{F}_n;$$ that is, $d_n$ is **absolutely integrable** and **$\mathscr{F}_n$-measurable**.
> - For $j \ge 0$,
>$$ 
> \begin{align*}
> \mathbb{E}\left[ d_{n+1} | \mathscr{F}_n \right]  &\ge 0
> \end{align*}
>$$ 


- [[Super-Martingale]]
- Check on the definition of [[Conditional Expectation]]

## Properties

>[!important]
>The *(sub, super) martingale difference* provide an **equivalent definitions** for *(sub, super) martingale*; and vice versa.

>[!info]
>The following theorem provides a way to construct (sub, super) martingale from (sub, super) martingale differences.
>
>Then opposite way can also be achieved.

>[!important] Proposition
>If $\set{(d_k, \mathscr{F}_k), k \ge 0}$ is **(sub, super) martingale difference sequence**, and
>$$
> \begin{align*}
> X_n = \sum_{k=0}^{n} d_k, 
> \end{align*}
>$$  
> then $\set{(X_n, \mathscr{F}_n), n \ge 0}$ is a **(sub, super) martingale**.

>[!important] Proposition
>Suppose $\set{(X_n, \mathscr{F}_n), n \ge 0}$ is a **(sub, super) martingale**. Define
>$$
> \begin{align*}
> d_0&:= X_0 - \mathbb{E}\left[ X_{0} \right]\\
> d_j &:= X_j - X_{j-1}, \quad j\ge 1.
> \end{align*}
>$$ 
>Then $\set{(d_j, \mathscr{F}_j), j \ge 0}$ is a **(sub, super) martingale difference** sequence.

>[!important]
>The most important property of martingale difference is that they are **orthogonal** to each other

>[!important] Theorem
>If $\set{(X_n, \mathscr{F}_n), n \ge 0}$ is a **martingale** where $X_n$ can be decomposed as
>$$
> \begin{align*}
> X_n = \sum_{j=0}^{n} d_j, 
> \end{align*}
>$$   
>$d_j$ is $\mathscr{F}_j$-measurable and  $\mathbb{E}[d_j^2] < \infty$ for $j \ge 0$, then $\set{d_j: j \ge 0}$ are **orthogonal**:
>$$
> \begin{align*}
>  \mathbb{E}\left[ d_i\,d_j \right] = 0 \quad i \neq j.
> \end{align*}
>$$ 





-----------
##  Recommended Notes and References

- [[Stochastic Process]]

- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]