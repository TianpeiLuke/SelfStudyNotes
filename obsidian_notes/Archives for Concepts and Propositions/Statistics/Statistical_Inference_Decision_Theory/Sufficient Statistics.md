---
tags:
  - concept
  - statistics/estimation
keywords:
  - sufficient_statistic
topics:
  - statistics
name: Sufficient Estimator
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Sufficient Estimator

>[!important] Definition
>Let $X$ be a sample from an unknown population $\mathcal{P} \in \mathscr{P}$, where $\mathscr{P}$ is *a family of populations*. 
>
>A statistic $T(X)$ is said to be **sufficient** for $\mathcal{P} \in \mathscr{P}$, (or for $\theta \in \Theta$ when $$\mathscr{P} := \{ \mathcal{P}_{\theta} :  \theta \in \Theta \}$$ 
>is a *parametric family*)  if and only if the *conditional distribution* of $X$ given $T$ is *known* does *not depend on* $\mathcal{P}$ or  $\theta$.

^7c0a9f

- [[Statistics]]
- [[Parametric Models]]
- [[Conditional Probability]]
- [[Point Estimator]]

## Explanation

>[!important]
>Once we observe $X$ and compute a *sufficient statistic* $T(X)$, the original data $X$ do *not contain any
> further information* concerning the unknown population P (since its conditional distribution is unrelated to $P$) and can be discarded. 
> 
> **A sufficient statistic $T(X)$ contains all information about $P$ contained in $X$**  and provides a reduction of the data if $T$ is *not one-to-one*.

>[!important]
>The concept of *sufficiency* **depends on the given family** $\mathcal{P}$. 

## Factorization

>[!important] Factorization Theorem for Sufficient Statistic
>Suppose that $X$ is a sample from $\mathcal{P} \in \mathscr{P}$ is a *family* of probability measures on $(\Omega^n, \mathscr{B}^n)$ dominated by a *$\sigma$-finite measure* $\nu$. 
>
>Then the statistic $T(X)$ is **sufficient** for $\mathcal{P} \in \mathscr{P}$ *if and only if* 
>- there are **nonnegative** *Borel functions* $h$ (which **does not depend on** $\mathcal{P}$) on $(\Omega^n, \mathscr{B}^n)$ and 
>- $g_{P}$ (which **depends on** $\mathcal{P}$) on the range of $T$ such that 
>$$
> \frac{d\mathcal{P}}{d\nu}(x) = g_{P}\left(T(x)\right)h(x).
>$$

- [[Probability Density Function of Random Variable]]

## Rao-Blackwell Theorem

- [[Rao-Blackwell Theorem]]

## Data Processing Inequality

![[Data-Processing Inequality#^11ff5a]]

![[Data-Processing Inequality#^8aa0d2]]

- [[Mutual Information]]
- [[Data-Processing Inequality]]

>[!info]
>For any statistics, $$\theta \to X \to T(X)$$
>
>Thus $$I(\theta; X) \ge I(\theta; X \,|\,T(X))$$


-----------
##  Recommended Notes and References

- [[Statistics]]
- [[Conditional Probability]]
- [[Probability Distribution of Random Variable]]


- [[Complete and Bounded Complete Statistics]]
- [[Basu Theorem]]

- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 103
- [[Elements of Information Theory by Cover]] pp 36