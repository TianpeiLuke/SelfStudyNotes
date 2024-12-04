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

## Explanation

>[!info]
>The **inverted index** is just the *adjacency list representation* of **sparse co-occurrence matrix**.

- [[Sparse Matrix Representation]]
- [[Adjacency Matrix of Graph]]

>[!info]
>**indexing** is an *inverse map*:
>- An **index** maps back from *terms* to the *parts of a document* where they *occur*.

- [[Hash Table for Efficient Retrieval and Inverse Map]]


-----------
##  Recommended Notes and References


- [[Introduction to Information Retrieval by Manning]] pp 6