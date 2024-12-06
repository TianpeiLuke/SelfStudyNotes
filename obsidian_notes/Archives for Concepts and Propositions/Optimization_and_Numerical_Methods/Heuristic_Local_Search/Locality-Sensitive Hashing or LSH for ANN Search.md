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

![[epsilon Isometry#^575618]]

>[!important] Definition
>The **locality-sensitive hashing (LSH)** finds the nearest neighbor in *high dimensional space* by *projecting* them into *low-dimensional space* using **hash functions**.
>- In particular, the hash function of **LSH** *preserves* the *neighborhood* of original space. 
>- That is, a **LSH hash function** $H: \mathcal{D}\to \mathbb{R}^{d}$ maps *similar documents* with *similar hash codes*.
>$$\lVert x_{1} - x_{2} \rVert < \delta  \implies d(H(x_{1}), H(x_{2})) < \epsilon$$
>- It achieves *approximate nearest neighbor (ANN) search* by comparing only documents with similar hash codes. $$x^{*} = \arg\min_{H(x) = H(q)}\,d(x, q)$$

- [[epsilon Isometry]]
- [[Approximate Nearest Neighbor Search]]
- [[Hash Table for Efficient Retrieval and Inverse Map]]


![[lsh_process.png]]

### Property of LSH Hash Functions

>[!important] Definition
>Let $x, y\in \mathcal{D} \subset \mathbb{R}^{d}$. 
>
>We say that a *hash function* $H$ is **($R$, $cR$, $p_{1}$, $p_{2}$)-sensitive** if it satisfies the following two conditions
>- if $\lVert x - y \rVert\le R$, then $$\mathcal{P}\{ H(x) = H(y) \} \ge p_{1},$$
>- if $\lVert x - y \rVert > cR$, then $$\mathcal{P}\{ H(x) = H(y) \} \le p_{2},$$
>  
>Note that $c > 1$ and $p_{1} > p_{2}$.  

### Example of LSH Techniques

#### Hamming-based LSH Techniques


- [[Weighted Hamming Distance]]
- [[MinHash Algorithm for ANN Search]]

#### Minkowski-based LSH Techniques


#### Angular-based LSH Techniques


#### Jaccard-based LSH Techniques

- [[Shingling or n-Gram based Document Similarity Measure]]
- [[Jaccard Similarity and Jaccard Distance between Two Sets]]


### Kernel-based LSH Techniques



- [[Positive Definite Kernel]]
- [[Positive Definite Kernel Examples]]
- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]

## Explanation

>[!important]
>The idea of **LSH**
>- $k$ *random hyperplanes* split the space into $2^k$ regions $$v \to \text{sgn}(Pv)$$  
>- compare *only* with points in the *same region*
>  
>
>- It assumes that **similar document** has **similar hash code**


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



## False Positive Rate of LSH




- [[Gaussian Random Projections]]
- [[Johnson-Lindenstrauss Lemma for Dimensionality Reduction]]




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
	- [IndexLSH for Fast Similarity Search in Faiss](https://www.youtube.com/watch?v=ZLfdQq_u7Eo)
	- [LSH.1 Exact duplicates and near-duplicates](https://www.youtube.com/watch?v=356GoYkmYKg)
	- [LSH.2 Duplicate detection: naive approach](https://www.youtube.com/watch?v=4h_cUtXQpzI)
	- [LSH.3 Detecting duplicates by hashing](https://www.youtube.com/watch?v=hIBN1fMBHzQ)
	- [LSH.4 Adler32 hashcode](https://www.youtube.com/watch?v=BWqH4O7OuyY)
	- [LSH.5 Clarification](https://www.youtube.com/watch?v=fRuIU5aqa-M)
	- [LSH.6 Error rates for exact duplicate detection](https://www.youtube.com/watch?v=zxF-3yZPGzU)
	- [LSH.7 Properties of conventional hashcodes](https://www.youtube.com/watch?v=4DEAWbwOiKI)
	- [LSH.8 Locality-sensitive hashing: the idea](https://www.youtube.com/watch?v=dgH0NP8Qxa8)
	- [LSH.9 Locality-sensitive hashing: how it works](https://www.youtube.com/watch?v=Arni-zkqMBA)
	- [LSH.10 False positive and negative errors of LSH](https://www.youtube.com/watch?v=h21irtHDsBw)
	- [LSH.11 Hash-code length and number of hashtables](https://www.youtube.com/watch?v=pPPFlT9Wg-s)
	- [LSH.12 Simhash algorithm](https://www.youtube.com/watch?v=gnraT4N43qo)
	- [LSH.13 Clarification](https://www.youtube.com/watch?v=dEqinx_Ohy8)

- Wikipedia [Locality-sensitive_hashing](https://en.wikipedia.org/wiki/Locality-sensitive_hashing)