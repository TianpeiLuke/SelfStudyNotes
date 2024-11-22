---
tags:
  - concept
  - natural_language_processing
  - information_retrieval/relevancy_metric
  - information_retrieval/index
keywords:
  - tf_idf_representation
  - okapi_bm25_score
topics:
  - information_retrieval/index
  - natural_language_processing/word_representation
name: Okapi BM25 score for Information Retrieval
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Okapi BM25 score for Information Retrieval

![[Co-Occurrence Matrix#^253cfb]]

- [[Co-Occurrence Matrix]]

>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary set* and $\mathcal{D}$ be the set of *documents*, where each document $d\in \mathcal{D}$ consists of a sequence of words/tokens $$d := (w_{1}^{d} \,{,}\ldots{,}\,w_{n_{d}}^{d}) \in \mathcal{D} \subset \mathcal{V}^{*}$$
>
>Denote the *term-document matrix* as $$X = [x_{i,d}] \in \mathbb{R}^{|\mathcal{V}| \times |\mathcal{D}|}$$ where each entity counts the *occurrence* of given term $t_{i}$ in document $d$  $$x_{i,d} = x(t_{i}, d) = \sum_{j=1}^{n_{d}}\mathbb{1}\left\{ w_{j}^{d} = t_{i} \right\}$$
>
>Let $Q$ be a *query* with $k$ *keywords* $q_{1}\,{,}\ldots{,}\,q_{k}$.
>
>The **BM25 sore** of a *document* $d\in \mathcal{D}$ is given by 
>$$
>\begin{align*}
>\text{BM25}(Q, d) &= \sum_{j=1}^{k}\text{idf}_{j} \cdot \frac{(k_{1} + 1)\,\text{tf}_{j,d}}{k_{1}\,\left( 1 - b + b\, \dfrac{n_{d}}{\mu_{\mathcal{D}}} \right) + \text{tf}_{j,d} } \\[8pt]
>&= \sum_{j=1}^{k}\log_{10}\left( \frac{|\mathcal{D}|}{\text{df}_{j}} \right) \cdot \frac{x(q_{j}, d)\,(k_{1} + 1)}{x(q_{j}, d) + k_{1}\,\left( 1 - b + b\, \dfrac{n_{d}}{\mu_{\mathcal{D}}} \right)}
>\end{align*}
>$$
>where
>- $n_{d}$ is the *number of tokens* in given document $d$.
>- $\mu_{\mathcal{D}}$ denotes the average document length, i.e. $$\mu_{\mathcal{D}} = \frac{1}{|\mathcal{D}|}\sum_{d \in \mathcal{D}}n_{d}$$
>- $\text{idf}(q_{k})$ is the *inverse document frequency* for the keyword. $$\text{idf}_{j} := \text{idf}(q_{j}) = \log_{10}\left( \frac{|\mathcal{D}|}{\text{df}_{j}} \right)  = \log_{10}\left( \frac{|\mathcal{D}|}{\sum_{d\in \mathcal{D}}x(q_{j}, d)} \right)$$

- [[Term Frequency and Inverse Document Frequency or TF-IDF]]



## Explanation

>[!info]
>- **tf-idf score** $$\text{tf-idf}(Q, d) := \sum_{j=1}^{k}\text{idf}_{j} \times \text{tf}_{j,d}$$
>- **BM25 score** $$\text{BM25}(Q, d) := \sum_{j=1}^{k}\text{idf}_{j} \times \frac{(k_{1} + 1)\,\text{tf}_{j,d}}{k_{1}\left(1 - b + b\,\dfrac{n_{d}}{\mu_{\mathcal{D}}}\right) + \text{tf}_{j,d}}$$

>[!info]
> "BM" means the *Best Match.*





-----------
##  Recommended Notes and References



- [[Vector Space Model in Information Retrieval]]
- [[Matrix]]
- [[Topic Models]]


- [[Introduction to Information Retrieval by Manning]] pp 232
- [[Speech and Language Processing by Jurafsky]] pp 111 - 114