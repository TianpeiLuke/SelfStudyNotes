---
tags:
  - concept
  - math/stochastic_process
  - machine_learning/theory
  - statistics/concentration_inequality
keywords:
  - growth_function
topics:
  - stochastic_process
  - machine_learning_theory
  - concentration_inequality
name: Growth Function of Function Class
date of note: 2024-06-01
---

## Concept Definition

>[!important]
>**Name**: Growth Function of Function Class

>[!important] Definition
>Let $\mathcal{F}$ be a class of *Boolean functions.* 
>
>Then the **growth function of $\mathcal{F}$**, denoted $$\tau_{\mathcal{F}}: \mathbb{N} \to \mathbb{N},$$ is defined as
>$$
> \begin{align*}
> \tau_{\mathcal{F}}(n) &:= \max \left\{|\mathcal{F}_{\mathcal{D}}|:  \mathcal{D} \subset \mathcal{X} \text{ such that } |\mathcal{D}| = n \right\}.
> \end{align*}
>$$ 
>
> In words, $\tau_{\mathcal{F}}(n)$ is the **number of different functions** from a set $\mathcal{D}$ of **size** $n$ to $\set{0,1}$ that can be obtained by *restricting* $\mathcal{F}$ to $\mathcal{D}$.

- [[Restriction of Function Class to Data]]


## Explanation

>[!info] 
>If $\mathcal{F}$ shatters $\mathcal{D}$,
>$$
>\tau_{\mathcal{F}}(|\mathcal{D}|) = 2^{|\mathcal{D}|}
>$$

- [[Shattering of Data by Function Class]]

>[!info]
>$$
>\text{VC-dim}(\mathcal{F}) := \max\left\{k \in \mathbb{N}: \tau_{\mathcal{F}}(k) = 2^k  \right\} 
>$$

- [[VC Dimension]]






-----------
##  Recommended Notes and References

- [[VC Dimension]]
- [[Restriction of Function Class to Data]]
- [[Shattering of Data by Function Class]]


- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Boosting Foundations and Algorithms by Schapire]]