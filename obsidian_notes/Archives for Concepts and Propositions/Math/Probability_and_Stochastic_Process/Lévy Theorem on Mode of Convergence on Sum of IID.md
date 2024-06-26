---
tags:
  - concept
  - math/probability
keywords:
  - levy_theorem_convergence_iid
topics:
  - probability
name: Levy Theorem on Convergence of Independent Random Variables
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: Lévy Theorem on Convergence of Independent Random Variables

>[!important] Levy's Theorem
>If $\left\{ X_{n},  n \ge 1 \right\}$ is a sequence of **independent** random variables,
>
>then 
>$$
>\begin{align*}
> &\sum_{j=1}^{n}X_{j} \text{ converges in probability } \\
>\iff\; & \sum_{j=1}^{n}X_{j} \text{ converges almost surely }.
\end{align*}
>$$
>
>This means that for $$S_{n} = \sum_{j=1}^n X_{j},$$ the following are **equivalent**:
>- $\{S_{n}\}$ is **Cauchy in probability**, i.e. for all $\epsilon >0$ and all $\delta \in (0, 1)$, there exists $N_{\sigma, \delta}$  such that for all  $n,m \ge N_{\sigma, \delta}$
>$$
> \mathcal{P}\left\{  | S_{n} - S_{m} | \ge \epsilon  \right\} \le \delta
>$$
>
>- $\{S_{n}\}$ **converges in probability**
>- $\{S_{n}\}$ **converges almost surely**, i.e. there exists some $\mu$
>$$
>\xi_{N} := \sup_{n \ge N}\left\lvert S_{n} - \mu \right\rvert \to 0, \quad \text{a.s.}
>$$
>- $\{S_{n}\}$ is **almost surely Cauchy.**
>$$
>\xi_{N} := \sup_{m, n \ge N}\left\lvert S_{n} - S_{m} \right\rvert \to 0, \quad \text{a.s.}
>$$


## Special Cases








## Explanation





-----------
##  Recommended Notes and References


- [[Independent Random Variables]]
- [[Expectation of Random Variable]]

- [[Pointwise Almost Everywhere Convergence]]
- [[Convergence in Measure]]


- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]