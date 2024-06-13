---
tags:
  - concept
  - math/information_theory
  - statistics/concentration_inequality
keywords:
  - entropy_functional
  - sub_additivity
  - tensorization_entropy
topics:
  - concentration_inequality
  - information_theory
name: Sub-Additivity of Entropy Functional
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Sub-Additivity of Entropy Functional

>[!important] Proposition
>Define $\Phi(x) = x\log x$,  for $x >0$ and $\Phi(0) = 0$. 
>
>Let $Z_1, Z_2  \,{,}\ldots{,}\, Z_n$ be **independent random variables** taking values in $\mathcal{X}$, and let $f: \mathcal{X}^n \to [0, \infty)$ be a measurable function. Denote $Z_{(-i)}$ by **leaving-out** $i$-th element from the list of random variables:
>$$
>Z_{(-i)} := \left(Z_1, \,{,}\ldots{,}\, Z_{i-1}, Z_{i+1}, \,{,}\ldots{,}\, Z_{n} \right).
>$$
>
>Letting $X = f(Z_1, Z_2 \,{,}\ldots{,}\, Z_n)$ such that $$\mathbb{E}\left[  X\log X \right] < \infty,$$ we have 
>$$
> \begin{align}
> H_{\Phi}\left(X\right) = \text{Ent}\left(X\right)  &\le \sum_{i=1}^{n}\mathbb{E}\left[ \mathbb{E}_{(-i)}\left[  \Phi(X) \right] - \Phi(\mathbb{E}_{(-i)}\left[ X \right] \right],
> \end{align}
>$$  
>where $\mathbb{E}_{(-i)}\left[\cdot\right]$ is the **conditional expectation** operator **conditioning on $Z_{(-i)}$.** That is,
>$$
>\mathbb{E}_{(-i)}\left[  \Phi(X) \right] := \mathbb{E}\left[ \Phi(f(Z_1, Z_2 \,{,}\ldots{,}\, Z_n)) \;|\;  Z_1, \,{,}\ldots{,}\, Z_{i-1}, Z_{i+1}, \,{,}\ldots{,}\, Z_{n} \right].
>$$
>
>  Introducing the notation $$\text{Ent}_{(-i)}(X) := \mathbb{E}_{(-i)}\left[  \Phi(X) \right] - \Phi(\mathbb{E}_{(-i)}\left[ X \right]),$$ this inequality can be re-written as
> $$ 
> \begin{align}
> \text{Ent}\left(X\right) &\le \mathbb{E}\left[ \sum_{i=1}^{n} \text{Ent}_{(-i)}(X)\right].
> \end{align}
>$$ 
>We call the above inequality the **sub-additivity** of **entropy functional**.

- [[Jackknife Estimator of Variance]]

>[!info]
>We summarize the **sub-additivity of entropy functional** as the following property.


>[!important] Tensorization Property of Entropy Functional
>Let $\mu = \mu_1 \,{\otimes}\ldots{\otimes}\,\mu_n$ where $\mu_i$ be the probability distribution of $Z_i$. Thus $\mu$ is the *joint probability distribution* of $Z = (Z_1 \,{,}\ldots{,}\, Z_n)$ when $Z_i$ are **independent**. 
>
>The **tensoriztion property of entropy** states that
>$$
> \begin{align*}
> \text{Ent}_{\mu_1 \,{\otimes}\ldots{\otimes}\, \mu_n}(f) &\le  \mathbb{E}_{\mu_1 \,{\otimes}\ldots{\otimes}\, \mu_n }\left[ \sum_{i=1}^{n}\text{Ent}_{\mu_i}(f) \right]
> \end{align*}
>$$  
>where the subscript $\mu_i$ indicates that the **integration concerns the $i$-th variable only**.

^713eb4



## Explanation














-----------
##  Recommended Notes and References

- [[f-Divergence]]
- [[Kullback-Leibler Divergence]]

- [[Entropy Functional]]
- [[Phi Entropy Functional]]

- [[Jackknife Estimator of Variance]]

- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Elements of Information Theory by Cover]]