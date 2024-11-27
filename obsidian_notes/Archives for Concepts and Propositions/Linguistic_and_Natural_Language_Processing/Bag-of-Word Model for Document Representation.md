---
tags:
  - concept
  - natural_language_processing/word_representation
keywords:
  - bag_of_words
topics:
  - natural_language_processing/word_representation
name: Bag-of-Word Model for Document Representation
date of note: 2024-09-12
---

## Concept Definition

>[!important]
>**Name**: Bag-of-Word Model for Document Representation

![[Co-Occurrence Matrix#^253cfb]]

>[!important] Definition
>The **bag-of-word (BOW) model** represents a text document $d\in \mathcal{D}$ as an *unordered set of words* with their *position ignored*, keeping only their *frequency*
>$$
>d \to (t_{1}\,{,}\ldots{,}\,t_{K})
>$$
>where $t_{i}\in \mathcal{V}$.
>
>That is, the **BOW model** represents a *document* $d\in \mathcal{D}$ via the corresponding *column vector* in *co-occurrence matrix* $X\in \mathbb{R}^{|\mathcal{V}|\times |\mathcal{D}|}$
>$$
>d \to X[:,d]
>$$

- [[Co-Occurrence Matrix]]

![[Multinomial Naive Bayes Model#^3fc7af]]


![[bag_of_word_document.png]]

- [[n-Gram Model and Language Model]]

### Multinomial Naive Bayes

>[!important] Definition
>The *probabilistic model* that corresponds to the **bag-of-word representation** is the **multinomial Naive Bayes model.**

![[Multinomial Naive Bayes Model#^b4ddab]]

- [[Multinomial Naive Bayes Model]]

## Explanation

>[!iinfo]
>The **bag-of-words (BOW)** representation is the simplest document representation via **vector space model.**

- [[Vector Space Model in Information Retrieval]]



-----------
##  Recommended Notes and References



- [[Word Embedding]]

- [[Cosine Similarity and Cosine Distance]]


- [[Probabilistic Latent Semantic Analysis]]
- [[Latent Dirichlet Allocation]]

- [[Vector Space over a Field]]


- Wikipedia [Bag-of-words_model](https://en.wikipedia.org/wiki/Bag-of-words_model)
- [[Speech and Language Processing by Jurafsky]]  pp 58
- [[Probabilistic Graphical Models by Koller]] pp 766
- [[Deep Learning Foundations and Concepts by Bishop]] pp 378
- [[Practical Natural Language Processing by Vajjala]] pp 87 - 89