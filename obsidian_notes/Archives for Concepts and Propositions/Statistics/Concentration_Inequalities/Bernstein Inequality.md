---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - bernstein_inequality
topics:
  - statistics
name: Bernstein Inequality
date of note: 2024-05-11
---

## Concept Definition

>[!important]
>**Name**: Bernstein's Inequality


>[!important] Bernstein's Condition
>Given a *random variable* $X$ with mean $\mu = \mathbb{E}\left[ X \right]$, we say that $X$ satisfies the **Bernstein's condition** *with parameter $\nu$, $c$*,  if the **variance** $\text{Var}(X) = \mathbb{E}\left[ X^2 \right] - \mu^2 \le \nu$, and
>$$
> \begin{align*}
> \mathbb{E}\left[ (X - \mu)_{+}^q \right] \le \frac{q!}{2} \nu c^{q-2}, \quad \text{ for all integers }q \ge 2,
> \end{align*}
>$$ 
>where $(x)_{+} = \max\set{x, 0}$. 

>[!important] Bernstein's Inequality (Simple Form)
>Let $X_{1} \,{,}\ldots{,}\, X_{n}$ be *independent* random variable. Assume that there exist *positive numbers* $\nu$ and $c$ such that
>$$
> \begin{align*}
> \mathbb{E}\left[ \left(X\right)_{+}^q \right] \le \frac{q!}{2}\nu c^{q-2}, \quad \forall q\in \mathbb{N},\; q\ge 2,
> \end{align*}
>$$ 
>where $(x)_{+}= \max(x, 0)$ be the positive part of $x$.
>
>Let $S = \sum_{i=1}^n (X_{i} - \mathbb{E}\left[ X_{i} \right])$, then,  for any $t > 0$,
>$$
> \begin{align}
> \mathcal{P} \{ S \ge t \} \le \exp \left(- \frac{t^2}{2(\nu + c\,t)} \right).
> \end{align}
>$$ 


## Explanation

>[!info]
>There are several main conditions on the Bennet's inequality
>- $X$ has **variance** and its **variance is bounded above** *by some constant* $\nu$.
>- $X$ has **moments of all orders** 
>- $X$ satisfies **the Bernstein condition** above, which provides *upper bounds* for *the growth rate* of **the high-order moments** with respect to the order.


## Bernstein Inequality for Bounded Random Variable

>[!info]
>Compared to both [[Hoeffding Inequality]] and [[Bennett Inequality]], the Bernstein's inequality has *dropped* **the boundedness condition** on the random variable.
>
>On the other hand, it has additional upper bounds on the growth rate of the moments

>[!important]
>For bounded random variables $X_i \le b$ almost surely for all $i \le n$, then *the Bernstein conditions* hold with
>$$
> \begin{align*}
> \nu = \sum_{i=1}^{n}\mathbb{E}\left[ X_i^2 \right], \quad c = b/3.
> \end{align*}
>$$ 

>[!important] Bernstein's Inequality for Bounded Random Variable
>Let $X_1 \,{,}\ldots{,}\, X_n$ be **independent**, *centered* random variables, such that $|X_i| \le b$ all $i$, almost surely. Then, for every $t \ge 0$, we have
>$$
> \begin{align}
> \mathcal{P}\left\{ \left\lvert \frac{1}{n}\sum_{i=1}^{n}X_i \right\rvert  \ge t \right\} \le 2\exp \left(- \frac{t^2}{2(\nu + bt/3)}\right). 
> \end{align}
>$$ 
>Here $\nu = \sum_{i=1}^{n}\mathbb{E}\left[ X_i^2 \right]$ is the variance of the sum.

- [[Chernoff Bound for Poisson distribution]]
- [[Chernoff Bound for Bernoulli distribution]]

>[!info]
>Bennet's inequality is **sharper** than Bernstein's inequality. 

- [[Bennett Inequality]]

## Characteristic of the Bound

>[!info]
>- Fort $t \gg \nu / c$, it **loses a logarithmic factor** in the *exponent* with respect to Bennett’s inequality. 
>
>- On the other hand, if $\nu$ is the **dominant term** in the *denominator of the exponent*, Bennett’s and Bernstein’s inequalities are **almost equivalent** and both provide a **sub-Gaussian type inequality**.

>[!important]
>The tail provided by the Bernstein's inequality has a smooth transition from the **sub-Gaussian tail** (*Gaussian like*, *super-exponential decay*) to **sub-Gamma tail** (*Poisson-like*, *exponential decay*). 
>
>- If the **deviation** $t$ is **small**, so that $\nu$ dominant towards $ct$ term in the denominator, then the bound is a Gaussian tail with $$\exp \left( - K t^2 \right)$$ 
>- If the **deviation** $t$ is **large** enough, so that $c t$ dominant towards $\nu$ term in the denominator, then the bound is a Poisson tail with $$\exp \left( - K_{c} t \right)$$ 
>  
>That is, 
>- In the **small deviation regime**, the tail is *sub-Gaussian like*, which decays fast;
>- In the **large deviations regime**, the tail is *sub-Gamma type*, which decays slowly.  

![[bernstein_inequality_bound.png]]



## General Form

>[!important] Bernstein's Inequality
>Let $X_{1} \,{,}\ldots{,}\, X_{n}$ be *independent* random variable. Assume that there exist positive numbers $\nu$ and $c$ such that
>$$
> \begin{align*}
> \mathbb{E}\left[ \left(X\right)_{+}^q \right] \le \frac{q!}{2}\nu c^{q-2}, \quad \forall q\in \mathbb{N},\; q\ge 3,
> \end{align*}
>$$ 
>where $(x)_{+}= \max(x, 0)$ be the positive part of $x$.
>
>Let $S = \sum_{i=1}^n (X_{i} - \mathbb{E}\left[ X_{i} \right])$, then, for all $\lambda \in (0, 1/c)$ and $t >0$,
>$$
> \begin{align*}
> \psi_{S}(\lambda) := \log \mathbb{E}\left[ e^{\lambda S} \right] \le \frac{\nu \lambda^2}{2(1 - c\lambda)}
> \end{align*}
>$$ 
>and the rate function
>$$
> \begin{align*}
> \psi_{S}^{*}(t)  \ge \frac{\nu}{c^2}h_{1}\left(\frac{ct}{\nu}\right),
> \end{align*}
>$$  
>where $h_{1}(x) := 1 + x - \sqrt{ 1 + 2x }$ for $x >0$.
> 
>In particular, for any $t > 0$,
>$$
> \begin{align}
> \mathcal{P} \{ S \ge c\,t + \sqrt{ 2 \nu t} \} \le \exp \left(-t\right).
> \end{align}
>$$ 




## Proof




## Generalization

- Bernstein inequality holds when $\{ (S_{n}, \mathscr{F}_{n}), n \ge 0 \}$ forms a **martingale** without assuming all random variables are independent from each other. 
- [[Bernstein Inequality for Martingale]]






-----------
##  Recommended Notes and References

- [[Cramér–Chernoff Method]]
- [[Chernoff Bound for Bernoulli distribution]]
- [[Independent Random Variables]]

- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Probability An Introduction by Vershynin]]