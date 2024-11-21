---
tags:
  - concept
  - natural_language_processing/word_representation
keywords:
  - n_gram_model
  - language_model
topics:
  - natural_language_processing/wording_representation
name: n-Gram Model Estimation Smoothing
date of note: 2024-09-08
---

## Concept Definition

>[!important]
>**Name**: n-Gram Model Estimation Smoothing

![[n-Gram Model and Language Model#^81ad19]]

![[n-Gram Model and Language Model#^2256aa]]

- [[n-Gram Model and Language Model]]

>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary* and $N$ be total number of $n$-gram tokens.
>
>The *maximum likelihood estimation* with **Laplace smoothing** of **bi-gram model** is given by 
>$$
>\widehat{p}(w_{n} \,|\,w_{n-1}) = \frac{C(w_{n-1},\,w_{n}) + 1}{C(w_{n-1}) + |\mathcal{V}|} = \frac{C(w_{n-1},\,w_{n}) + 1}{\sum_{w\in \mathcal{V}}(C(w_{n-1},\,w) + 1)} 
>$$
>where $C(w_{n-1},\,w_{n})$ is the *count of occurrance* of *bigram* $w_{n-1},w_{n}$.
>- This ratio is given by the **Bayesian estimation** given **Laplace prior.**

^c8317a

- [[Laplace Distribution]]


## Explanation





-----------
##  Recommended Notes and References


- [[Bag-of-Words for Text Representation]]
- [[Word Embedding]]
- [[Naive Bayes Model]]
- [[Multinomial Naive Bayes Model]]
- [[Multinomial Principle Component Analysis]]
- [[Probabilistic Latent Semantic Analysis]]
- [[Latent Dirichlet Allocation]]


- [[Foundations of Statistical Natural Language Processing by Manning]] pp 191
- [[Speech and Language Processing by Jurafsky]] pp 45 - 49