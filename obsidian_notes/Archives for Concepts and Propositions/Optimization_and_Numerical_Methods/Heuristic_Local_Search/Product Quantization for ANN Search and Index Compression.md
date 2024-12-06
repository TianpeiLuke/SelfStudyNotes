---
tags:
  - concept
  - information_retrieval/index
  - information_retrieval/search
  - algorithm/search
  - machine_learning/clustering
keywords:
  - product_quantization_index
topics:
  - information_retrieval/index
  - information_retrieval/search
  - algorithm/search
  - machine_learning/clustering
name: Product Quantization for ANN Search and Index Compression
date of note: 2024-12-03
---

## Concept Definition

>[!important]
>**Name**: Product Quantization for ANN Search and Index Compression

### Indexing via Production Quantization

>[!important] Definition
>The **product quantization (PQ)** can be obtained as follows
>- divide each data vector into a set of $m$ *sub-vectors* of *equal dimension* $$v := [v^{1} \,{,}\ldots{,}\,v^{m}], \quad v^{i} \in \mathbb{R}^{d / m}$$
>	- It decompose the sample space into the *direct sum* of $m$ *subspaces* $$\mathcal{X} := \mathcal{X}_{1} \,{\oplus}\ldots{\oplus}\, \mathcal{X}_{m}$$
>- *group* sub-vectors $v^{i}$ into $k$ *clusters* for each $i=1\,{,}\ldots{,}\,m$, 
>	- denote the cluster $j$ for sub-vectors $v^{i}$ as $C_{i,j}$
>- find the *centroid* for each cluster, called the **reproduction values** 
>	- denote the centroid for cluster $C_{i,j}$ as $\mu_{i,j}$
>- *map* each sub-vector to its *nearest centroid*, referred to as the **quantized sub-vectors** $$q(v^{i}) = \mu_{i,j} \implies \mu_{i,j} = \arg\min_{\mu\in \left\{ \mu_{i,1} \,{,}\ldots{,}\,\mu_{i,k}\right\}}d(\mu, v^{i}) $$
>- assign the sub-vector the corresponding **reproduction value IDs** $$\mu_{i,j} \to I_{i,j}$$
>	- **reproduction values** is the assigned cluster ID.
>- Thus the *quantization* of $v$ is $$v \to q(v) = [I_{1,j_{1}} \,{,}\ldots{,}\,I_{m,j_{m}}]$$

^4d9624

- [[k-Means Clustering]]
- [[Indexing or Index Construction for Information Retrieval]]

![[prod_quant_subvector.png]]

![[prod_quant_reprod_map.png]]

![[pq_encoding.png]]

### Symmetric and Asymmetric Distance Computation

>[!important] Definition
>Let $q(v)$ be the *product quantization code* of vector $v \in \mathcal{X}$. $$q(v) := (I_{1}(v) \,{,}\ldots{,}\,I_{m}(v))$$ where
>- $I_{i}(u)$ is the corresponding *centroid id* for the vector $u^{i}$, $$I_{i}(u) := \arg\min_{j=1\,{,}\ldots{,}\,k}d(\mu_{i,j}, u^{i})$$
>- and $\mu_{i,j}$ is the $j$-th centroid in $i$-th subspace.
>
>The **symmetric distance computation (SDC)** between two vectors $u, v\in \mathcal{X}$ is defined as the distance between two **product-quantized vectors**
>$$
>\hat{d}(u, v) := d(q(u), q(v)) := \sqrt{ \sum_{i=1}^{m}d^2(\mu_{i, I_{i}(u)}, \mu_{i, I_{i}(v)}) }
>$$

![[pq_distance.png]]

>[!important] Definition
>Let $q(v)$ be the *product quantization code* of vector $v \in \mathcal{X}$. $$q(v) := (I_{1}(v) \,{,}\ldots{,}\,I_{m}(v))$$ where
>- $I_{i}(u)$ is the corresponding *centroid id* for the vector $u^{i}$, $$I_{i}(u) := \arg\min_{j=1\,{,}\ldots{,}\,k}d(\mu_{i,j}, u^{i})$$
>- and $\mu_{i,j}$ is the $j$-th centroid in $i$-th subspace.
>
>The **asymmetric distance computation (ADC)** between two vectors $u, v\in \mathcal{X}$ is defined as the distance between *actual query* $u$ and *product-quantized keys* $q(v)$
>$$
>\hat{d}(u, v) := d(u, q(v)) := \sqrt{ \sum_{i=1}^{m}d^2(u^{i}, \mu_{i, I_{i}(v)}) }
>$$

- [[Approximate Nearest Neighbor Search]]
- [[Cosine Similarity and Cosine Distance]]


>[!info]
>Note that the **asymmetric distance computation** is close to **real distance computation**
>$$
>d(v, q(x)) \approx d(v, x)
>$$
>*only if* $$q(x) - x \approx 0$$

![[pq_distance_approx.png]]

>[!info]
>The **asymmetric distance computation** is closer to $d(v,x)$  as compared to the **symmetric version** $$\lVert d(v,x) - d(q(v), q(x))  \rVert  \ge \lVert d(v,x) - d(v, q(x))  \rVert$$ 

![[pq_asymmetric_distance.png]]

