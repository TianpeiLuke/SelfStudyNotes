---
tags:
  - concept
  - math/stochastic_process
  - statistics/concentration_inequality
keywords:
  - sub_gaussian_process
topics:
  - stochastic_process
  - concentration_inequality
name: Sub-Gaussian Process
date of note: 2024-06-02
---

## Concept Definition

>[!important]
>**Name**: Sub-Gaussian Process

![[Sub-Gaussian Norm#^67d04f]]


- [[Sub-Gaussian Norm]]

>[!important] Definition
>Consider a *random process* $(X_t)_{t\in T}$ on a *metric space* $(T, d)$. 
>
>We say that the process has **sub-gaussian increments** if there exists $K \ge 0$ such that for any $t, s \in T$,
>$$
> \begin{align}
> \lVert X_{t} - X_{s} \rVert_{\psi_{2}}  &\le K\, d(t, s) 
> \end{align}
>$$ 

^61c82d

- [[Stochastic Process]]
- [[Sub-Gaussian Random Variable]]

- [[Contraction Function]]

## Explanation





-----------
##  Recommended Notes and References

- [[Sub-Gaussian Norm]]
- [[Sub-Gaussian Random Variable]]

- [[Stochastic Process]]


- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]