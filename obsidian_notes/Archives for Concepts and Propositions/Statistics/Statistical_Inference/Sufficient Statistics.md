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
>Let $X$ be a sample from an unknown population $P \in \mathcal{P}$, where $\mathcal{P}$ is *a family of populations*. 
>
>A statistic $T(X)$ is said to be **sufficient** for $P \in \mathcal{P}$, (or for $\theta \in \Theta$ when $$\mathcal{P} := \{ P_{\theta} :  \theta \in \Theta \}$$ 
>is a *parametric family*)  *if and only if* the *conditional distribution* of $X$ given $T$ is *known* (does *not depend on* $P$ or  $\theta$).

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
>Suppose that $X$ is a sample from $P \in \mathcal{P}$ is a *family* of probability measures on $(\Omega^n, \mathscr{B}^n)$ dominated by a *$\sigma$-finite measure* $\nu$. 
>
>Then the statistic $T(X)$ is **sufficient** for $P \in \mathcal{P}$ *if and only if* 
>- there are **nonnegative** *Borel functions* $h$ (which **does not depend on** $P$) on $(\Omega^n, \mathscr{B}^n)$ and 
>- $g_{P}$ (which **depends on** $P$) on the range of $T$ such that 
>$$
> \frac{dP}{d\nu}(x) = g_{P}\left(T(x)\right)h(x).
>$$





-----------
##  Recommended Notes and References

- [[Conditional Probability]]
- [[Probability Distribution of Random Variable]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]]