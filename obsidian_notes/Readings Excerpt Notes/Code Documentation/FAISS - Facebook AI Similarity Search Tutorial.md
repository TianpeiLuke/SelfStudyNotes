---
tags:
  - code
  - package
  - llm/similarity_search
keywords:
  - faiss
  - similarity_search
  - retrieval_augmented_generation
topics:
  - similarity_search
language: c++
name: FAISS - Facebook AI Similarity Search
date of note: 2024-07-29
proprietary?: No
---

## Code Repository Summary:

>[!quote]
>FAISS (Facebook AI Similarity Search) is a library that allows developers to quickly search for embeddings of multimedia documents that are similar to each other. It solves limitations of traditional query search engines that are optimized for hash-based searches, and provides more scalable similarity search functions.

### The Task of FAISS

>[!quote]
>In Faiss terms, the data structure is an _index_, an object that has an _add_ method to add $x_i$ vector. Note that the dimension of $x_i$ is assumed to be fixed.
> 
> Computing the argmin is the _search_ operation on the index.
> 
> This is all what Faiss is about. It can also:
> 
> - return not just the nearest neighbor, but also the 2nd nearest, 3rd, ..., *$k$-th nearest neighbor*
>     
> - search several vectors at a time rather than one (batch processing). For many index types, this is faster than searching one vector after another
>     
> - trade precision for speed, ie. give an incorrect result 10% of the time with a method that's 10x faster or uses 10x less memory
>     
> - perform maximum inner product search $\arg\max_{i}<x,x_{i}>$ instead of minimum Euclidean search. There is also limited support for other distances ($L_{1}$, $L_{\infty}$, etc.).
>     
> - return all elements that are *within a given radius* of the query point (range search)
>     
> - store the index on *disk* rather than in RAM
>     
> - index *binary vectors* rather than floating-point vectors
>     
> - ignore a subset of index vectors according to a *predicate* on the vector ids.






******
## Code Install Page

- https://github.com/facebookresearch/faiss/blob/main/INSTALL.md

## Code Manual

- https://github.com/facebookresearch/faiss/wiki





-----------
##  Recommended Notes


- [[Hierarchical Navigable Small Worlds or HNSW for Graph-based ANN Search]]
- [[Navigable Small World Model and Kleinberg Variant of Watts-Strogatz Model]]


- [[Inverted File Index for ANN Search]]
- [[Product Quantization for ANN Search and Index Compression]]
- [[Inverted File Index - Product Quantization for ANN Search]]


- [[k Nearest Neighbor Density Estimation]]
- [[MinHash Algorithm for ANN Search]]
- [[Locality-Sensitive Hashing or LSH for ANN Search]]


- [[k-d Tree Structure for ANN Search]]
- [[Approximate Nearest Neighbor Search]]
- [[Similarity Search]]


-----------
## Citations



- Reference: https://ai.meta.com/tools/faiss/
- Github [https://github.com/facebookresearch/faiss](https://github.com/facebookresearch/faiss)
- Youtube
	- [Faiss - Introduction to Similarity Search](https://www.youtube.com/watch?v=sKyvsdEv6rk)
	- [Index 2024 Talk: Vector Search and the FAISS Library](https://www.youtube.com/watch?v=jIn2ElPSyUc)