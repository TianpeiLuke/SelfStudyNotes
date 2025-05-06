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

### Add $k$ Smoothing

>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary* and $N$ be total number of $n$-gram tokens.
>
>The **add-k smoothing** of **bi-gram model** is given by 
>$$
>\widehat{p}(w_{n} \,|\,w_{n-1}) = \frac{C(w_{n-1},\,w_{n}) + k}{C(w_{n-1}) + k|\mathcal{V}|} = \frac{C(w_{n-1},\,w_{n}) + k}{\sum_{w\in \mathcal{V}}(C(w_{n-1},\,w) + k)} 
>$$
>where 
>- $C(w_{n-1},\,w_{n})$ is the *count of occurrance* of *bigram* $w_{n-1},w_{n}$.
>- $k\in (0,1]$. We can choose $k$ with *cross-validation* or *hold-out.* 



## Explanation

>[!quote]
>There is a problem with using *maximum likelihood estimates* for probabilities: any finite training corpus will be **missing** some perfectly acceptable English word sequences. 
>- That is, cases where a particular $n$-gram **never occurs in the training data** but **appears in the test set**.
>  
>These unseen sequences or **zeros**—sequences that don’t occur in the training set zeros but do occur in the test set—are a problem for two reasons. 
>- First, their presence means we are *underestimating the probability* of word sequences that might occur, which hurts the performance of any application we want to run on this data. 
>- Second, if the probability of *any word* in the test set is $0$, the probability of *the whole test set* is $0$. 
>	- **Perplexity** is defined based on the inverse probability of the test set. Thus if some words in context have *zero probability*, we *can’t compute perplexity* at all,  
>
>The standard way to deal with putative “*zero probability n-grams*” that should really have some non-zero probability is called **smoothing** or **discounting**. 
>- Smoothing algorithms shave off a bit of probability mass from some more frequent events and give it to *unseen events*.
>  
>-- [[Speech and Language Processing by Jurafsky]] pp 45  





-----------
##  Recommended Notes and References


- [[Bag-of-Word Model for Document Representation]]
- [[Word Embedding]]
- [[Naive Bayes Model]]
- [[Multinomial Naive Bayes Model]]
- [[Multinomial Principle Component Analysis]]
- [[Probabilistic Latent Semantic Analysis or pLSA]]
- [[Latent Dirichlet Allocation]]


- [[Foundations of Statistical Natural Language Processing by Manning]] pp 191
- [[Speech and Language Processing by Jurafsky]] pp 45 - 49
- [[Artificial Intelligence Modern Approach by Russell]] pp 863