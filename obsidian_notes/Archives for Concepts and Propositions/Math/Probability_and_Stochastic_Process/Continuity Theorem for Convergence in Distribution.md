---
tags:
  - concept
  - math/probability
  - math/functional_analysis
keywords:
  - convergence_in_distribution
  - levy_theorem_convergence_distribution
topics:
  - probability
name: Continuity Theorem for Convergence in Distribution
date of note: 2024-06-04
---

## Concept Definition

>[!important]
>**Name**: Lévy's Continuity Theorem for Convergence in Distribution

>[!important] Lévy's Continuity Theorem
>Let $(X_{n}, n \ge 1)$ be a sequence of **independent** random variables having *distribution* $\mathcal{P}_{i}$ and *characteristic function* $\phi_{i}(t).$
>
>1. If $$X_{n} \stackrel{d}{\longrightarrow} X_{0},$$ then for all $t\in \mathbb{R}$,  $$\phi_{n}(t) \rightarrow \phi_{0}(t).$$
>
>2. **Conversely**, if
>	- $\phi_{n}(t)$ **converges** at $n\to \infty$, i.e.  there exists some function $\phi_{\infty}(t)$ such that for all $t\in \mathbb{R}$  $$\phi_{n}(t)\rightarrow \phi_{\infty}(t),$$
>	- and $\phi_{\infty}(t)$ is **continuous** *at origin* $0$, 
>
>     then there *exists* some *distribution function* $\mathcal{P}_{\infty}$ so that $$\mathcal{P}_{n} \stackrel{d}{\longrightarrow} \mathcal{P}_{\infty},$$ and $\phi_{\infty}(t)$ is the *characteristic function* of $\mathcal{P}_{\infty}$.
>
>If furthermore, $\phi_{\infty}(0)=1$, then $F_{\infty}$ is **proper.**

^11ddd4

- [[Independent Random Variables]]
- [[Convergence in Distribution]]
- [[Characteristic Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Continuous Function]]


## Explanation






-----------
##  Recommended Notes and References

- [[Independent Random Variables]]
- [[Convergence in Distribution]]
- [[Characteristic Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Continuous Function]]


- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]

- [[Real Analysis Modern Techniques and Their Applications by Folland]]