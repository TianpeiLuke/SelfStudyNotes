---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - bennett_inequality
topics:
  - statistics
name: Bennett Inequality
date of note: 2024-05-11
---

## Concept Definition

>[!important]
>**Name**: Bennett's Inequality


>[!important] Bennett's Inequality
>Let $X \in L^2(\Omega, \mathscr{F}, \mathcal{P})$ be a random variable with **finite variance** such that $X \le b$ for some $b > 0$ *almost surely*. 
>
>Let $Z = X - \mathbb{E}\left[ X \right]$ be the *centered* random variable and $\nu = \mathbb{E}\left[ X^2 \right]$ be the *second moment*. 
>
>If we write $$\phi(u) = e^u - u - 1$$ for $u \in \mathbb{R}$, then, for all $\lambda > 0$,
>$$
> \begin{align*}
> \log \mathbb{E}\left[ e^{\lambda Z} \right] \le \log\left(1 + \frac{\nu}{b^2}\phi(b \lambda)\right) \le \frac{\nu}{b^2}\,\phi(b\lambda),
> \end{align*}
>$$ 
>and for any $t > 0$,
>$$
> \begin{align}
> \mathcal{P} \{ Z \ge t \} \le \exp \left(-\frac{\nu}{b^2}h\left(\frac{b\,t}{\nu}\right)\right)
> \end{align}
>$$ 
>where $h(u) = (1 + u) \log(1 + u) - u$ for $u > 0$.

- [[Basic Inequalities and Cramér–Chernoff Method]]

## Explanation

>[!info]
>For
>$$
> \begin{align*}
> h(u) &= (1+ u)\log(1 + u) - u, \quad u \ge -1,
> \end{align*}
> $$  
> the **convex conjugate function** of $h(u)$ is
>$$
> \begin{align*}
> h^{*}(x) &= \sup_{u \ge -1}\set{x u - h(u)} \\
> &=  \sup_{u \ge -1}\set{x u - (1+ u)\log(1 + u) + u} \\
> &= e^x - x - 1\\
> &= \phi(x)
> \end{align*}
>$$  
>where $1+ u^{*}= e^{x}$.  

>[!info]
>There are two main conditions on the Bennet's inequality
>- $X \in L^2(\Omega, \mathscr{F}, \mathcal{P})$ has **finite variance (or, second moment)**
>- $X \le b, \text{a.s.}$, i.e. $X$ is **bounded above almost surely**.

> [!info]
>This condition is stronger than Markov inequality, but is *weaker* than *Chernoff's inequality.* 

- [[Markov Inequality]]

> [!info]
>Compared to Hoedffding's inequality condition, $X$ only need **one-side bounded.**  

- [[Hoeffding Inequality]]


>[!info]
>Bennet's inequality provides a *Poisson-like* upper tail. See [[Chernoff Bound for Poisson distribution]]

>[!info]
>Bennet's inequality is **sharper** than Bernstein's inequality. 

- [[Bernstein Inequality]]


## Sum of Independent Samples

>[!important] Bennett's Inequality
>Let $X_{1} \,{,}\ldots{,}\, X_{n}$ be *independent* random variable with **finite variance** such that $X_{i} \le b$ for some $b > 0$ *almost surely* for all $i\le n$. 
>
>Let $S = \sum_{i=1}^n (X_{i} - \mathbb{E}\left[ X_{i} \right])$ be the sum of *centered* random variables and $\nu = \sum_{i=1}^n \mathbb{E}\left[ X_{i}^2 \right]$ be proportional to the *sample estimate of the second moment*. 
>
>If we write $$\phi(u) = e^u - u - 1$$ for $u \in \mathbb{R}$, then, for all $\lambda > 0$,
>$$
> \begin{align*}
> \log \mathbb{E}\left[ e^{\lambda S} \right] \le n \log\left(1 + \frac{\nu}{n b^2}\phi(b \lambda)\right) \le \frac{\nu}{b^2}\,\phi(b\lambda),
> \end{align*}
>$$ 
>and for any $t > 0$,
>$$
> \begin{align}
> \mathcal{P} \{ S \ge t \} \le \exp \left(-\frac{\nu}{b^2}h\left(\frac{b\,t}{\nu}\right)\right)
> \end{align}
>$$ 
>where $h(u) = (1 + u) \log(1 + u) - u$ for $u > 0$.


## Proof




## Generalization








-----------
##  Recommended Notes and References

- [[Cramér–Chernoff Method]]

- [[Martingale]]
- [[Martingale Differences]]

- [[Chernoff Bound for Bernoulli distribution]]
- [[Independent Random Variables]]

- [[Concentration Inequalities by Boucheron]]