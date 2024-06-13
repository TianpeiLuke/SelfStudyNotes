---
tags:
  - concept
  - math/information_theory
  - statistics/concentration_inequality
keywords:
  - han_inequality
topics:
  - information_theory
  - concentration_inequality
name: Han Inequality
date of note: 2024-05-23
---

## Concept Definition

>[!important]
>**Name**: Han Inequality

>[!important] Han's Inequality
>Let $X_1, X_2 \,{,}\ldots{,}\, X_n$ be random variables. 
>
>Then
>$$
> \begin{align}
> H(X_1, X_2 \,{,}\ldots{,}\, X_n) &\le \frac{1}{n-1}\sum_{i=1}^{n}H(X_1 \,{,}\ldots{,}\, X_{i-1}, X_{i+1} \,{,}\ldots{,}\, X_n)  \\
> \Leftrightarrow H(X) &\le \frac{1}{n-1}\sum_{i=1}^{n}H(X_{(-i)}) \nonumber
> \end{align}
>$$
>where $X_{(-i)}$ is the vector $X$ by **leaving out $i$-th element**.

- [[Shannon Entropy]]
- [[Jackknife Estimator of Variance]]


>[!important] Han's Inequality for Relative Entropy
>Let $(\mathcal{X}, \mathscr{B})$ be a measurable space, and $P$ and $Q$ be *probability measures* on $\mathcal{X}^{n}$ such that $$P = P_1 \,{\otimes}\ldots{\otimes}\, P_n$$ is a **product measure**. 
>
>We denote the element of $\mathcal{X}^{n}$ by $x = (x_1 \,{,}\ldots{,}\, x_n)$ and write $$x_{(-i)} := (x_1 \,{,}\ldots{,}\, x_{i-1}, x_{i+1} \,{,}\ldots{,}\, x_n)$$ for the (n-1)-vector obtained by **leaving out the $i$-th component** of $x$ (i.e. the $i$-th **Jackknife sample** of $x$). 
>
>Denote $Q_{(-i)}$ and $P_{(-i)}$ the **marginal distributions** of $Q$ and $P$. Let $p_{(-i)}$ and $q_{(-i)}$ denote the corresponding probability density function with respect to base measure $\mu$ on $\mathcal{X}$.
>$$
> \begin{align*}
> q_{(-i)}(x_{(-i)}) &= \int_{y \in \mathcal{X}}q(x_{(-i)}) d\mu(y)\\
> p_{(-i)}(x_{(-i)}) &= \int_{y \in \mathcal{X}}p(x_{(-i)}) d\mu(y)\\
> &= \prod_{j \neq i}p_{j}(x_j).
> \end{align*}
>$$  
>
>Then
>$$ 
> \begin{align}
> \mathbb{KL}\left(Q\left\|\right. P\right) &\ge \frac{1}{n-1}\sum_{i=1}^{n} \mathbb{KL}\left(Q_{(-i)} \left\|\right. P_{(-i)} \right)  
> \end{align}
>$$  
>or equivalently,
>$$ 
> \begin{align}
> \mathbb{KL}\left(Q\left\|\right. P\right) &\le \sum_{i=1}^{n}\left( \mathbb{KL}\left(Q\left\|\right. P\right)  - \mathbb{KL}\left(Q_{(-i)} \left\|\right. P_{(-i)} \right) \right).  
> \end{align}
>$$ 

- [[Kullback-Leibler Divergence]]


## Explanation





-----------
##  Recommended Notes and References

- [[Sub-Additivity of Entropy Functional and Tensorization]]
- [[Sub-Additivity of Phi Entropy Functional]]


- [[Shannon Entropy]]
- [[Kullback-Leibler Divergence]]

- [[Jackknife Estimator of Variance]]

- [[Elements of Information Theory by Cover]]
- [[Concentration Inequalities by Boucheron]]