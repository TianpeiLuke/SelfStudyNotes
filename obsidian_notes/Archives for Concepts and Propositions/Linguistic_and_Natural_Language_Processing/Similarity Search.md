---
tags:
  - concept
  - llm/similarity_search
keywords:
  - similarity_search
topics:
  - similarity_search
name: Similarity Search
date of note: 2024-07-29
---

## Concept Definition

>[!important]
>**Name**: Similarity Search

>[!important] Definition
>Given a set of vectors $\left\{ x_{1} \,{,}\ldots{,}\, x_{n} \right\}$ in $\mathbb{R}^{d}$, and a vector $x\in \mathbb{R}^{d}$, the task of **similarity search** is to find the closest vector in the set to $x$, i.e. $$i = \arg\min_{i}d(x, x_{i})$$ where $d: \mathbb{R}^{d} \times \mathbb{R}^d \to \mathbb{R}_{+}$ is a *distance metric* in $\mathbb{R}^d$.

- [[k Nearest Neighbor Density Estimation]]
- [[Metric Space]]



## Explanation





-----------
##  Recommended Notes and References

- [[k Nearest Neighbor Density Estimation]]

- [[FAISS - Facebook AI Similarity Search Tutorial]]
- [[Speech and Language Processing by Jurafsky]] 