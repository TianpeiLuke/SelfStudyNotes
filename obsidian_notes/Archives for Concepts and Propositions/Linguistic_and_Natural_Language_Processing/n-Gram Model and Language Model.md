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

^b7a2b4

>[!important] Definition
>A **n-gram model** is a *language model* for a sequence of $n$-words. $$p(w_{1}\,{,}\ldots{,}\,w_{n})$$
>- For $n=2$, it is referred to as the **bi-gram model**, which assigns probability for every two successive words $$p(w_{i}, w_{i+1})$$
>- For $n=3$, it is referred to as the **tri-gram model**, which assigns probability for every three-word sequence $$p(w_{i}. w_{i+1}, w_{i+2})$$
>- We also use the **n-gram model** to estimate the probability of a given word, given *previous $n-1$ words* $$p(w_{n} \,|\,w_{n-1}\,{,}\ldots{,}\,w_{1}) = \frac{p(w_{n},\,w_{n-1}\,{,}\ldots{,}\,w_{1})}{p(w_{n-1}\,{,}\ldots{,}\,w_{1})}$$ 

^81ad19

- [[Autoregressive Models]]
- [[Tokenization of Words and Subwords and SentencePiece Tokenization]]


### Maximum Likelihood Estimation of Joint Probability

>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary*. 
>
>The **maximum likelihood estimation** of **n-gram model** is given by 
>$$
>\widehat{p}(w_{n} \,|\,w_{n-1}\,{,}\ldots{,}\,w_{1}) = \frac{C(w_{1}\,{,}\ldots{,}\,w_{n-1},\,w_{n})}{C(w_{1}\,{,}\ldots{,}\,w_{n-1})}
>$$
>where $C(w_{1}\,{,}\ldots{,}\,w_{n-1},\,w_{n})$ is the *count of occurrance* of *$n$-gram* $w_{1}\,{,}\ldots{,}\,w_{n}$.
>- This ratio is called a **relative frequency**, which is given by dividing the observed frequency of a particular *sequence* by the observed frequency of a *prefix*.  

^2256aa

- [[Maximum Likelihood Estimation]]

### Smoothing and Discount

![[n-Gram Model Estimation Smoothing#^c8317a]]

- [[n-Gram Model Estimation Smoothing]]


## Explanation

>[!info]
>In $n$-gram, we assume that each $n$-gram sequence is selected independently from a **multinomial distribution**
>$$
>(W_{1}\,{,}\ldots{,}\,W_{n}) \in \mathcal{V}^{n} \sim Multinomial(n; p_{1} \,{,}\ldots{,}\, p_{k})
>$$
>where $n$ is the number of *total counts* of $n$-gram in corpus, and $p_{i}$ are the probability of given assignment 

- [[Multinomial Distribution]]

## Evaluation of Language Model

- [[Perplexity]]



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
- [[Speech and Language Processing by Jurafsky]] pp 33 - 38, 45