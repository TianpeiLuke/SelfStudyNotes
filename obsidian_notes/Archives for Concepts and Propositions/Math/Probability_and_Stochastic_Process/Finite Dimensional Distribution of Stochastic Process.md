---
tags:
  - concept
  - math/stochastic_process
  - math/probability
  - math/measure_theory
  - math/functional_analysis
keywords:
  - stochastic_process
  - finite_dimensional_distribution
topics:
  - stochastic_process
  - probability
  - measure_theory
  - functional_analysis
name: Finite Dimensional Distribution of Stochastic Process
date of note: 2024-05-30
---

## Concept Definition

>[!important]
>**Name**: Finite Dimensional Distribution of Stochastic Process

![[Stochastic Process#^963482]]

>[!important] Definition
>For a stochastic process $X: (\Omega, \mathscr{F}, \mathcal{P}) \to \mathcal{X}^T$ with *law* $\mu$, the **finite dimensional distribution** for  $\set{t_1 \,{,}\ldots{,}\, t_n} \subset T$ is defined as
>$$
>\mu_{t_1 \,{,}\ldots{,}\, t_n} := \mathcal{P} \circ \left( X_{t_{1}} \,{,}\ldots{,}\, X_{t_{n}}\right)^{-1}.
>$$
>The measure $\mu_{t_1 \,{,}\ldots{,}\, t_n}$ is the **joint distribution** of random vector $\left( X_{t_{1}} \,{,}\ldots{,}\, X_{t_{n}}\right).$
>


- [[Stochastic Process]]
- [[Random Element and Random Variable]]
- [[Push-forward Measure and Push-forward Operator]]

>[!info]
>It is viewed as **projection** onto a **finite product space** indexed by  $S \subset T$, where $|S| = n$.
>$$
>\left( X_{t_{1}} \,{,}\ldots{,}\, X_{t_{n}}\right) := \pi_{t_{1} \,{,}\ldots{,}\, t_{n}}: \mathcal{X}^{T} \to \mathcal{X}^{S}
>$$


## Explanation

>[!info]
>By [[Product Measure on Infinite Product Space]], for any **product measure** defined on **infinite dimensional space** $\mu_{T}$, the finite dimensional distribution $\mu_{C}: \prod_{t\in C}\mathscr{F}_{t} \to [0,+\infty]$ as 
>$$
>\mu_{C} := \pi_{C, \#}(\mu_{T})
>$$
>is **well defined**. 
>
>Here $C\subset T$ is *finite* and  $\pi_{C}$ is the projection from $\prod_{t\in T}\mathcal{X}_{t} \to \prod_{t\in C}\mathcal{X}_{t}$. $\pi_{C, \#}(\mu_{T})$ is the push-forward operator on measure by $\pi_{C}.$

- [[Arbitrary Cartestian Products]]
- [[Finite Set and Cardinality]]
- [[Canonical Projection]]
- [[Push-forward Measure and Push-forward Operator]]



-----------
##  Recommended Notes and References



- [[Random Element and Random Variable]]
- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[sigma Algebra]]

- Wikipedia [Stochastic process](https://en.wikipedia.org/wiki/Stochastic_process)