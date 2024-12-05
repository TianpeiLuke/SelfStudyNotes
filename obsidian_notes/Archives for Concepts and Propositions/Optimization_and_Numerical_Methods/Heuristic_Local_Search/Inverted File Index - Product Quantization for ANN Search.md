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
name: Inverted File Index - Product Quantization for ANN Search
date of note: 2024-12-03
---

## Concept Definition

>[!important]
>**Name**: Inverted File Index - Product Quantization for ANN Search

### Indexing via Production Quantization

![[Product Quantization for ANN Search and Index Compression#^81f958]]

- [[Product Quantization for ANN Search and Index Compression]]
- [[k-Means Clustering]]
- [[Indexing or Index Construction for Information Retrieval]]
- [[Approximate Nearest Neighbor Search]]

### Inverted File Index + PQ Indexing System


>[!important] Definition
>The *construction* of **Inverted File Index - Product Quantization (IVF-PQ)** is described as below
>- Groups the database $\mathcal{D} \subset \mathcal{X}$ into $k$ clusters (*Voronoi diagram*) $$C_{1}\,{,}\ldots{,}\,C_{k}$$
>- *Within* each cluster (Voronoi region), compute *residual vector* of the key $x_{t}\in \mathcal{D}$ to the corresponding centroid $$r_{t} := x_{t} - \mu_{i(t)}$$ where $$i(t) := \arg\min_{1\,{,}\ldots{,}\,k}d(\mu_{i}, x_{t})$$
>	- $r_{t}$ is the *centered* version of $x_{t}$ within the corresponding cluster
>- Apply the **product quantization** on each residual vector
>	- Split each *residual vector* $r_{t}$ into $m$ *sub-vectors*, $$r_{t} := (r_{t}^1 \,{,}\ldots{,}\,r_{t}^{m})$$
>	- Cluster each *sub-vector* $r_{t}^i$ within the corresponding *subspace* $i$
>		- Denote $c_{i,j}$ are the centroid of $j$-th cluster in subspace $i$
>	- Map the sub-vector of residual to *closest centroid* within subspace $$r_{t}^{i} \to c_{i,I_{i}(r_{t})}$$
>		- Denote $$I_{i}(r_{t}):=  \arg\min_{j=1\,{,}\ldots{,}\,k}d(c_{i,j}, r_{t}^{i})$$
>	- Replace the sub-vectors to be the clusterID $$r_{t} \to q(r_{t}) := [I_{1}(r_{t}) \,{,}\ldots{,}\,I_{m}(r_{t})]$$
>- The **inverted file index** is given by the map $$j \to [q(r_{1}) \,{,}\ldots{,}\, q(r_{T})]$$ where the *hashed value* $j$ is the cluster id for the *posting* $$h(r_{s}) := j = \arg\min_{1\,{,}\ldots{,}\,k}d(\mu_{i}, r_{s}), \quad s=1\,{,}\ldots{,}\,T$$

- [[k-Means Clustering]]
- [[Inverted File Index for ANN Search]]
- [[Inverted Index for Information Retrieval]]
- Youtube [Faiss - Vector Compression with PQ and IVFPQ (in Python)](https://www.youtube.com/watch?v=BMYBwbkbVec&t=67s)

>[!info]
>Since centering is within each cluster, we can do it *in parallel*.

![[invert_file_index_prod_quant_train.png]]

###  ANN Search via IVF-PQ System

>[!important] 
>The **ANN search** for a query $v$ based on **IVF-PQ** is given by the following steps 
>- Find the *$k$-nearest centroids* $\mu_{1}\,{,}\ldots{,}\,\mu_{k}$ of Voronoi partitions for query $v$ 
>- Compute the **residual vector** from query $v$ to *each centroid* separately $$v_{(s)} := v - \mu_{s}, \quad s=1\,{,}\ldots{,}\,k$$
>- Choose the **key residual vectors** in *selected regions* as *candidates*. $$W := \left\{ r_{t}:\, h(r_{t}) = s,\quad s = 1\,{,}\ldots{,}\,k \right\} $$
>- Spilt *query residual vector* (with respect to *each cluster centroid*)  into sub-vectors $$v_{(s)} := (v_{(s)}^{1}\,{,}\ldots{,}\,v_{(s)}^{m}), \quad s = 1\,{,}\ldots{,}\,k$$
>- Retrieve the subspace centroid $c_{i,j}$ for each subvector $i=1\,{,}\ldots{,}\,m$, $j=1\,{,}\ldots{,}\,T$
>- Compute the **partial distance matrix** between *query sub-vector* and *each subspace centroid* in each subspace and for *each selected Voronoi region* $$d_{i,j}^{(s)} := d(v_{(s)}^{i}, c_{i,j}), \quad i\in [m],\,  j\in [T],\, s\in [k]$$
>- The **asymmetric distance** between query $v$ and *candidate* $x\in W$ can be computed by *sum of partial distances* $$d(v, x) \approx d(v, q(x)) := \sqrt{ (d_{1,I_{1}(x)}^{(s)})^{2} \,{+}\ldots{+}\, (d_{m,I_{m}(x)}^{(s)})^{2} } $$ where 
>	- $s$ is the *Voronoi region* that contains the key $x$, $$s = h(x)$$
>	- and $I_{i}(x)$ is *$i$-th component* of  **PQ code** of $x$, which corresponds to the *closest cluster centroid id* for the subvector $x^{i}$, $$I_{i}(x) := \arg\min_{j=1\,{,}\ldots{,}\,k}d(c_{i,j}, x^{i})$$
>	- The *PQ code* of candidate $x$ $$q(x) := (I_{1}(x) \,{,}\ldots{,}\,I_{m}(x))$$
>- The **ANN search** is done by comparing the distance between query to candidates $$x^{*} = \arg\min_{x\in W}\;d(v, q(x)) \approx \arg\min_{x\in W}\;d(v, x)$$

>[!quote]
>After all the distances are calculated, the _k nearest neighbors_ need to be selected. 
>- To do it efficiently, authors propose maintaining a [MaxHeap](https://medium.com/@slavahead/heapify-with-heap-sort-5df23b5764c1) data structure. 
>- It has a limited capacity of _k_ and at each step, it stores _k_ *current smallest distances*. 
>- Whenever a new distance is calculated, its value is added to the **MaxHeap** only if the computed value is *less than the largest value* in the MaxHeap. 
>- After calculating all the distances, the answer to the query is already stored in the MaxHeap. 
>- The advantage of using the MaxHeap is its fast building time which is $$O(n).$$
>  
>-- [Similarity Search, Part 3: Blending Inverted File Index and Product Quantization](https://towardsdatascience.com/similarity-search-blending-inverted-file-index-and-product-quantization-a8e508c765fa)  
  


![[invert_file_index_prod_quant_inference.png]]




### IVF-PQ Indexing System


![[inverted_index_asym_dist_comp.png]]

## Explanation

>[!quote]
>The algorithm takes advantage of both **inverted file index** and **product quantization**. 
>- Depending on the *number of Voronoi partitions* probe during the inference, the *same number of subvector-to-centroid matrices* _d_ needs to be computed and **stored in the memory**. 
>- This might look like a downside but comparing it to overall advantages, it is a pretty good trade-off.
>  
>-- [Similarity Search, Part 3: Blending Inverted File Index and Product Quantization](https://towardsdatascience.com/similarity-search-blending-inverted-file-index-and-product-quantization-a8e508c765fa)  


## FAISS Implementation of IVF + PQ Indexing

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
	- [Product Quantization for Vector Similarity Search (+ Python)](https://www.youtube.com/watch?v=t9mRf2S5vDI)

- Medium
	- [Similarity Search, Part 2: Product Quantization](https://towardsdatascience.com/similarity-search-product-quantization-b2a1a6397701)
	- [Similarity Search, Part 3: Blending Inverted File Index and Product Quantization](https://towardsdatascience.com/similarity-search-blending-inverted-file-index-and-product-quantization-a8e508c765fa)

- Jégou, H., Douze, M., & Schmid, C. (2011). Product Quantization for Nearest Neighbor Search. _IEEE Transactions on Pattern Analysis and Machine Intelligence_, _33_(1), 117–128. IEEE Transactions on Pattern Analysis and Machine Intelligence. [https://doi.org/10.1109/TPAMI.2010.57](https://doi.org/10.1109/TPAMI.2010.57)  [[jegouProductQuantizationNearest2011]]