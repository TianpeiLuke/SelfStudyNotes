---
tags:
  - concept
  - information_retrieval/index
  - information_retrieval/search
  - algorithm/search
  - machine_learning/dimensionality_reduction
  - algorithm/hash_table
keywords:
  - locality_sensitive_hashing
  - lsh_algorithm
  - approximate_nearest_neightbor_search
topics:
  - algorithm/search
  - information_retrieval/search
  - algorithm/hash_table
  - machine_learning/dimensionality_reduction
name: Locality-Sensitive Hashing or LSH for Approximate Nearest Neighbor Search
date of note: 2024-11-29
---

## Concept Definition

>[!important]
>**Name**: Locality-Sensitive Hashing or LSH for Approximate Nearest Neighbor Search

>[!info]
>The idea of **LSH**
>- $k$ *random hyperplanes* split the space into $2^k$ regions
>- compare *only* with points in the *same region*
>  
>$$
>v \to \text{sgn}(Pv)
>$$  

- [[Approximate Nearest Neighbor Search]]
- [[Gaussian Random Projections]]
- [[Johnson-Lindenstrauss Lemma for Dimensionality Reduction]]
- [[Hash Table for Efficient Retrieval and Inverse Map]]

![[lsh_process.png]]

### LSH Search 


- [[Shingling or n-Gram based Document Similarity Measure]]
- [[Jaccard Similarity and Jaccard Distance between Two Sets]]

### Variants

- [[MinHash Algorithm for ANN Search]]


## Explanation


>[!info]
>Search time complexity
>$$
>O\left( kd + \frac{dn}{2^{k}} \right) \approx O(d \log (n))
>$$
>- $$O(kd)$$ to find region via *projection* on $k$ hyperplanes
>- compare $$O\left( \frac{n}{2^{k}} \right)$$ points in $R$, each takes $d$ operations as inner product on $d$ dimensional space. 

>[!info]
>- **hash table**, which defines indexing that *minimizes the collision*
>- **LSH**, which defines indexing that *maximizes the collision* for nearest neighbors

- [[Hash Table for Efficient Retrieval and Inverse Map]]

### Curse of Dimensionality

- [[Curse of Dimensionality]]




-----------
##  Recommended Notes and References


- [[Similarity Search]]
- [[Principal Component Analysis]]
- [[k-d Tree Structure for ANN Search]]
- [[k Nearest Neighbor Classification]]
- [[k Nearest Neighbor Density Estimation]]

- [[Indexing or Index Construction for Information Retrieval]]
- [[Information Retrieval]]


- Jafari, O., Maurya, P., Nagarkar, P., Islam, K. M., & Crushev, C. (2021). _A Survey on Locality Sensitive Hashing Algorithms and their Applications_ (Databases (Cs.DB) arXiv:2102.08942). arXiv. [https://doi.org/10.48550/arXiv.2102.08942](https://doi.org/10.48550/arXiv.2102.08942)
- Datar, M., Immorlica, N., Indyk, P., & Mirrokni, V. S. (2004, June). Locality-sensitive hashing scheme based on p-stable distributions. In _Proceedings of the twentieth annual symposium on Computational geometry_ (pp. 253-262). [[datarLocalitySensitiveHashingScheme2004]]
- Gionis, A., Indyk, P., & Motwani, R. (1999, September). Similarity search in high dimensions via hashing. In _Vldb_ (Vol. 99, No. 6, pp. 518-529).

- Youtube
	- [Locality Sensitive Hashing (LSH) for Search with Shingling + MinHashing (Python)](https://www.youtube.com/watch?v=e_SBq3s20M8&list=PLIUOU7oqGTLhlWpTz4NnuT3FekouIVlqc&index=5)
	- [kNN.16 Locality sensitive hashing (LSH)](https://www.youtube.com/watch?v=LqcwaW2YE_c)

- Wikipedia [Locality-sensitive_hashing](https://en.wikipedia.org/wiki/Locality-sensitive_hashing)