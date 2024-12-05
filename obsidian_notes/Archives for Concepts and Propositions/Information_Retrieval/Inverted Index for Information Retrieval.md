---
tags:
  - concept
  - information_retrieval/index
keywords:
  - inverted_index_retrieval
  - inverted_file
topics:
  - information_retrieval/index
name: Inverted Index for Information Retrieval
date of note: 2024-11-29
---

## Concept Definition

>[!important]
>**Name**: Inverted Index for Information Retrieval

![[Co-Occurrence Matrix#^253cfb]]

>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary set* and $\mathcal{D}$ be the set of *documents*, where each document $d\in \mathcal{D}$ consists of a sequence of words/tokens $$d := (w_{1}^{d} \,{,}\ldots{,}\,w_{n_{d}}^{d}) \in \mathcal{D} \subset \mathcal{V}^{*}$$
>
>Consider a *term-document matrix* $$X := [x(i,d)]\in \mathbb{R}^{|\mathcal{V}|\times |\mathcal{D}|}$$
>- This matrix is a *sparse matrix* since each document has much less terms than the vocabulary.
>- The *non-zero entries* in *each row* represents which document that contains the given term. $$m \to  \{ d_{i_{1}} \,{,}\ldots{,}\, d_{i_{K}}\}, \quad x(m, d_{i_{j}}) > 0 $$
>  
>The **inverted index**, or **inverted file**  consists of two parts:
>- a **dictionary** of *terms* or **vocabulary** or **lexicon** $\mathcal{V}$
>- and for each term $m\in \mathcal{V}$, a *list of indices* for documents that contains the given term, $$m \to  ( d_{i_{k}}\in \mathcal{D}:\, x(m, d_{i_{k}}) > 0,\, i_{k}\in [|\mathcal{D}|])$$ 
>	- Each item in the list, which records that a term appeared in a document, is called a **posting** 
>	- Such list is called a **posting list** or **inverted list.**
>	- All *posting lists* taken together are referred to as the **postings.**

- [[Co-Occurrence Matrix]]
- [[Term Frequency and Inverse Document Frequency or TF-IDF]]


![[inverted_index.png]]

>[!important] Definition
>For each document in $\mathcal{D}$, we assume that it has a *unique serial number*, called the **document identifier (docID)**
>- During the *index construction*, we can simply assign successive integers to each new document.
>- The *term-document matrix* consists of pairs of *term* and *docID*
>

- [[Indexing or Index Construction for Information Retrieval]]

>[!important]
>For a new sample, we **merge inverted lists** for attributes present in new example


## Explanation

>[!info]
>For $|\mathcal{V}|= d$ and $|\mathcal{D}| = n$, the average complexity is about $$O(d\,\sqrt{n})$$


>[!info]
>The **inverted index** is just the *adjacency list representation* of **sparse co-occurrence matrix**.

- [[Sparse Matrix Representation]]
- [[Adjacency Matrix of Graph]]

>[!info]
>**indexing** is an *inverse map*:
>- An **index** maps back from *terms* to the *parts of a document* where they *occur*.

- [[Hash Table for Efficient Retrieval and Inverse Map]]

## Similarity Search via Inverted Index
### Exact Nearest Neighbor Search

>[!important] 
>The **inverted index** can be used to search *$k$ nearest neighbor* for a query $q$.
>
>Let $q:= (q^1 \,{,}\ldots{,}\,q^{m})$ be $m$ terms in the query.
>
>The **nearest neighbor** $d\in \mathcal{D}$ to $q$ in terms of *Jaccard distance* with respect to *Shingling* is defined as $$J(d, q) := \frac{|\left\{ w^{i}: w^{i}\in q \land w^{i} \in d \right\}|}{|\left\{ w^{i}: w^{i}\in q \lor w^{i} \in d \right\}|}$$
>
>The **nearest neighbor search** via *Shingling-based Jaccard distance* can be done by *merging inverted lists*
>- $\left\{ w^{i}: w^{i}\in q \land w^{i} \in d \right\}$ is a set of *posting lists* that have *both* $q$ and $d$ as items
>- $\left\{ w^{i}: w^{i}\in q \lor w^{i} \in d \right\}$  is a set of *posting lists* that have *either* $q$ or $d$ as items
>  

^e1bebe


- [[Similarity Search]]
- [[Jaccard Similarity and Jaccard Distance between Two Sets]]
- [[Shingling or n-Gram based Document Similarity Measure]]

### Approximate Nearest Neighbor Search

![[Inverted File Index for ANN Search#^8d02f1]]

- [[Inverted File Index for ANN Search]]
- [[Hash Table for Efficient Retrieval and Inverse Map]]

![[inverted_file_index_knn.png]]


## IVF + PQ Indexing System

- [[Product Quantization for ANN Search and Index Compression]]



-----------
##  Recommended Notes and References


- Youtube
	- [kNN.17 Inverted index](https://www.youtube.com/watch?v=Mlp8hlKwETs)

- Medium
	- [Similarity Search, Part 1: kNN & Inverted File Index](https://towardsdatascience.com/similarity-search-knn-inverted-file-index-7cab80cc0e79)

- [[Introduction to Information Retrieval by Manning]] pp 6