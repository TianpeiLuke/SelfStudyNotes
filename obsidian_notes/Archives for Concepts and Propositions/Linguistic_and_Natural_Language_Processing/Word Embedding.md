---
tags:
  - concept
  - natural_language_processing
  - natural_language_processing/word_representation
keywords:
  - word_embedding
topics:
  - natural_language_processing/word_representation
name: Word Embedding
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Word Embedding

![[Vector Semantics and Distributional Hypothesis in Linguistic#^849498]]

![[Vector Semantics and Distributional Hypothesis in Linguistic#^be40ca]]

- [[Vector Semantics and Distributional Hypothesis in Linguistic]]

>[!important] Definition
>A **word embedding** is a *vector representation* of word so that the *semantic similar word* would map to a neighborhood in *Euclidean space*.
>$$
>w_{1} \text{ is semantically }\sim w_{2} \implies E(w_{1}) \in B(E(w_{2}), \delta)
>$$
>
>Two main properties for *word embedding*
>- the embedding vectors are **short vectors**, i.e. they are of *smaller dimensionality* than the vocabulary size. $$p \ll |\mathcal{V}|$$
>- the embedding vectors are **dense vectors**

- [[Word Embedding Semantic Properties]]

### Sparse Word Embedding

- [[Co-Occurrence Matrix]]
- [[Term Frequency and Inverse Document Frequency or TF-IDF]]

### Static Word Embedding


- [[Probabilistic Latent Semantic Analysis]]
- [[Word2Vec Algorithm for Static Word Embedding]]
- [[Skip-Gram Algorithm with Negative Sampling for Word Embedding]]
- [[Contiuous-Bag-of-Words Algorithm for Word Embedding]]


### Contextual Word Embedding

- [[Self-Supervised Learning]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]


## Explanation





-----------
##  Recommended Notes and References






- [[Word Embedding Evaluation and Datasets]]


- [[Speech and Language Processing by Jurafsky]] 