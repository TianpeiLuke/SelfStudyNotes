---
tags:
  - concept
  - information_retrieval/index
  - information_retrieval/similarity_metric
  - natural_language_processing/sequence_similarity
keywords:
  - w_shingling_similarity
  - n_gram_model
  - shingle_n_gram
topics:
  - information_retrieval/similarity_measure
  - natural_language_processing/sequence_similarity
name: Shingling or n-Gram based Document Similarity Measure
date of note: 2024-11-29
---

## Concept Definition

>[!important]
>**Name**: Shingling or n-Gram based Document Similarity Measure

![[Jaccard Similarity and Jaccard Distance between Two Sets#^584d86]]

>[!important] Definition
>The **$n$-shingling** is a set of *unique shinglings*, each of which is composed of *contiguous subsequence* of $n$ tokens within a document $d$.
>- The symbol $n$ denotes the quantity of tokens in *each shingle selected*, or solved for.
>- Some textbook called it  **$w$-shinglings** or **$k$-shinglings**.
>  
>  
>In particular, let $$(w_{1}\,{,}\ldots{,}\,w_{n})$$ be a **shingle** which is a subsequence of $n$ contiguous tokens in the document $d$.
>- The  **$n$-shingling** of document $d$ is defined as $$S_{n}(d) := \text{unique}\{(w_{1}\,{,}\ldots{,}\,w_{n}) \,{,}\ldots{,}\, (w_{m}\,{,}\ldots{,}\,w_{m+n-1}) \,{,}\ldots{,}\, \}$$ for each $n$-gram $(w_{m}\,{,}\ldots{,}\,w_{m+n-1})$ in $d$.
>- A *n-gram language model* assign a probability for each *unique shingling*, i.e. $$p(w_{1}\,{,}\ldots{,}\,w_{n})$$ 
>
>Then the **$n$-shingling based similiarty** between two documents $d_{1}$ and $d_{2}$ is defined as the *Jaccard similarity* between *$n$-shinglings* of two documents
>$$
>\text{n-shingling}(d_{1}, d_{2}) := \frac{\lvert S_{n}(d_{1}) \cap S_{n}(d_{2}) \rvert }{\lvert S_{n}(d_{1}) \cup S_{n}(d_{2}) \rvert}
>$$

- [[Jaccard Similarity and Jaccard Distance between Two Sets]]
- [[n-Gram Model and Language Model]]
- [[Bag-of-Word Model for Document Representation]]


## Explanation

>[!info]
>The **w-shingling based similarity** is equivalent to a **Jaccard similarity** between two $n$-gram models

## NN Search via Inverted Index

- [[Inverted Index for Information Retrieval]]



-----------
##  Recommended Notes and References


- [[ROUGE metric for LLM Generation]]


- [[Introduction to Information Retrieval by Manning]] pp 438
- [[Handbook of Natural Language Processing by Indurkhya]] pp 293 - 315

- Youtube
	- [3 Traditional Methods for Similarity Search (Jaccard, w-shingling, Levenshtein)](https://www.youtube.com/watch?v=AY62z7HrghY&list=PLIUOU7oqGTLhlWpTz4NnuT3FekouIVlqc&index=1)

- Wikipedia [w-shingling](https://en.wikipedia.org/wiki/W-shingling)