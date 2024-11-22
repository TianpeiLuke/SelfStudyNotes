---
tags:
  - concept
  - natural_language_processing/word_representation
keywords: 
topics: 
name: 
date of note: 2024-09-12
---

## Concept Definition

>[!important]
>**Name**: 



### Continuous Bag-of-Words




### Skip-Gram


![[word2vec_cont_bog_skipgram.png]]

## Explanation

>[!quote]
>The *intuition* of **word2vec** is that instead of counting how often each word $w$ occurs near, say, `apricot`, we’ll instead *train a classifier* on a binary prediction task: 
>- “Is word `w` likely to show up near `apricot`?” 
>
>We *don’t actually care* about this prediction task;  instead we’ll take the *learned classifier weights* as the **word embeddings**. 
>
>The **revolutionary intuition** here is that we can just use running text as *implicitly supervised training data* for such a classifier; 
>- a word `c` that occurs *near the target word* `apricot` acts as *gold ‘correct answer’* to the question 
>	- “Is word `c` likely to show up near `apricot`?” 
>
>This method, often called **self-supervision**, avoids the need for self-supervision any sort of hand-labeled supervision signal.
>
>-- [[Speech and Language Processing by Jurafsky]] pp 118

- [[Self-Supervised Learning]]



-----------
##  Recommended Notes and References


- [[n-Gram Model and Language Model]]
- [[Word Embedding]]
- [[n-Gram Model and Language Model]]
- [[Cosine Similarity and Cosine Distance]]


- [[Probabilistic Latent Semantic Analysis]]
- [[Latent Dirichlet Allocation]]


- [[Vector Space over a Field]]

- Wikipedia [Vector_space_model](https://en.wikipedia.org/wiki/Vector_space_model)
- [[Speech and Language Processing by Jurafsky]] pp 116 - 120