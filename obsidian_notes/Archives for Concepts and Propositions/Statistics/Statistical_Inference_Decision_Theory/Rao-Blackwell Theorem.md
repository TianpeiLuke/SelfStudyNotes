---
tags:
  - concept
  - statistics/estimation
  - math/probability
  - math/convex_analysis
keywords:
  - rao-blackwell_theorem
  - sufficient_statistic
topics:
  - statistics/decision_theory
name: Rao-Blackwell Theorem
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Rao-Blackwell Theorem

![[Convex Decision Problem#^34756f]]


>[!important] Rao-Blackwell Theorem
>Let $T$ be a **sufficient statistic** for $\mathcal{P} \in \mathscr{P}$, and $T_{0}: \mathcal{X}\to \mathbb{R}^d$ be **non-randomized rule** satisfying 
>$$
>  \mathbb{E}_{ \mathcal{P} }\left[ \lVert T_{0} \rVert  \right] < \infty.
>$$
>Define $$T_{1} :=  \mathbb{E}_{ \mathcal{P} }\left[\, T_{0}(X) \,|\,T\, \right].$$
>
>Then $$R_{T_{1}}(\mathcal{P}) \le R_{T_{0}}(\mathcal{P})$$ for any $\mathcal{P} \in \mathscr{P}.$
>
>If $L(\mathcal{P}, \cdot)$ is **strictly convex** and $T_{0}$ is *not a function* of $T$, then $T_{0}$ is **inadmissible**.


- [[Sufficient Statistics]]
- [[Admissibility of Statistical Decision]]
- [[Conditional Expectation]]
- [[Convex Function]]

## Explanation


## Mininum Variance Unbiased  Estimation

- [[Minimum Variance Unbiased Estimation]]

>[!important]
>The **Rao-Blackwell Theorem** states that the **conditional mean estimator** 
>$$T_{1} :=  \mathbb{E}_{ \mathcal{P} }\left[\, T_{0}(X) \,|\,T\, \right]$$ as function of a *sufficient statistics* $T$ can achieve **lower risk** than original estimator $T_{0}$.
>
>That is, if a *sufficient statistic* $T$ is available, then we only need to consider the *estimator* that are **function of $T$**.




-----------
##  Recommended Notes and References


- [[Admissibility of Statistical Decision]]
- [[Convex Decision Problem]]
- [[Statistical Decision Problem]]



- [[All of Statistics A Concise Course by Wasserman]]

- [[Mathematical Statistics by Shao]] pp 117