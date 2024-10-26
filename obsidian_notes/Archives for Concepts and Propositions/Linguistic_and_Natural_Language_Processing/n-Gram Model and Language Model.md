---
tags:
  - concept
  - natural_language_processing/word_representation
keywords:
  - n_gram_model
  - language_model
topics:
  - natural_language_processing/wording_representation
name: n-Gram Model and Language Model
date of note: 2024-09-08
---

## Concept Definition

>[!important]
>**Name**: n-Gram Model and Language Model

>[!important] Definition
>Consider the task of *predicting* the probability of *next word* given the occurrence of a sequence of words in a sentence: $$p(w_{n} \,|\,w_{n-1}\,{,}\ldots{,}\,w_{1})$$ 
>where $w_{i}$ is referred as **words** or **tokens**.
>
>A **language model (LM)** is a model that assign a *probability* to a sequence of words $$p(w_{1}\,{,}\ldots{,}\,w_{n})$$

>[!important] Definition
>A **n-gram model** is a *language model* for a sequence of $n$-words. $$p(w_{1}\,{,}\ldots{,}\,w_{n})$$
>- For $n=2$, it is referred to as the **bi-gram model**, which assigns probability for every two successive words $$p(w_{i}, w_{i+1})$$
>- For $n=3$, it is referred to as the **tri-gram model**, which assigns probability for every three-word sequence $$p(w_{i}. w_{i+1}, w_{i+2})$$
>- We also use the **n-gram model** to estimate the probability of a given word, given *previous $n-1$ words* $$p(w_{n} \,|\,w_{n-1}\,{,}\ldots{,}\,w_{1})$$ 

### Estimation of Joint Probability



- [[Multinomial Distribution]]



## Explanation





-----------
##  Recommended Notes and References


- [[Word Embedding]]
- [[Naive Bayes Model]]
- [[Multinomial Naive Bayes Model]]
- [[Multinomial Principle Component Analysis]]
- [[Probabilistic Latent Semantic Analysis]]
- [[Latent Dirichlet Allocation]]

- Daniel Jurafsky and James H. Martin. 2024. *Speech and Language Processing: An Introduction to Natural Language Processing, Computational Linguistics, and Speech Recognition with Language Models*, 3rd edition
- [[Foundations of Statistical Natural Language Processing by Manning]] pp 191