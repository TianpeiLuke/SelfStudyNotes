---
tags:
  - entry_point
  - concept
  - statistics/concentration_inequality
keywords: 
topics:
  - concentration_inequality
name: Martingale Based Inequalities
date of note: 2024-05-11
---

## Concept Definition

- [[Martingale]]
- [[Martingale Differences]]

>[!important] Bernstein's Inequality for Martingale
>Let $\set{(D_n, \mathscr{F}_n), n \ge 1}$ be a **martingale difference sequence**, and suppose that 
>$$
>\begin{align*}
> \mathbb{E}\left[\exp \left(\lambda D_n \right) \Big| \mathscr{F}_{n-1}  \right]   \le \exp\left(\frac{\lambda^2 \nu_k^2}{2}  \right),
>\end{align*}
>$$  
>almost surely for any $|\lambda| < 1/\alpha_k$. 
>
>Then for $t > 0$,
>$$  
> \begin{align}
> \mathcal{P}\left\{\sum_{k=1}^{n}D_k \ge t \right\} &\le  \exp \left(- \frac{t^2}{2 \left(\sum_{k=1}^{n}\nu_k^2 + \alpha_{*}\,t \right)} \right). 
> \end{align}
>$$ 
>where $\alpha_{*} := \max_{1 \le k \le n} \alpha_k$

- [[Bernstein Inequality for Martingale]]

>[!important] Azuma-Hoeffding Inequality
>Let $\set{(D_i, \mathscr{F}_i), i \ge 1}$ be a **martingale difference sequence** for which there are constants $n$, and $\set{(a_i, b_i)}^{n}_{i=1}$ such that $D_i \in [a_i, b_i]$ *almost surely* for all $k = 1 \,{,}\ldots{,}\, n$. 
>
>Then, for all $t \ge 0$,
>$$
> \begin{align}
> \mathcal{P} \left\{\sum_{k=1}^{n}D_k  \ge t  \right\}  &\le \exp\left(- \frac{2 t^2}{ \sum_{k=1}^{n}(b_k - a_k)^2}\right) 
> \end{align}
>$$ 


- [[Azuma-Hoeffding Inequality]]

>[!important]  Bounded Difference Inequality (McDiarmid's Inequality)
>Suppose that $f$ satisfies **the bounded difference property** with parameters $(L_1 \,{,}\ldots{,}\, L_n)$, i.e. given vectors $x, x' \in \mathcal{X}^n$ and an index $k \in \set{1, 2 \,{,}\ldots{,}\, n}$, we define a new vector $x^{(-k)} \in \mathcal{X}^n$ via
>$$
> \begin{align*}
> x_j^{(-k)} &= \left\{\begin{array}{cc}
> x_j & j \neq k\\
> x_k'& j = k
> \end{array}
> \right.
> \end{align*}
>$$ 
> Then, each index $k = 1, 2 \,{,}\ldots{,}\, n$,
> $$
> \begin{align}
> \lvert f(x) - f(x^{(-k)}) \rvert \le L_k, \quad\text{ for all }x, x' \in \mathcal{X}^n.
> \end{align}
>$$  
>
>Suppose that the random vector $X = (X_1, X_2 \,{,}\ldots{,}\, X_n)$ has **independent components.** 
>
>Then
>$$
> \begin{align}
> \mathcal{P}\left\{ \lvert f(X) - \mathbb{E}\left[ f(X) \right] \rvert \ge t \right\}  &\le  2 \exp \left( - \frac{2 t^2}{ \sum_{k=1}^{n}L_k^2}\right).
> \end{align}
>$$ 

- [[Bounded Difference Inequality]]

>[!important] Doob's Maximal Inequality
>Suppose $\set{(X_n, \mathscr{F}_n), n \ge 0}$ is a **sub-martingale**. 
>
>Then for any $t >0$, 
>$$
> \begin{align}
> \mathcal{P}\left\{\max_{k \le n}X_k \ge t  \right\} \le \frac{1}{t}\mathbb{E}_{}\left[ X_n \mathbb{1}\left\{\max_{k \le n}X_k \ge t \right\} \right] 
> \end{align}
>$$ 
>
>If $X_{n} \ge 0$, almost surely for all $n$, then 
>$$
> \begin{align}
> \mathcal{P}\left\{\max_{k\le n}X_k \ge t  \right\} \le \frac{1}{t}\mathbb{E}_{}\left[ X_n \right]. 
> \end{align}
>$$ 

- [[Doob Maximal Inequality]]







-----------
##  Recommended Notes and References

- [[Concepts and Theorems for Martingale]]
- [[Basic Inequalities and Cramér–Chernoff Method]]

- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Probability An Introduction by Vershynin]]
