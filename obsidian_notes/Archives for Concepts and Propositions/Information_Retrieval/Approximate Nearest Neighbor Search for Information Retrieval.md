---
tags:
  - concept
  - information_retrieval/search
  - information_retrieval/index
  - algorithm/tree
  - algorithm/search
  - machine_learning/algorithms
keywords:
  - approximate_nearest_neightbor_search
topics:
  - algorithm/search
  - information_retrieval/search
  - machine_learning_algorithm
name: 
date of note: 2024-11-29
---

## Concept Definition

>[!important]
>**Name**: Approximate Nearest Neighbor Search for Information Retrieval

>[!important] Definition
>Let $$\mathcal{D} := \left\{ x_{1}\,{,}\ldots{,}\,x_{n} \right\} $$ be a set of data in $\mathcal{X}$.
>- Denote $q\in \mathcal{X}$ be a *query point*.
>
>The task of the **approximate nearest neighbor (ANN) search** is to find the list of $k$ *ordered statistics* $$x^{(1)} \,{,}\ldots{,}\, x^{(k)}$$ in $\mathcal{D}$ so that $$d(q, x^{(1)}) \le d(q, x^{(2)}) \,{\le}\ldots{\le}\,d(q, x^{(k)}) \,{\le}\ldots{\le}\,d(q, x^{(n)}) $$
>where $d(\cdot, \cdot)$ is a metric in $\mathcal{X}$.
>- Note that an *exhaustive comparison* between $q$ and each sample in $\mathcal{D}$ is in $O(n)$, which is *prohibitive large* for large $n$.
>- This problem is more difficult for *high dimension data* $\mathcal{X} \subset \mathbb{R}^{d}$ when $d \gg n.$ This phenomenon is called the **curse of dimensionality.**
>- In practice, finding the **absolute nearest neighbor** is not necessary.
>- The **approximate nearest neighbor (ANN) search** is a class of *heuristic-based search algorithms*.

^fb4fa7


- [[k Nearest Neighbor Classification]]
- [[Order Statistics]]
- [[Curse of Dimensionality]]

## Explanation

>[!important] 
>There are several issues to consider:
>- **Effective Dimension**: Nearest-neighbor search gets progressively harder as the dimensionality increases.
>	- **Curse of Dimensionality**:
>		- Searches in high-dimensional spaces become hard because a sphere of radius $r$, representing all the points with distance $\le r$ from the center, progressively fills up *less volume relative to a cube* as the dimensionality increases. $$\frac{\text{Vol}(B(0, r(1+\epsilon)))}{\text{Vol}(B(0, r))} \approx (1 + \epsilon)^{d}$$
>	- One solution is for *dimensionality reduction*, which is used in **LSH**
>- **Exact Search vs. Approximate Search**:
>	- *Johnson-Linderstrauss Lemma* states that there exists projection that maps $n$ $d$-dimensional points into $$d' := O(\log n / \epsilon^2)$$ dimensional space that such that distance to the nearest neighbor in the low-dimensional space is within $(1+ \epsilon)$ times that of the actual nearest neighbor.
>- **Static or Dynamic** Data:
>	- If we need to frequently insert or delete samples in $\mathcal{D}$, we may need a dynamic data structure.

- [[Curse of Dimensionality]]
- [[Principal Component Analysis]]
- [[Johnson-Lindenstrauss Lemma for Dimensionality Reduction]]



## Algorithms for Approximate Nearest Neighbor 


- [[k-d Tree Structure for Approximate Nearest Neighbor Search]]
- [[Ball Tree Structure for Approximate Nearest Neighbor Search]]
- [[Locality-Sensitive Hashing or LSH]]
- [[Hierarchical Navigable Small Worlds or HNSW for Graph-based ANN Search]]


## Applications

### Classifications

- [[k Nearest Neighbor Classification]]

### Density Estimation

- [[k Nearest Neighbor Density Estimation]]

### Information Retrieval

- [[Information Retrieval with Encoder Language Models]]
- [[Retrieval Augmented Generation]]


-----------
##  Recommended Notes and References


- [[Locality-Sensitive Hashing or LSH]]
- [[Information Retrieval]]

- [[Metric Space]]
- [[Graph]]

- [[Algorithm Design Manual by Skiena]] pp 460, 638 - 647
- [[Introduction to Information Retrieval by Manning]]
- [[Speech and Language Processing by Jurafsky]] pp
- Youtube
	- [Graph-Based Approximate Nearest Neighbors (ANN) and HNSW](https://www.youtube.com/watch?v=4PsyNdFlxmk)
	- [[CVPR20 Tutorial] Billion-scale Approximate Nearest Neighbor Search](https://www.youtube.com/watch?v=SKrHs03i08Q)