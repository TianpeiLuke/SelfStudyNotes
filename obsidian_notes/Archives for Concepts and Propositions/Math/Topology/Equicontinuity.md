---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - equicontinuity
topics:
  - functional_analysis
  - topology
name: Equicontinuity
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Equicontinuity


>[!important] Definition
>Let $\mathscr{F}$ be a *family of functions* from a metric space $(X, p)$ to another metric space $(Y, d)$. 
>
>We say $\mathscr{F}$ is an **equicontinuous family** if and only if for all $\epsilon >0$ and *all $x \in X$*, there exists $\delta > 0$ such that $$d(f(x), f(x')) < \epsilon$$ whenever $$p(x, x') < \delta$$ for *every $f \in \mathscr{F}$* and *all $x' \in X$*.


>[!important] Definition
>We say $\mathscr{F}$ is a **uniformly equicontinuous family** if and only if for all $\epsilon >0$, there exists $\delta > 0$ such that $$d(f(x), f(x')) < \epsilon$$ whenever $$p(x, x') < \delta$$ for *all $x, x' \in X$* and *every $f \in \mathscr{F}$*.


## Explanation

>[!important]
>- **Continuity** of the **specific**  *function* $f$ at $x_0$ means that for all $\epsilon >0$, there exists a $\epsilon$-neighborhood $U$ of $x_0$ such that for all $x \in U$, $$d(f(x), f(x_0)) < \epsilon.$$ 
>  Such neighborhood $U$ depends on both $\epsilon, x_{0}$ as well as $f$.
>- **Equicontinuity** of a *__family__ of functions* $\mathscr{F}$ means that a *single $\epsilon$-neighborhood* $U$ can be chosen that will **work for all the functions** $f\in \mathscr{F}$. 
>  Such neighborhood $U$ depends on both $\epsilon, x_{0}$ but *not choice of* $f$.

- [[Continuous Function]]


-----------
##  Recommended Notes and References

- [[Compactness]]
- [[Total Boundedness]]

- [[Metric Space]]
- [[Continuous Function]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)