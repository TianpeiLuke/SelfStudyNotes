---
tags:
  - concept
  - math/stochastic_process
keywords:
  - step_process
topics:
  - stochastic_process
name: Step Process
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Step Process

>[!important] Definition
>Let $T \subset \mathbb{R}$ be a *compact subspace*. 
>
>A *stochastic process* $(X_{t}, t \in T)$ is called the **step process** if 
>- $X(\omega, t)$ is **jointly square-integrable** in $(\omega, t)$, i.e. $$\mathbb{E}_{ \mathcal{P} }\left[  \int_{T}X^2_{t}dt \right] < \infty,$$ and
>- there exists a *partition* $P$ of $T$, i.e. $$T = \bigcup_{i=1}^{n}T_{i}, \quad \text{ and }\quad T_{i}\cap T_{j} = \emptyset, \forall i\neq j, \;$$ such that for all $t\in T_{i}:= [t_{i}, t_{i+1})$, $i=1 \,{,}\ldots{,}\,n$,  $$X_{t} = X_{i}.$$ 
>  
 >Note that $X_{i}$ is $\mathscr{F}_{t_i}$-**measurable** random variable.

^57feed


- [[Progressively Measurable Stochastic Process]]
- [[Adapted Stochastic Process and Non-anticipating Process]]
- [[Stochastic Process]]
- [[Characteristic Function of Set]]



## Explanation





-----------
##  Recommended Notes and References

- [[Progressively Measurable Stochastic Process]]
- [[Adapted Stochastic Process and Non-anticipating Process]]
- [[Stochastic Process]]

- [[Ito Stochastic Integration of Step Process]]
- [[Simple Integral of Simple Functions]]

- [[Introduction to Stochastic Differential Equations by Evans]]