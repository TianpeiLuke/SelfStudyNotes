---
tags:
  - concept
  - math/topology
  - math/functional_analysis
  - math/stochastic_process
  - statistics/concentration_inequality
keywords:
  - packing_number
  - epsilon_cover
topics:
  - topology
  - functional_analysis
  - stochastic_process
  - concentration_inequality
name: Packing Number of Metric Space
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: Packing Number of Metric Space

![[epsilon-Separated Set in Metric Space#^252e03]]

- [[epsilon-Separated Set in Metric Space]]

>[!important] Definition
>The **largest possible cardinality** of an *$\epsilon$-separated* subset of a given set $K \subset T$ is called  **the packing number of $K$** and is denoted $$\mathcal{P}(K, d,  \epsilon).$$

- [[Lebesgue Number Lemma in Compact Metric Space]]
- [[Metric Space]]

## Explanation



## Equivalence of Covering Number and Packing Number

>[!important] Theorem 
>Let  $(T, d)$ be a **complete metric space** and $K \subset T$ be any subset. 
>
>For any  $\epsilon > 0$, we have
>$$
> \begin{align}
> \mathcal{P}(K, d,  2\epsilon) \le \mathcal{N}(K, d, \epsilon) \le \mathcal{P}(K, d,  \epsilon)
> \end{align}
>$$ 

- [[Packing Number of Metric Space]]

## Relation with Error Correcting Code

>[!important] Proposition
>Assume that positive integers $k$, $n$ and $r$ are such that
>$$
> \begin{align}
> \log_2 \mathcal{P}(\set{0, 1}^n, d_H, 2r) \ge k. 
> \end{align}
>$$ 
> where $d_H$ is the **Hamming distance**. 
> 
> Then there exists an **error correcting code** that *encodes* $k$-bit strings *into* $n$-bit
> strings and can **correct $r$ errors**.

- [[Error Correcting Code]]



-----------
##  Recommended Notes and References


- [[Covering Number of Metric Space]]
- [[Covering of Set and Open Covering of Topological Set]]
- [[epsilon-Cover and epsilon-Net of Metric Space]]
- [[epsilon-Separated Set in Metric Space]]

- [[Lebesgue Number Lemma in Compact Metric Space]]
- [[Metric Space]]


- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]
- [[Topology Book by Munkres]]