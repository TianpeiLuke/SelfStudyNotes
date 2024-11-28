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

![[Vector Semantics and Distributional Hypothesis in Linguistic#^c91885]]

- [[Vector Semantics and Distributional Hypothesis in Linguistic]]

>[!important] Definition
>A **word embedding** is a *vector representation* of word so that the *semantic similar word* would map to a neighborhood in *Euclidean space*.
>$$
>w_{1} \text{ is semantically }\sim w_{2} \implies E(w_{1}) \in B(E(w_{2}), \delta)
>$$
>- A **word embedding** is a map from **distributional representation space** to **distributed representation space.**
>
>Two main properties for *word embedding*
>- the embedding vectors are **short vectors**, i.e. they are of *smaller dimensionality* than the vocabulary size. $$p \ll |\mathcal{V}|$$
>- the embedding vectors are **dense vectors**
>

- [[Word Embedding Semantic Properties]]
- [[Distributed Representation]]
- [[Vector Semantics and Distributional Hypothesis in Linguistic]]


### Sparse Word Embedding

- [[Co-Occurrence Matrix]]
- [[Bag-of-Word Model for Document Representation]]
- [[Bag-of-Word Model for Document Representation]]
- [[Term Frequency and Inverse Document Frequency or TF-IDF]]

### Static Global Word Embedding

- [[Latent Semantic Analysis via Singular Value Decomposition]]
- [[Probabilistic Latent Semantic Analysis]]
- [[Word2Vec Algorithm for Static Word Embedding]]
- [[Noise Contrastive Estimation]]
- [[Skip-Gram Algorithm with Negative Sampling for Word Embedding]]
- [[Contiuous-Bag-of-Words Algorithm for Word Embedding]]


### Contextual Word Embedding

- [[Contextual Embeddings and Word Sense]]
- [[Self-Supervised Learning]]
- [[Representation Learning]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Information Noise Contrastive Estimation as Contrastive Learning]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]


## Explanation





-----------
##  Recommended Notes and References



- Liu, Q., Kusner, M. J., & Blunsom, P. (2020). A survey on contextual embeddings. _arXiv preprint arXiv:2003.07278_.



- [[Word Embedding Evaluation and Datasets]]


- [[Practical Natural Language Processing by Vajjala]] pp 81 - 113
- [[Practical Natural Language Processing by Vajjala]] pp 81 - 113
- [[Speech and Language Processing by Jurafsky]] 