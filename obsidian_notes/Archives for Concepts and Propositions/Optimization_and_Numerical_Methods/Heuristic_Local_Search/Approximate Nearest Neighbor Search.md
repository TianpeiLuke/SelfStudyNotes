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
name: Approximate Nearest Neighbor Search
date of note: 2024-11-29
---

## Concept Definition

>[!important]
>**Name**: Approximate Nearest Neighbor Search

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

- [[Similarity Search]]
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
- Indyk, P., & Motwani, R. (1998, May). Approximate nearest neighbors: towards removing the curse of dimensionality. In _Proceedings of the thirtieth annual ACM symposium on Theory of computing_ (pp. 604-613).


## Algorithms for Approximate Nearest Neighbor 

### List-based Data Structure

- [[Shingling or n-Gram based Document Similarity Measure]]
- [[Inverted Index for Information Retrieval]]

### Tree-based Data Structure

- [[k-d Tree Structure for ANN Search]]
- [[Ball Tree Structure for ANN Search]]
- [[MinHash Algorithm for Approximate Nearest Neighbor Search]]

### Hash Table and Dimensionality Reduction

- [[Inverted File Index for ANN Search]]
- [[Product Quantization for ANN Search and Index Compression]]
- [[Inverted File Index - Product Quantization for ANN Search]]
## Code

- E. Bernhardsson, [ANN Benchmarks](https://github.com/erikbern/ann-benchmarks) (2021), GitHub
- Facebook Research, [Faiss HNSW Implementation](https://github.com/facebookresearch/faiss/blob/main/faiss/impl/HNSW.cpp), GitHub
- [[FAISS - Facebook AI Similarity Search Tutorial]]

- [[Locality-Sensitive Hashing or LSH for ANN Search]]
- [[MinHash Algorithm for ANN Search]]

### Graph-based Data Structure

- [[Navigable Small World Model and Kleinberg Variant of Watts-Strogatz Model]]
- [[Hierarchical Navigable Small Worlds or HNSW for Graph-based ANN Search]]

## Code

- E. Bernhardsson, [ANN Benchmarks](https://github.com/erikbern/ann-benchmarks) (2021), GitHub
- Facebook Research, [Faiss HNSW Implementation](https://github.com/facebookresearch/faiss/blob/main/faiss/impl/HNSW.cpp), GitHub
- [[FAISS - Facebook AI Similarity Search Tutorial]]


## Applications

### Classifications

- [[k Nearest Neighbor Classification]]

### Density Estimation

- [[k Nearest Neighbor Density Estimation]]

### Information Retrieval

- [[Inverted Index for Information Retrieval]]
- [[Information Retrieval with Encoder Language Models]]
- [[Retrieval Augmented Generation]]


-----------
##  Recommended Notes and References


- [[Similarity Search]]
- [[Indexing or Index Construction for Information Retrieval]]
- [[Information Retrieval]]
- [[Metric Space]]
- [[Graph]]

- [[Algorithm Design Manual by Skiena]] pp 460, 638 - 647
- [[Introduction to Information Retrieval by Manning]]
- [[Speech and Language Processing by Jurafsky]] pp

- Indyk, P., & Motwani, R. (1998, May). Approximate nearest neighbors: towards removing the curse of dimensionality. In _Proceedings of the thirtieth annual ACM symposium on Theory of computing_ (pp. 604-613).
- Li, W., Zhang, Y., Sun, Y., Wang, W., Li, M., Zhang, W., & Lin, X. (2020). Approximate Nearest Neighbor Search on High Dimensional Data—Experiments, Analyses, and Improvement. _IEEE Transactions on Knowledge and Data Engineering_, _32_(8), 1475–1488. IEEE Transactions on Knowledge and Data Engineering. [https://doi.org/10.1109/TKDE.2019.2909204](https://doi.org/10.1109/TKDE.2019.2909204)

- Youtube
	- [Graph-Based Approximate Nearest Neighbors (ANN) and HNSW](https://www.youtube.com/watch?v=4PsyNdFlxmk)
	- [[CVPR20 Tutorial] Billion-scale Approximate Nearest Neighbor Search](https://www.youtube.com/watch?v=SKrHs03i08Q)
	- [Approximate Nearest Neighbors : Data Science Concepts](https://www.youtube.com/watch?v=DRbjpuqOsjk)