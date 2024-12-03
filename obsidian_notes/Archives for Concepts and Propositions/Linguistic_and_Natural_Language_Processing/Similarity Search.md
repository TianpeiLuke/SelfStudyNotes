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


## Similarity Measure
#### Set-based Similarity Measure

- [[Jaccard Similarity and Jaccard Distance between Two Sets]]
- [[Shingling or n-Gram based Document Similarity Measure]]
- [[Minimum Edit Distance or Levenshtein Distance via Dynamic Programming]]

#### Similarity Measure in Vector Space

- [[Cosine Similarity and Cosine Distance]]
- [[Weighted Hamming Distance]]

#### Similarity Measure in Space of Probability Density Functions

- [[Concepts and Theorems in Information Theory]]
- [[Kullback-Leibler Divergence]]
- [[f-Divergence]]
- [[alpha-Divergence]]
- [[Renyi Divergence and Renyi Entropy]]
- [[Hellinger Distance between Distributions]]
- [[Jensen-Shannon Divergence]]
- [[Chi-squared Divergence]]
- [[Total Variation between Measures]]
- [[Integral Probability Metric between Probability Measures]]
- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]
- [[Wasserstein Distance]]


## Approximate k-Nearest Neighbor Search

- [[Approximate Nearest Neighbor Search]]
- [[k-d Tree Structure for Approximate Nearest Neighbor Search]]
- [[Ball Tree Structure for Approximate Nearest Neighbor Search]]
- [[Locality-Sensitive Hashing or LSH for Approximate Nearest Neighbor Search]]
- [[Navigable Small World Model and Kleinberg Variant of Watts-Strogatz Model]]
- [[Hierarchical Navigable Small Worlds or HNSW for Graph-based ANN Search]]




-----------
##  Recommended Notes and References

- [[k Nearest Neighbor Density Estimation]]

- [[FAISS - Facebook AI Similarity Search Tutorial]]
- [[Speech and Language Processing by Jurafsky]] 