---
tags:
  - concept
  - information_retrieval/index
  - information_retrieval/search
  - algorithm/search
  - machine_learning/clustering
keywords:
  - product_quantization_index
  - inverted_file_index_search
topics:
  - information_retrieval/index
  - information_retrieval/search
  - algorithm/search
  - machine_learning/clustering
name: Inverted File Index for ANN Search
date of note: 2024-12-03
---

## Concept Definition

>[!important]
>**Name**: Inverted File Index for ANN Search

![[Inverted Index for Information Retrieval#^e1bebe]]

### Inverted File Index

>[!important] Definition
>Let $q \in \mathbb{R}^{d}$ be a vector representation of query, 
>
>The **inverted file index (IVF)** will use a *hash function* to convert the query vector $q$ into $h(q)$ $$q \to h(q)$$
>- Each hashed value contains its own set of *potential candidates for nearest neighbors* $$h(q) \to [d_{1}\,{,}\ldots{,}\,d_{m}] := \text{IVF}(h(q))$$
>- Then the *ANN search* is *within this candidate list* $$x^{*} = \arg\min_{x\in \text{IVF}(h(q))}d(x, q)$$

^8d02f1

- [[Hash Table for Efficient Retrieval and Inverse Map]]
- [[Inverted Index for Information Retrieval]]
- [[Approximate Nearest Neighbor Search]]
- [[Cosine Similarity and Cosine Distance]]

![[inverted_file_index_knn.png]]

### Voronoi Diagram or Dirichlet Tessellation 

>[!important] Definition
>The following steps implement the **inverted file index (IVF)** via **Voronoi Diagram (Dirichlet Tessellation)**:
>- Create $k$ clusters for given data set $\mathcal{D}$ so that each data is assigned with a cluster
>	- Define the *hash function* for $x\in \mathcal{D}$ as the *assignment* to cluster $$h(x) := \text{clusterID}(x) := \arg\min_{i =1\,{,}\ldots{,}\,k}d(\mu_{i}, x)$$ where $\mu_{i}$ is the *centroid* of the cluster $C_{i}$
>- Create a *inverted index*, where each *hashed value* is mapped to a  *posting list* that consists of a files $x\in \mathcal{D}$ that mapped to given index. $$k \to [d_{1}\,{,}\ldots{,}\,d_{m}], \quad h(d_{t}) =k $$
>	- We can store the *residual vector* of each sample to the cluster centroid $$h(d_{t}) =k \implies d_{t} \in C_{k} \implies r_{t} := d_{t} - \mu_{k}$$
>	- The *inverted list* $$k \to [r_{1}\,{,}\ldots{,}\,r_{m}], \quad r_{t} = d_{t} - \mu_{k}$$
>- Thus the *ANN search* is done by comparing query with the corresponding items in *posting list* $$x^{*} = \arg\min_{x\in C_{k}(q)}d(x, q)$$

- [[k-Means Clustering]]

![[inverted_file_index_cluster.png]]


## Explanation

>[!info]
>**Inverted File Index** is based on **vector quantization**.



## IVF + PQ Indexing

- [[Product Quantization for ANN Search and Index Compression]]
- [[Inverted File Index - Product Quantization for ANN Search]]

### FAISS Implementation of IVF + PQ Indexing

- [[FAISS - Facebook AI Similarity Search Tutorial]]


-----------
##  Recommended Notes and References


- [[Similarity Search]]
- [[Indexing or Index Construction for Information Retrieval]]
- [[Information Retrieval]]

- [[Representation Learning]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Denoising Auto-Encoder]]


- Youtube
	- [IVF Vector Index | Vector Database Fundamentals](https://www.youtube.com/watch?v=VOerTAir9SU)

- Medium
	- [Similarity Search, Part 1: kNN & Inverted File Index](https://towardsdatascience.com/similarity-search-knn-inverted-file-index-7cab80cc0e79)



- Jégou, H., Douze, M., & Schmid, C. (2011). Product Quantization for Nearest Neighbor Search. _IEEE Transactions on Pattern Analysis and Machine Intelligence_, _33_(1), 117–128. IEEE Transactions on Pattern Analysis and Machine Intelligence. [https://doi.org/10.1109/TPAMI.2010.57](https://doi.org/10.1109/TPAMI.2010.57)  [[jegouProductQuantizationNearest2011]]