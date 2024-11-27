---
tags:
  - concept
  - natural_language_processing/word_representation
  - deep_learning/representation_learning
keywords:
  - word2vec_embedding
  - continuous_bag_of_words_embedding
topics:
  - natural_language_processing/word_representation
  - representation_learning
name: Contiuous-Bag-of-Words Algorithm for Word Embedding
date of note: 2024-09-12
---

## Concept Definition

>[!important]
>**Name**: Contiuous-Bag-of-Words Algorithm for Word Embedding

>[!important] Definition
>Let $(w_{1}\,{,}\ldots{,}\,w_{T})$ be a sequence of words in training corpus. 
>
>The *objective* of **continuous bag-of-words (CBOW) model** is to learn *embedding* $E: \mathcal{V} \to \mathbb{R}^{d}$ that maximizes the average log-probability
>$$
>\begin{align*}
>\max_{E}\; &\frac{1}{T}\sum_{i=1}^{T}\;\log p(w_{i}\;|\;w_{i-l} \,{,}\ldots{,}\,w_{i-1},\, w_{i+1},\,{,}\ldots{,}\,w_{i+l}) \\[8pt]
>&= \frac{1}{T}\sum_{i=1}^{T}\;\log p(w_{i}\;|\;B(w_{i}, l); E)
>\end{align*}
>$$
>where 
>- $l \ge 1$ is the *training context* and 
>- For each *target word* $w_{i}$, define the *context words* as neighboring words within a  *symmetric context window* of size $l$ $$c_{j} = \left\{\begin{array}{ll}w_{i-l+j-1} &j=1\,{,}\ldots{,}\,l \\[5pt] w_{i-l+j} &j=l+1\,{,}\ldots{,}\,2l \end{array}\right.$$
>	- The *neighborhood* of  $w_{i}$ consists of $2l+1$ words $$B(w_{i}, l) := \{   c_{1} \,{,}\ldots{,}\,c_{l},\, w_{i},\, c_{l+1}\,{,}\ldots{,}\, c_{2l}\} $$
>- and the probability is given by the *soft-max* $$\log p(w_{i}\;|\;B(w_{i}, l);\, E) = \sum_{j=1}^{2l}\left\langle  E(c_{j})\,,\, E(w_{i})   \right\rangle - \log \sum_{w\in \mathcal{V}} \exp \left(\sum_{j=1}^{2l}\left\langle  E(w)\,,\, E(c_{j})   \right\rangle\right) $$

- [[Bag-of-Word Model for Document Representation]]
- [[Word2Vec Algorithm for Static Word Embedding]]
- [[Word Embedding]]
- [[n-Gram Model and Language Model]]


### Learning CBOW model via Generalized Linear Model

>[!important] Definition
>The **CBOW model** learns embedding $E: \mathcal{V}\to \mathbb{R}^{d}$ via **softmax regression**
>$$
>\begin{align*}
>\max_{E}\;& \sum_{i=1}^{T}\sum_{j=1}^{2l}\left\langle  E(c_{j})\,,\, E(w_{i})   \right\rangle - \sum_{i=1}^{T}\log \sum_{w\in \mathcal{V}} \exp \left(\sum_{j=1}^{2l}\left\langle  E(w)\,,\, E(c_{j})   \right\rangle\right)
>\end{align*}
>$$
>- This problem is solved via 2-layer neural network.
>- Similar to **skip-gram model**, we can applies the *negative sampling*
>- We define the *training objective* for **Negative Sampling (NEG)** as $$\begin{align*}L(E) &:= \sum_{(i,j): Y(i,j)=1}-\log \sigma\left(\left\langle  E(w_{i})\,,\, E(c_{j})   \right\rangle\right) \\[8pt] &+ \sum_{(i,s):Y(i,s) = 0}\,-\log \sigma\left(-\left\langle  E(w_{i})\,,\, \sum_{s=1}^{k}\;\mathbb{E}_{ \tilde{c}_{s} \sim p_{\text{noise}} }\left[ E(\tilde{c}_{s})\right]  \right\rangle\right)\end{align*}$$
>	- we still take a pair of words and teach the model that they co-occur 
>	- but instead of *adding the errors* we *add the input words* for the same target word.

- [[Generalized Linear Models]]
- [[Noise Contrastive Estimation]]
- [[Density Ratio Estimation via Binary Classifiers]]

![[CBOW_example.png]]

![[CBOW_dsta_prepare.png]]

![[CBOW_model.png]]

>[!quote]
>The objective is to learn an embedding matrix $$E\in \mathbb{R}^{|\mathcal{V}| \times d}.$$
>- To begin with, we initialize the matrix randomly. 
>	- Here, $|\mathcal{V}|$ is the size of corpus vocabulary and $d$ is the dimension of the embedding. 
>- Let’s break down the shallow net in Figure 3-9 layer by layer. 
>	- In the *input layer*, **indices** of the words in context are used to fetch the corresponding *rows* from the *embedding matrix* $E$. 
>	- The vectors fetched are then **added** to get a single $d$-dim vector, and this is passed to the next layer.  $$h = \sum_{c_{j} \in B(w_{i}, l)}E_{c_{j},:}$$
>	- The *next layer* simply takes this $d$ vector and *multiplies* it with another matrix $E^{'} \in \mathbb{R}^{d \times  |\mathcal{V}| }.$ $$hE^{'} \in \mathbb{R}^{|\mathcal{V}|}$$
>	- This gives a $1 \times |\mathcal{V}|$ vector, which is fed to a *softmax function* to get probability distribution over the vocabulary space. 
>	- This distribution is compared with the label and uses *back propagation* to update both the matrices $E$ and $E^{'}$ accordingly. 
>	- At the end of the training, $E$ is the **embedding matrix** we wanted to learn.
>		- $E$ and $E'$ are different embeddings, but we can use either of them.
>
>-- Vajjala, S., Majumder, B., Gupta, A., & Surana, H. (2020). _Practical Natural Language Processing: A Comprehensive Guide to Building Real-World NLP Systems_ (1st edition). O’Reilly Media. pp 100

## Explanation

>[!important]
>Let $w_{i}$ be target word, and $c_{i}$ be its context words, i.e. $$c_{i} := (w_{i-l} \,{,}\ldots{,}\,w_{i-1},\, w_{i+1},\,{,}\ldots{,}\,w_{i+l})$$
>
>- In **continuous bag-of-word approach**, the task is to **predict** the representation of *target word*  given a combination of representation of all *context words* $$p(w_{i} \;|\;c_{i}) := p(w_{i}\;|\;w_{i-l} \,{,}\ldots{,}\,w_{i-1},\, w_{i+1},\,{,}\ldots{,}\,w_{i+l})$$
>- In **skip-gram approach**, the task is to **predict** the representation of *each context word*  given the representation of *target word* $$p(c_{i} \;|\;w_{i}) := p(w_{i-l} \,{,}\ldots{,}\,w_{i-1},\, w_{i+1},\,{,}\ldots{,}\,w_{i+l}\;|\;w_{i}) = \prod_{j=i-l, j\neq i}^{i+l}p(w_{j}\;|\;w_{i})$$

![[word2vec_cont_bog_skipgram.png]]

- [[Skip-Gram Algorithm with Negative Sampling for Word Embedding]]

>[!quote]
>- **Skip-gram**: works well with a small amount of the training data, represents well even rare words or phrases.  
>- **CBOW**: several times faster to train than the skip-gram, slightly better accuracy for the frequent words.


-----------
##  Recommended Notes and References





- [[Cosine Similarity and Cosine Distance]]


- [[Probabilistic Latent Semantic Analysis]]
- [[Latent Dirichlet Allocation]]

- [[Vector Space over a Field]]

- Wikipedia [Word2vec](https://en.wikipedia.org/wiki/Word2vec)
- [[Speech and Language Processing by Jurafsky]] 
- [[Practical Natural Language Processing by Vajjala]]  pp 98 - 100

- Mikolov, T., Chen, K., Corrado, G.S., & Dean, J. (2013). Efficient Estimation of Word Representations in Vector Space. _International Conference on Learning Representations_.
- Mikolov, T., Sutskever, I., Chen, K., Corrado, G. S., & Dean, J. (2013). Distributed representations of words and phrases and their compositionality. _Advances in neural information processing systems_, _26_.