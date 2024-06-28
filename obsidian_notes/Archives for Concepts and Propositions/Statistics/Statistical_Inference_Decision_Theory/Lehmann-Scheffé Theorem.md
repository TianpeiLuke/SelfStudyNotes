---
tags:
  - concept
  - statistics/estimation
keywords:
  - lehmann_scheffe_theorem
topics:
  - statistics/estimation
name: Lehmann-Scheffé Theorem
date of note: 2024-06-26
---

## Concept Definition

>[!important]
>**Name**: Lehmann-Scheffé Theorem

>[!important] Lehmann-Scheffé Theorem
>Suppose that there exists a **sufficient** and **complete statistic** $T(X)$ for $\mathcal{P} \in \mathscr{P}$. 
>
>If $\theta$ is *estimable*, then there is a **unique (up to a $\mathcal{P}$-null set) unbiased estimator** of $\theta$ that is of the form $$h(T)$$ with a *Borel function* $h$.  
>
>Furthermore, $h(T)$ is the **unique UMVUE** of $\theta$.

^e0b496

- [[Uniformly Minimum Variance Unbiased Estimation]]
- [[Sufficient Statistics]]
- [[Complete and Bounded Complete Statistics]]
- [[Mathematical Statistics by Shao]] pp 162


## Explanation

>[!important]
>This theorem is the consequence of **Rao-Blackwell Theorem**, which states that
>$$
>T_{1} := \mathbb{E}_{ \mathcal{P} }\left[\, T_{0}(X) \,|\,T\, \right]
>$$
>is at least **as good as** $T_{0}$ itself.
>
>This shows that the **conditional mean estimator** is UMVU estimatior.

- [[Rao-Blackwell Theorem]]
- [[Admissibility of Statistical Decision]]




-----------
##  Recommended Notes and References


- [[Uniformly Minimum Variance Unbiased Estimation]]
- [[Sufficient Statistics]]
- [[Complete and Bounded Complete Statistics]]


- [[Measurable Function]]
- [[Borel sigma Field]]

- [[Mathematical Statistics by Shao]] pp 162