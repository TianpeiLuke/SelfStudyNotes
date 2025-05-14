---
tags:
  - concept
  - natural_language_processing/word_representation
  - information_retrieval/vector_space_model
keywords:
  - vector_space_model_ir
topics:
  - information_retrieval/vector_space_models
  - natural_language_processing/word_representation
name: Vector Space Model for Text Representation
date of note: 2024-09-12
---

## Concept Definition

>[!important]
>**Name**: Vector Space Model for Text Representation

![[Co-Occurrence Matrix#^253cfb]]



>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary set* and $\mathcal{D}$ be the set of *documents*, where each document $d\in \mathcal{D}$ consists of a sequence of words/tokens $$d := (w_{1}^{d} \,{,}\ldots{,}\,w_{n_{d}}^{d}) \in \mathcal{D} \subset \mathcal{V}^{*}$$
>
>The **vector space model** defines a *vector space of documents* $V \subset \mathbb{R}^{p}$, where each document is represented by a vector $$d\in \mathcal{D} \implies d \in \mathbb{R}^{p}$$  
>- the dimension $p$ is called the **word dimension.**

- [[Information Retrieval]]

### Examples

>[!example]
>In **term-document matrix**, each document is represented by the *count of occurrence of words* in $\mathcal{V}$. $$d\in \mathbb{N}^{|\mathcal{V}|}$$

- [[Co-Occurrence Matrix]]

>[!example]
>For **bag-of-words representation**, each document is represented by the *count of occurrence of word groups* $$d\in \mathbb{N}^{p}$$

- [[Bag-of-Word Model for Document Representation]]

>[!example]
>The **tf-idf vector space model** represents each document $d\in \mathcal{D}$ as the *centroid* of *tf-idf* representation for all words in the document
>$$
>d := \frac{1}{n_{d}}\sum_{i=1}^{n_{d}}w_{i}^{d}
>$$
>where $w_{i}^{d}$ is given by the *row vector* of *term-document matrix* weighted by *tf-idf*.
>$$w_{i}^{d} = \mathbb{1}\left\{ w_{i}^{d} = w_{k} \right\}\; \text{tf-idf}(X_{k,:})$$

- [[Term Frequency and Inverse Document Frequency or TF-IDF]]

>[!example]
>The **pointwise mutual information vector space model** represents each document $d\in \mathcal{D}$ as the *centroid* of *pointwise mutual information* representation for all words in the document
>$$
>d := \frac{1}{n_{d}}\sum_{i=1}^{n_{d}}w_{i}^{d}
>$$

- [[Pointwise Mutual Information]]

>[!example]
>The **word2vec vector space model** represents each document $d\in \mathcal{D}$ as the *centroid* of *word2vec* representation for all words in the document
>$$
>d := \frac{1}{n_{d}}\sum_{i=1}^{n_{d}}w_{i}^{d}
>$$
>where $w_{i}^{d}$ is given by the *word2vec embedding*
>$$w_{i}^{d} = \mathbb{1}\left\{ w_{i}^{d} = w_{k} \right\}\; \text{word2vec}(w_{k})$$




### Cosine Similarity

![[Cosine Similarity and Cosine Distance#^ad349d]]

- [[Cosine Similarity and Cosine Distance]]

>[!important] Definition
>In the **vector space model** of documents $V \subset \mathbb{R}^{p}$, the *similarity* between documents can be measured via the **cosine similarity** $$S_{c}(d_{1}, d_{2}) := \frac{\left\langle d_{1} , d_{2} \right\rangle_{V}}{\lVert d_{1} \rVert\, \lVert d_{2} \rVert  }$$



### Word Embeddings

- [[Word Embedding]]
- [[Word2Vec Algorithm for Static Word Embedding]]


## Explanation





-----------
##  Recommended Notes and References


- [[Bag-of-Word Model for Document Representation]]

- [[n-Gram Model and Language Model]]
- [[Cosine Similarity and Cosine Distance]]


- [[Probabilistic Latent Semantic Analysis or pLSA]]
- [[Latent Dirichlet Allocation or LDA]]

- [[Vector Space over a Field]]

- Wikipedia [Vector_space_model](https://en.wikipedia.org/wiki/Vector_space_model)
- [[Speech and Language Processing by Jurafsky]] pp 107
- [[Introduction to Information Retrieval by Manning]] pp 120 - 124
- [[Foundations of Statistical Natural Language Processing by Manning]] pp 539 - 544
- [[Practical Natural Language Processing by Vajjala]] pp 84