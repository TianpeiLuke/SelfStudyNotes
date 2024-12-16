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
>- We can use the *chain rule of probability* to compute the joint probability as $$p(w_{1}\,{,}\ldots{,}\,w_{n}) = \prod_{k=1}^{n}p(w_{k}\;|\;w_{k-1}\,{,}\ldots{,}\,w_{1})$$ This is the **autoregressive language model.**
>- For autoregressive language model, we only need to model the conditional probability $$p(w_{k}\;|\;w_{k-1}\,{,}\ldots{,}\,w_{1}).$$
>

^b7a2b4

- [[Autoregressive Models]]

>[!important] Definition
>The task of language model is to estimate $$p(w_{k} \,|\,w_{k-1}\,{,}\ldots{,}\,w_{1})$$ 
>
>A **n-gram model** is a *language model* that is based on the *Markov assumption* i.e. $$p(w_{k} \,|\,w_{k-1}\,{,}\ldots{,}\,w_{1}) \approx p(w_{k} \,|\,w_{k-1}\,{,}\ldots{,}\,w_{k-n+1})$$ for some $n$
>- That is, it assumes that a history of *previous $n-1$ words* would be *sufficient* to *predict* the current word.
>- For $n=1$, it is referred to as the **uni-gram model**, which assumes that all words are *independent*, and estimate $$p(w_{k})$$
>- For $n=2$, it is referred to as the **bi-gram model**, which estimate the conditional probability for a word given its immediate successive word $$p(w_{k} | w_{k-1})$$
>- For $n=3$, it is referred to as the **tri-gram model**, which assigns probability for every three-word sequence and estimate the conditional distribution based on previous two words $$p(w_{k} | w_{k-1}, w_{k-2})$$


^81ad19

- [[Markov Chain and Markov Process]]
- [[Dynamic Bayesian Network]]
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

>[!example]
>The most common MLE of n-gram is for **bi-gram**
>$$
>\widehat{p}(w_{n} \,|\,w_{n-1}) = \frac{C(w_{n-1},\,w_{n})}{C(w_{n-1})} = \frac{C(w_{n-1},\,w_{n})}{\sum_{w}\,C(w_{n-1},\,w)}
>$$
>and **tri-gram**
>$$
>\widehat{p}(w_{n} \,|\,w_{n-1},\, w_{n-2}) = \frac{C(w_{n-2},\,w_{n-1},\,w_{n})}{C(w_{n-2},\,w_{n-1})}
>$$


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

## Similarity Measure based on n-Gram

- [[Shingling or n-Gram based Document Similarity Measure]]


## Evaluation of Language Model

- [[Perplexity Measure for Language Models]]
- [[ROUGE metric for LLM Generation]]
- [[Bilingual Evaluation Understudy or BLEU metric for LLM Generation]]


## Bag-of-Words and Multinomial Naive Bayes 

- [[Bag-of-Word Model for Document Representation]]
- [[Multinomial Naive Bayes Model]]




-----------
##  Recommended Notes and References


- [[Bag-of-Word Model for Document Representation]]
- [[Word Embedding]]
- [[Naive Bayes Model]]
- [[Multinomial Naive Bayes Model]]
- [[Multinomial Principle Component Analysis]]
- [[Probabilistic Latent Semantic Analysis]]
- [[Latent Dirichlet Allocation]]

- [[Alphabets and Strings Abstract Definition]]

- [[Foundations of Statistical Natural Language Processing by Manning]] pp 191
- [[Speech and Language Processing by Jurafsky]] pp 33 - 38, 45
- [[Deep Learning Foundations and Concepts by Bishop]] pp 379
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 49
- [[Artificial Intelligence Modern Approach by Russell]] pp 862