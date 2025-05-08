---
tags:
  - concept
  - natural_language_processing/word_representation
keywords:
  - word2vec_embedding
topics:
  - natural_language_processing/word_representation
name: Word2Vec Algorithm for Static Word Embedding
date of note: 2024-09-12
---

## Concept Definition

>[!important]
>**Name**: Word2Vec Algorithm for Static Word Embedding

![[Vector Semantics and Distributional Hypothesis in Linguistic#^849498]]

![[Vector Semantics and Distributional Hypothesis in Linguistic#^be40ca]]

- [[Vector Semantics and Distributional Hypothesis in Linguistic]]
- [[Word Embedding]]
- [[Vector Space Model in Information Retrieval]]

### Continuous Bag-of-Words

>[!important] Definition
>Let $w_{i}$ be target word, and $c_{i}$ be its context words, i.e. $$c_{i} := (w_{i-l} \,{,}\ldots{,}\,w_{i-1},\, w_{i+1},\,{,}\ldots{,}\,w_{i+l})$$
>
>- In **continuous bag-of-word approach**, the task is to **predict** the representation of *target word*  given a combination of representation of all *context words* $$p(w_{i} \;|\;c_{i}) := p(w_{i}\;|\;w_{i-l} \,{,}\ldots{,}\,w_{i-1},\, w_{i+1},\,{,}\ldots{,}\,w_{i+l})$$

- [[Continuous-Bag-of-Words Algorithm for Word Embedding]]

### Skip-Gram

>[!important] Definition
>Let $w_{i}$ be target word, and $c_{i}$ be its context words, i.e. $$c_{i} := (w_{i-l} \,{,}\ldots{,}\,w_{i-1},\, w_{i+1},\,{,}\ldots{,}\,w_{i+l})$$
>
>- In **skip-gram approach**, the task is to **predict** the representation of *each context word*  given the representation of *target word* $$p(c_{i} \;|\;w_{i}) := p(w_{i-l} \,{,}\ldots{,}\,w_{i-1},\, w_{i+1},\,{,}\ldots{,}\,w_{i+l}\;|\;w_{i}) = \prod_{j=i-l, j\neq i}^{i+l}p(w_{j}\;|\;w_{i})$$

>[!quote]
>The **intuition** of *skip-gram* is:  
>1. Treat the *target* word and a *neighboring context word* as **positive examples**. 
>2. *Randomly sample* other words in the lexicon to get **negative samples**. 
>3. Use *logistic regression* to train a classifier to distinguish those two cases. 
>4. Use the learned **weights** as the **embeddings**.
>   
>-- [[Speech and Language Processing by Jurafsky]] pp 118   

- [[Skip-Gram Algorithm with Negative Sampling for Word Embedding]]

![[word2vec_cont_bog_skipgram.png]]

## Explanation

>[!quote]
>The *intuition* of **word2vec** is that instead of counting how often each word $w$ occurs near, say, `apricot`, we’ll instead *train a classifier* on a binary prediction task: 
>- “Is word `w` likely to show up near `apricot`?” 
>
>- We *don’t actually care* about this prediction task;  instead we’ll take the *learned classifier weights* as the **word embeddings**. 
>
>The **revolutionary intuition** here is that we can just use running text as *implicitly supervised training data* for such a classifier; 
>- a word `c` that occurs *near the target word* `apricot` acts as *gold ‘correct answer’* to the question 
>	- “Is word `c` likely to show up near `apricot`?” 
>
>This method, often called **self-supervision**, avoids the need for self-supervision any sort of hand-labeled supervision signal.
>
>-- [[Speech and Language Processing by Jurafsky]] pp 118

- [[Self-Supervised Learning]]

>[!quote]
>We’ll see how to do *neural networks* in the next chapter, but **word2vec** is a  much simpler model than the neural network language model, in two ways. 
>- First,  word2vec simplifies the task (making it **binary classification** instead of *word prediction*). 
>- Second, word2vec simplifies the architecture (training a **logistic regression  classifier** instead of a *multi-layer neural network* with hidden layers that demand  more sophisticated training algorithms).
>  
>-- [[Speech and Language Processing by Jurafsky]] pp 118  

- [[Logistic Regression]]
- [[Classification Problem]]
- [[Artificial Neural Network and Deep Learning]]


>[!important]
>The **global representation** of word learns *one embedding* for each word in the vocabulary, *regardless* of context around it.
>
>A more adaptive approach is the **contextual embedding**, which provides *different representation* of same word for *different context*.

- [[Contextual Embeddings and Word Sense]]



-----------
##  Recommended Notes and References


- [[n-Gram Model and Language Model]]
- [[Word Embedding]]
- [[n-Gram Model and Language Model]]
- [[Cosine Similarity and Cosine Distance]]


- [[Probabilistic Latent Semantic Analysis or pLSA]]
- [[Latent Dirichlet Allocation or LDA]]


- [[Vector Space over a Field]]

- Wikipedia [Word2vec](https://en.wikipedia.org/wiki/Word2vec)
- [[Speech and Language Processing by Jurafsky]] pp 117 - 120
- [[Deep Learning Foundations and Concepts by Bishop]] pp 375 - 377
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 773
- [[Practical Natural Language Processing by Vajjala]] 
- Youtube
	- [Lecture 2 | Word Vector Representations: word2vec](https://www.youtube.com/watch?v=ERibwqs9p38)

- Mikolov, T., Chen, K., Corrado, G.S., & Dean, J. (2013). Efficient Estimation of Word Representations in Vector Space. _International Conference on Learning Representations_.
- Mikolov, T., Sutskever, I., Chen, K., Corrado, G. S., & Dean, J. (2013). Distributed representations of words and phrases and their compositionality. _Advances in neural information processing systems_, _26_.