>[!quote]
>One can see that **SDC** and **ADC** have the *same query preparation cost*, which does not depend on the data set size $n$. 
>- When $n$ is *large* ($n > k D$), the **most consuming operations** are the *summations* in (12) and (13). 
>- The complexity given in this table for *searching the $k$ smallest elements* is the *average complexity* for $n k$ and when the elements are arbitrarily ordered ([23], Section 5.3.3, (17)). 
>  
>The **only advantage** of **SDC** over **ADC** is to *limit the memory usage* associated with the *queries*, as the query vector is defined by a code. 
>- This is, in most cases, *not relevant* and one should then use the **asymmetric version**, which obtains a lower distance distortion for a similar complexity. 
>
>  
>-- Jégou, H., Douze, M., & Schmid, C. (2011). Product Quantization for Nearest Neighbor Search. _IEEE Transactions on Pattern Analysis and Machine Intelligence_, _33_(1), 117–128. IEEE Transactions on Pattern Analysis and Machine Intelligence. [https://doi.org/10.1109/TPAMI.2010.57](https://doi.org/10.1109/TPAMI.2010.57)  [[jegouProductQuantizationNearest2011]]


### Optimized ANN Search Approach via Partial Distance

>[!important] Definition
>The *approximate nearest neighbor search* based on  **product quantization** is described as follows
>- divide the query vector into $m$ sub-vectors $$v = [v^1\,{,}\ldots{,}\,v^{m}]$$
>- compute the **partial distance** between *query sub-vectors* $v^{i}$ to *centroid* $\mu_{i,j}$ of every cluster $C_{i,j}$ in corresponding subspace $i$  $$d_{i,j} := d(v^{i}, \mu_{i,j}), \quad j=1\,{,}\ldots{,}\,k,\; i=1\,{,}\ldots{,}\,m$$
>- store the *partial distances* as $$d := [d_{i,j}]$$
>- The **PQ code** of each key $x$ indicate the closest centroid* $$I_{i}(x) := \arg\min_{j=1\,{,}\ldots{,}\,k}d(\mu_{i,j}, x^{i})$$
>	- The **PQ code**  is $$q(x) = [I_{1}(x) \,{,}\ldots{,}\,I_{m}(x)]$$
>- The **asymmetric distance computation (ADC)** between query $v$ and key $x$ is given by $$d(v, x) \approx d(v, q(x)) := \sqrt{ d_{1,I_{1}(x)}^2 \,{+}\ldots{+}\, d_{m, I_{m}(x)}^2}$$
>	- for each subvector $$d(v^{i}, I_{i}(x)) := d(v^{i}, \mu_{i,I_{i}(x)})$$
>- Find $k$-nearest neighbor based on the *approximated distance* $$x^{*} = \arg\min_{x\in \mathcal{D}}d(v,q(x)) \approx \arg\min_{x\in \mathcal{D}}d(v,x)$$

^81f958


![[pq_residual_storage.png]]

![[pq_distance_query_key.png]]

### Inverted File Index + PQ Indexing System and ANN Search

- [[Inverted File Index - Product Quantization for ANN Search]]
- Youtube [Faiss - Vector Compression with PQ and IVFPQ (in Python)](https://www.youtube.com/watch?v=BMYBwbkbVec&t=67s)


![[inverted_index_asym_dist_comp.png]]

## Explanation

>[!info]
>**Product Quantization** is based on **vector quantization**.

>[!info]
>**Product Quantization** can be seen as a **tokenization** method for numerical vectors.

- [[Tokenization of Words and Subwords and SentencePiece Tokenization]]

### Distance Metrics for Product Quantization

>[!quote]
>So far have looked at how to *approximate euclidean distance* by using **partial distances**. Let us generalize the rule for other metrics as well.
> 
> Imagine we would like to calculate a *distance metric* between a pair of vectors. If we know the metrics’ formula, we can directly apply it to get the result. But sometimes we can do it *by parts* in the following manner:
> 
> - Both vectors are divided into _n_ subvectors.
> - For each pair of respective subvectors, the distance metric is calculated.
> - Calculated _n_ metrics are then *combined* to produce the actual distance between the original vectors.
> 
>**Euclidean distance** is an example of a metric which can be calculated by parts.
>
>**Inner product** is another example of such metric with aggregation functions.
>
>In the context of **product quantization**, this is a very *important property* because during inference the algorithm calculates distances *by parts*. This means that it would be much more problematic to use metrics for product quantization that do not have this property. **Cosine distance** is an example of such metric.
>
>If there is still a need to use a metric without this property, then *additional heuristics* need to be applied to aggregate partial distances with some error. 
>
>-- [Similarity Search, Part 2: Product Quantization](https://towardsdatascience.com/similarity-search-product-quantization-b2a1a6397701)



### FAISS Implementation of IVF + PQ Indexing

- [[FAISS - Facebook AI Similarity Search Tutorial]]


## Quantization vs. Dimensionality Reduction

- [[Metric Entropy of Metric Space]]
- [[Johnson-Lindenstrauss Lemma for Dimensionality Reduction]]



-----------
##  Recommended Notes and References


- [[Similarity Search]]
- [[Indexing or Index Construction for Information Retrieval]]
- [[Information Retrieval]]
- [[Representation Learning]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Denoising Auto-Encoder]]


- Youtube
	- [Product Quantization for Vector Similarity Search (+ Python)](https://www.youtube.com/watch?v=t9mRf2S5vDI)

- Medium
	- [Similarity Search, Part 2: Product Quantization](https://towardsdatascience.com/similarity-search-product-quantization-b2a1a6397701)
	- [Similarity Search, Part 3: Blending Inverted File Index and Product Quantization](https://towardsdatascience.com/similarity-search-blending-inverted-file-index-and-product-quantization-a8e508c765fa)

- Jégou, H., Douze, M., & Schmid, C. (2011). Product Quantization for Nearest Neighbor Search. _IEEE Transactions on Pattern Analysis and Machine Intelligence_, _33_(1), 117–128. IEEE Transactions on Pattern Analysis and Machine Intelligence. [https://doi.org/10.1109/TPAMI.2010.57](https://doi.org/10.1109/TPAMI.2010.57)  [[jegouProductQuantizationNearest2011]]