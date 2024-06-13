---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - hoeffding_inequality
topics:
  - statistics
name: Hoeffding Inequality
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**: Hoeffding's Inequality

>[!important] Hoeffding's Lemma
>Let $X$ be a random variable with $\mathbb{E}_{}\left[ X \right] = 0$, taking values in a **bounded interval** $[a, b]$ and let $\psi_{X}(\lambda) := \log \mathbb{E}_{}\left[ e^{\lambda X} \right]$. Then
>$$
> \begin{align*}
> \psi_{X}''(\lambda) \le \frac{(b - a)^2}{4}
> \end{align*}
> $$
> and **$X \in \mathcal{G}((b - a)^2/4)$.**

- [[Sub-Gaussian Random Variable]]


>[!important] Hoeffding's Inequality
>Let $X_1 \,{,}\ldots{,}\, X_n$ be **independent** random variables such that $X_i$ **takes its values in $[a_i, b_i]$** *almost surely* for all $i \le n$. Let
>$$
> \begin{align*}
> S &= \sum_{i=1}^{n} \left( X_i - \mathbb{E}_{}\left[ X_{i} \right] \right).
> \end{align*}
>$$ 
>Then for every $t > 0$,
>$$
>\begin{align}
> \mathcal{P}\{S \ge  t\} \le \exp \left( - \frac{2t^2}{\sum_{i=1}^{n}(b_i - a_i)^2}\right). 
>\end{align}
>$$ 



>[!important] Hoeffding's Inequality (Rademacher Random Variable)
>Let us consider the random variables 
>$$
> \begin{align*}
> X_i &= \epsilon_i \alpha_i, \quad i=1 \,{,}\ldots{,}\, n 
> \end{align*}
>$$  
>where $\epsilon_1 \,{,}\ldots{,}\, \epsilon_n$ are **independent** **Rademacher random variables** (i.e. **symmetric Bernoulli random variables** with $\mathcal{P}\{\epsilon_i = 1\} = \mathcal{P}\{\epsilon_i = -1\} = 1/2$) and $\alpha_1 \,{,}\ldots{,}\, \alpha_n$ are real numbers.  We get
>$$
> \begin{align*}
> \mathcal{P}\{S \ge  t \} \le \exp \left(- \frac{t^2}{2\sum_{i=1}^{n}\alpha_i^2} \right).
> \end{align*}
>$$ 


## Explanation

>[!info]
>There is one main conditions on the Bennet's inequality
>- $a\le X \le b, \text{a.s.}$, i.e. $X$ takes values in a **bounded interval almost surely**.

> [!info]
>This condition is stronger than Markov inequality


## Generalization

### Sub-Gaussian Random Variables

>[!important]  Hoeffding's Inequality for Sub-Gaussian Random Variable
>Let $X_1 \,{,}\ldots{,}\, X_n$ be **independent, sub-gaussian** random variables. Let
>$$
> \begin{align*}
> S &= \sum_{i=1}^{n} \left( X_i - \mathbb{E}_{}\left[ X_{i} \right] \right).
> \end{align*}
>$$ 
>Then for every $t > 0$,
>$$
>\begin{align}
> \mathcal{P}\{S \ge  t\} \le \exp \left( - \frac{c\, t^2}{\sum_{i=1}^{n} \lVert X_{i} \rVert_{\psi_2}^2}\right). 
>\end{align}
>$$ 

- [[Sub-Gaussian Random Variable]]
- [[Sub-Gaussian Norm]]
- [[High Dimensional Probability An Introduction by Vershynin]]

### Martingale Assumption

>[!info]
>Note that  we can *drop the independence assumption* among $X_{n}$. Instead, we can assume that *the sum* of $n$ random variables 
>$$
>S_{n} = \sum_{i=1}^{n} \left( X_i - \mathbb{E}_{}\left[ X_{i} \right] \right), \quad  n \ge 1
>$$
>forms a **martingale**. Then the martingale difference is 
>$$
>D_{n}:= S_{n} - S_{n-1} = X_{n} - \mathbb{E}\left[ E_{n} \right]
>$$

- Hoeffding inequality holds for martingale assumption too. See [[Azuma-Hoeffding Inequality]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]

### Convex Lipschitz Function of Sub-Gaussian Random Variable

![[Concentration of Separately Convex Lipschitz Functions#^ced8d1]]

![[Concentration of Separately Convex Lipschitz Functions#^8b2d89]]

- [[Concentration of Separately Convex Lipschitz Functions]]

### Functional Hoeffding Inequality

![[Functional Hoeffding Inequality#^3e5445]]

- [[Functional Hoeffding Inequality]]





-----------
##  Recommended Notes and References

- [[Independent Random Variables]]

- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]