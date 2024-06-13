---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - bernstein_inequality
topics:
  - statistics
name: Bernstein Inequality for Martingale
date of note: 2024-05-11
---

## Concept Definition

>[!important]
>**Name**: Bernstein's Inequality for Martingale


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
>where $\alpha_{*} := \max_{1 \le k \le n} \alpha_k.$

- [[Martingale]]
- [[Martingale Differences]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]


## Explanation

>[!info]
>Compare with the Bernstein condition in [[Bernstein Inequality]], we see that this condition is assuming that each term $D_{n}$ *given all past history* $\mathscr{F}_{n-1}$  is **sub-Gaussian**. 


>[!info]
>Just like the independent random variable setting, the Bernstein's inequality in Martingale setting also have **two regimes**:
>$$
>\mathcal{P}\left\{\sum_{k=1}^{n}D_k \ge t \right\} \le \left\{ \begin{array}{cc}
>  \exp\left(- \frac{t^2}{2 \sum_{k=1}^{n}\nu_k^2}\right)& \text{ if } 0 \le t \le \sum_{k=1}^{n}\nu_k^2 / \alpha_{*} \\[15pt]
>  \exp \left(- \frac{t}{\alpha_{*}} \right)  &\text{ if } t > \sum_{k=1}^{n}\nu_k^2 / \alpha_{*}.
> \end{array}\right. 
>$$


## Sub-Exponential Tail

>[!important]
>The sum $\sum_{k=1}^{n}D_k$ is **sub-exponential** with **parameters** $$\left(\sqrt{\sum_{k=1}^{n}\nu_k^2}\;  , \;\alpha_{*}\right),$$  where $\alpha_{*} := \max_{1 \le k \le n} \alpha_k$. 
>  
>  That is, for any $|\lambda| < 1/\alpha_{*}$, 
>$$ 
> \begin{align*}
> \mathbb{E}\left[ \exp\left\{\lambda \left(\sum_{k=1}^{n}D_k\right) \right\}  \right]   \le \exp\left(\frac{\lambda^2\sum_{k=1}^{n}\nu_k^2}{2}\right)
> \end{align*}
>$$ 


## Proof

>[!info]
>We follow the standard approach of controlling the moment generating function of $\sum_{k=1}^{n}D_k,$ and then applying **the Chernoff bound**. [[Cramér–Chernoff Method]]
>
>For any scalar $\lambda$ such that $|\lambda| < 1/\alpha_{*}$, conditioning on $\mathscr{F}_{n-1}$ , by definition of conditional expectation
>$$
>\begin{align*}
>\mathbb{E}\left[ \exp\left\{\lambda \left(\sum_{k=1}^{n}D_k\right) \right\}  \right]&= \mathbb{E}\left[ \mathbb{E}\left[ \exp\left\{\lambda \left(\sum_{k=1}^{n}D_k\right) \right\} \Big| \mathscr{F}_{n-1}  \right]  \right]  \\
>&= \mathbb{E}\left[ \exp\left\{\lambda \left(\sum_{k=1}^{n-1}D_k \right)\right\} \mathbb{E}\left[ \exp\left\{\lambda D_n \right\}  \;\Big|\; \mathscr{F}_{n-1} \right]  \right]
\end{align*}
>$$
>Then we apply the Bernstein condition and then the RHS results in the same form with $n-1$ terms. Thus, we can use induction, and recursively increase the upper bound
>$$
>\begin{align*}
>\mathbb{E}\left[ \exp\left\{\lambda \left(\sum_{k=1}^{n}D_k\right) \right\}  \right] &\le  \mathbb{E}\left[ \exp\left\{\lambda \left(\sum_{k=1}^{n-1}D_k \right)\right\}   \right] \exp\left(\frac{\lambda^2 \nu_n^2}{2}  \right)\\
>&\le \mathbb{E}\left[ \exp\left\{\lambda \left(\sum_{k=1}^{n-2}D_k \right)\right\}   \right] \exp\left(\frac{\lambda^2 (\sum_{k=n-1}^n \nu_k^2)}{2} \right)\\
>&\le \dots \\
>&\le \exp\left(\frac{\lambda^2\sum_{k=1}^{n}\nu_k^2}{2}\right).
\end{align*}
>$$
>Note that each time, in order to apply the Bernstein condition, we need $|\lambda| < 1/\alpha_k$. In the final form, 
>$$
>(|\lambda| < 1/\alpha_1) \,{\land}\ldots{\land}\,(|\lambda| < 1/\alpha_n) \implies |\lambda| < 1 / (\max_{1\le i \le n} \alpha_{i}) := 1 / \alpha^{*}.
>$$
>This proves the sub-exponential bound. 
>
>The Tail bound for Bernstein inequality follow from the property of sub-exponential distribution. Q.E.D.











-----------
##  Recommended Notes and References

- [[Cramér–Chernoff Method]]
- [[Chernoff Bound for Bernoulli distribution]]
  

  
