---
tags:
  - concept
  - natural_language_processing/word_representation
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
keywords:
  - contextual_embedding_nlp
topics:
  - natural_language_processing/word_representation
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
name: Contextual Embeddings and Word Sense
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Contextual Embeddings and Word Sense

![[Vector Semantics and Distributional Hypothesis in Linguistic#^c91885]]


>[!important] Definition
>The **contextual word embedding** is a class of representations of word meaning based on integrating the meaning of the helpful contextual words. 
>- The *contextual word embedding* is **context-dependent**, i.e. changing the context of the word would result in the change of *word embedding*. 
>- That is, for token $t_{i}\in \mathcal{V}$, its representation depends on the *entire input sequence* $$h(t_{i}) = f(E(w_{1})\,{,}\ldots{,}\,E(w_{n}))$$

- [[Word Embedding]]
- [[Word Embedding Semantic Properties]]
- [[Vector Semantics and Distributional Hypothesis in Linguistic]]

>[!important] Definition
>The **contextual word embedding** can address *word sense disambiguation* for *polysemous words* by referring to their contexts.
>- The representation of a word which has a particular *sense* in a *context* is closer to other instances of the *same sense* of the word.

- [[Word Sense and WordNet]]

## Explanation

>[!info]
>The **global representation** of word learns *one embedding* for each word in the vocabulary, *regardless* of context around it.
>
>The **contextual embedding** provides *different representation* of word based on *different context*.

- [[Word2Vec Algorithm for Static Word Embedding]]
- [[Contiuous-Bag-of-Words Algorithm for Word Embedding]]
- [[Skip-Gram Algorithm with Negative Sampling for Word Embedding]]

>[!quote]
>**Distributional word representations** (Turian et al., 2010; Mikolov et al., 2013; Pennington et al., 2014) trained in an unsupervised manner on large-scale corpora are widely used in modern natural language processing systems. 
>- However, these approaches only obtain a **single global representation** for each word, ignoring their context. 
>
>Different from traditional word representations, **contextual embeddings** move beyond word-level semantics in that each token is associated with a representation that is a function of the entire input sequence. 
>- These **context-dependent representations** can capture many syntactic and semantic properties of words under diverse linguistic contexts.
>  
>  
>-- Liu, Q., Kusner, M. J., & Blunsom, P. (2020). A survey on contextual embeddings. _arXiv preprint arXiv:2003.07278_.  

- [[Vector Semantics and Distributional Hypothesis in Linguistic]]



-----------
##  Recommended Notes and References








- [[Speech and Language Processing by Jurafsky]] pp 186, 231
- Liu, Q., Kusner, M. J., & Blunsom, P. (2020). A survey on contextual embeddings. _arXiv preprint arXiv:2003.07278_.