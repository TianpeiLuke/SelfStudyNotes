---
tags:
  - concept
  - natural_language_processing/word_representation
  - deep_learning/representation_learning
keywords:
  - skip_gram_word_embedding
topics:
  - natural_language_processing/word_representation
name: Skip-Gram Algorithm with Negative Sampling for Word Embedding
date of note: 2024-09-12
---

## Concept Definition

>[!important]
>**Name**: Skip-Gram Algorithm with Negative Sampling for Word Embedding

![[Co-Occurrence Matrix#^f79d93]]

- [[Co-Occurrence Matrix]]

### Skip-Gram Word Embedding

>[!important] Definition
>Let $(w_{1}\,{,}\ldots{,}\,w_{T})$ be a sequence of words in training corpus. 
>
>The *objective* of **skip-gram model** is to learn *embedding* $E: \mathcal{V} \to \mathbb{R}^{d}$ that maximizes the average log-probability
>$$
>\max_{E}\; \frac{1}{T}\sum_{i=1}^{T}\;\sum_{j \in [-l, l] \land j\neq 0 }\;\log p(w_{i+j}\;|\;w_{i};\, E)
>$$
>where 
>- $l \ge 1$ is the *training context* and 
>- For each *target word* $w_{i}$, define the *context words* as neighboring words within a  *symmetric context window* of size $l$ $$c_{j} = \left\{\begin{array}{ll}w_{i-l+j-1} &j=1\,{,}\ldots{,}\,l \\[5pt] w_{i-l+j} &j=l+1\,{,}\ldots{,}\,2l \end{array}\right.$$
>	- The *neighborhood* of  $w_{i}$ consists of $2l+1$ words $$B(w_{i}, l) := \{   c_{1} \,{,}\ldots{,}\,c_{l},\, w_{i},\, c_{l+1}\,{,}\ldots{,}\, c_{2l}\} $$
>- and the probability is given by the *soft-max* $$\log p(w_{i+j}\;|\;w_{i};\, E) = \left\langle  E(w_{i+j})\,,\, E(w_{i})   \right\rangle - \log \sum_{w\in \mathcal{V}} \exp \left(\left\langle  E(w)\,,\, E(w_{i})   \right\rangle\right) $$
>- Note that **skip-gram** assumes that *all context words* are *conditionally independent* given target word. $$w_{i+j} \perp w_{i+k} \;|\;w_{i}$$

- [[Softmax Function and Log-Sum-Exp Function]]
- [[Conditional Independence]]

![[skipgram_embedding.png]]

![[skipgram_embedding.png]]
### Learning Skip-Gram Embedding with Negative Sampling

>[!important] Definition
>Let $\mathcal{V}$ be the *vocabulary set* and $\mathcal{D}$ be a *training corpus* i.e. a sequence of words/tokens $$\mathcal{D} := (w_{1} \,{,}\ldots{,}\,w_{T}) \subset \mathcal{V}^{*}$$
>- For each *target word* $w_{i}$, define the *context words* as neighboring words within a  *symmetric context window* of size $l$ $$c_{j} = \left\{\begin{array}{ll}w_{i-l+j-1} &j=1\,{,}\ldots{,}\,l \\[5pt] w_{i-l+j} &j=l+1\,{,}\ldots{,}\,2l \end{array}\right.$$
>	- The *neighborhood* of  $w_{i}$ consists of $2l+1$ words $$B(w_{i}, l) := \{   c_{1} \,{,}\ldots{,}\,c_{l},\, w_{i},\, c_{l+1}\,{,}\ldots{,}\, c_{2l}\} $$
>
>Instead of training on $$\log p(c_{j}|w_{i}),$$  the **skip-gram with negative sampling (SGNS)**  applies the *Noise Contrastive Estimation* to *approximately* maximize the average log-probability.
>
>Specifically, for each  *target word* $w_{i}^{d}$,  select a *candidate context word* as follows $$c \sim \left\{\begin{array}{ll} \text{Uniform}(c_{1} \,{,}\ldots{,}\,c_{l},\, c_{l+1}\,{,}\ldots{,}\, c_{2l}) &\text{with probability }p \\[5pt] p_{\text{noise}}(c) &\text{with probability }1 - p \end{array}\right.$$ that is 
>- with probability $p$,  we randomly select a **context word** in the context window;
>- with probability $1-p$ we randomly select a **noise sample** from vocabulary based on $p_{noise}(w)$
>- Denote $k$ i.i.d. *noisy sample* as $$\tilde{c}_{s} \sim p_{\text{noise}}(c), \quad s=1\,{,}\ldots{,}\,k$$
>- The joint distribution of context word given target word is from a *mixture family* $$p(c_{1}\,{,}\ldots{,}\,c_{2l} | w_{i}) = p\;\prod_{j=1}^{2l}p(c_{j}|w_{i}) + (1-p)\;\prod_{j=1}^{K}p_{\text{noise}}(\tilde{c}_{j})$$
>  
>The **skip-gram with negative sampling (SGNS)** learns a probabilistic *classification* model such that 
>- for a given tuple $(w, c)$,  return the probability that $c$ is a real context work. That is, define the target label $$y := y(w, c) = \left\{\begin{array}{ll}1 & \text{if }c\in B(w, l) \\[5pt] 0 & \text{if }c\not\in B(w,l) \end{array}\right.$$
>
>Based on **distributional hypothesis**, the classification probability depends on the *cosine similarity* between *embeddings* of target word $t$ and the candidate context word $c$
>- In particular, we **learns the representation** $E: \mathcal{V} \to \mathbb{R}^{d}$, such that $$p(y_{i} = 1\;|\,w_{i},\, c_{j}) = \sigma \left(\left\langle  E(w_{i})\,,\, E(c_{j})   \right\rangle\right)$$ where $\sigma(\cdot)$ is the *sigmoid function* $$\sigma(x) := \frac{1}{1 + \exp(-x)}$$
>- That is, the classification is based on *logistic regression.*
>- **Skip-gram models** assume that *all* context words are *independent.* That is $$\log p(y_{i}=1\,|\, w_{i},\, c_{1:2l}) = \sum_{j=1}^{2l}\;\log \sigma\left(\left\langle  E(w_{i})\,,\, E(c_{j})   \right\rangle\right).$$
>- We define the *training objective* for **Negative Sampling (NEG)** as $$\begin{align*}L(E) &:= \sum_{(i,j): Y(i,j)=1}-\log \sigma\left(\left\langle  E(w_{i})\,,\, E(c_{j})   \right\rangle\right) \\[8pt] &+ \sum_{(i,s):Y(i,s) = 0}\,\sum_{s=1}^{k}\;\mathbb{E}_{ \tilde{c}_{s} \sim p_{\text{noise}} }\left[ -\log \sigma\left(-\left\langle  E(w_{i})\,,\, E(\tilde{c}_{s})   \right\rangle\right) \right]  \end{align*}$$
>	- For each *positive sample*, we need $k \in [5, 20]$ *negative samples*.
>	- $$1 - \sigma(x) = \sigma(-x).$$


- [[Vector Semantics and Distributional Hypothesis in Linguistic]]
- [[Logistic Regression]]
- [[Sigmoid Function as Activation for Deep Learning]]
- [[Noise Contrastive Estimation]]
- [[Mixture Family of Distributions]]
- [[Density Ratio Estimation via Binary Classifiers]]


![[skip_gram_example.png]]

![[skip_gram_data_prepare.png]]

![[skip_gram_model.png]]


>[!info]
>Compare to the *NCE loss*
>$$
>\begin{align*}
> L(\theta) &= \mathbb{E}_{p_{\text{joint, data}}(X, Y) }\left[ -\log p_{\text{joint}, \theta}(Y \,|\,X) \right] \\[8pt]
> &= \sum_{i: Y_{i} = 1}\left[-\log \frac{p(X_{i}; \theta)}{p(X_{i}; \theta)+ p_{n}(X_{i})} \right] +  \sum_{i: Y_{i} = 0}\left[-\log \frac{p_{n}(X_{i})}{p(X_{i}; \theta)+ p_{n}(X_{i})} \right] \\[8pt]
> &= \sum_{i: Y_{i} = 1}\left[ -\log \sigma \left(\log p(X_{i}; \theta) - \log p_{n}(X_{i}) \right) \right] \\[5pt]
> &\;\; +  \sum_{i: Y_{i} = 0}\left[ -\log \left\{1 - \sigma \left(\log p(X_{i}; \theta) - \log p_{n}(X_{i}) \right)  \right\}\right]
>\end{align*}
>$$
>
>The **SGNS loss** did not use the *noise ratio* since we only cares for the embedding map $E$.  


### Noise Distribution

>[!important]
>It is common to define the noise distribution via *unigram model* as $$p_{\text{noise}, \alpha}(c) = \frac{\text{C}(c)^{\alpha}}{\sum_{w\in \mathcal{V}}\text{C}(w)^{\alpha}}$$ where
>- $C(w)$ is the count of occurrence of word $w$.
>-  it is common to choose $\alpha=0.75.$

- [[n-Gram Model and Language Model]]

### Word Embedding Output

>[!important]
>The *skip-gram* learns two embedding for each target world $w_{i}$ 
>- **target embedding** $E(w_{i})$
>- **context embedding** $E(c_{j})$
>- It is common to just add them together as the **word embedding** for $w_{i}$ as $$\hat{w}_{i} := E(w_{i}) + E(c_{j})$$
>- Alternatively we can drop the *context embedding*





## Explanation

>[!quote]
>The **intuition** of *skip-gram* is:  
>1. Treat the *target* word and a *neighboring context word* as **positive examples**. 
>2. *Randomly sample* other words in the lexicon to get **negative samples**. 
>3. Use *logistic regression* to train a classifier to distinguish those two cases. 
>4. Use the learned **weights** as the **embeddings**.
>   
>-- [[Speech and Language Processing by Jurafsky]] pp 118   

- [[Noise Contrastive Estimation]]

>[!important]
>Let $w_{i}$ be target word, and $c_{i}$ be its context words, i.e. $$c_{i} := (w_{i-l} \,{,}\ldots{,}\,w_{i-1},\, w_{i+1},\,{,}\ldots{,}\,w_{i+l})$$
>
>- In **continuous bag-of-word approach**, the task is to **predict** the representation of *target word*  given a combination of representation of all *context words* $$p(w_{i} \;|\;c_{i}) := p(w_{i}\;|\;w_{i-l} \,{,}\ldots{,}\,w_{i-1},\, w_{i+1},\,{,}\ldots{,}\,w_{i+l})$$
>- In **skip-gram approach**, the task is to **predict** the representation of *each context word*  given the representation of *target word* $$p(c_{i} \;|\;w_{i}) := p(w_{i-l} \,{,}\ldots{,}\,w_{i-1},\, w_{i+1},\,{,}\ldots{,}\,w_{i+l}\;|\;w_{i}) = \prod_{j=i-l, j\neq i}^{i+l}p(w_{j}\;|\;w_{i})$$

![[word2vec_cont_bog_skipgram.png]]

- [[Contiuous-Bag-of-Words Algorithm for Word Embedding]]
- [[Word2Vec Algorithm for Static Word Embedding]]

![[skipgram_embedding_pca.png]]

### Subsampling of Frequent Words

>[!quote]
>In very large corpora, the *most frequent words* can easily occur hundreds of millions of times (e.g., “in”, “the”, and “a”). Such words usually provide **less information value** than the *rare words*. 
>- For example, while the Skip-gram model benefits from observing the co-occurrences of “France” and “Paris”, it benefits much less from observing the frequent co-occurrences of “France” and “the”, as nearly every word co-occurs frequently within a sentence with “the”. 
>- This idea can also be applied in the **opposite direction**; 
>	- the vector representations of **frequent words** *do not change significantly* after training on several million examples.  
>
>To counter the **imbalance** between the rare and frequent words, we used a simple **subsampling approach**: 
>- each word $w_{i}$ in the training set is **discarded** with probability computed by the formula $$P(w_{i}) = 1- \sqrt{ \frac{t}{f(w_{i})} }$$ where 
>	- $f(w_{i})$ is the *frequency* of word $w_{i}$
>	- and $t$ is a *chosen threshold,* typically around $10^{-5}$.
>	  
>We chose this subsampling formula because it aggressively subsamples words whose frequency is greater than t while preserving the ranking of the frequencies. Although this subsampling formula was chosen heuristically, we found it to work well in practice. It accelerates learning and even significantly improves the accuracy of the learned vectors of the rare words, as will be shown in the following sections.
>
>-- 	  Mikolov, T., Sutskever, I., Chen, K., Corrado, G. S., & Dean, J. (2013). Distributed representations of words and phrases and their compositionality. _Advances in neural information processing systems_, _26_. pp 5




-----------
##  Recommended Notes and References


- [[n-Gram Model and Language Model]]
- [[Word Embedding]]
- [[n-Gram Model and Language Model]]
- [[Cosine Similarity and Cosine Distance]]


- [[Probabilistic Latent Semantic Analysis]]
- [[Latent Dirichlet Allocation]]

- [[Vector Space over a Field]]

- [[Speech and Language Processing by Jurafsky]] pp 117 - 122
- [[Practical Natural Language Processing by Vajjala]] pp 101 - 103- [[Practical Natural Language Processing by Vajjala]] pp 101 - 103
- [[Deep Learning Foundations and Concepts by Bishop]] pp 375
- Wikipedia [Word2vec](https://en.wikipedia.org/wiki/Word2vec)
- Mikolov, T., Chen, K., Corrado, G.S., & Dean, J. (2013). Efficient Estimation of Word Representations in Vector Space. _International Conference on Learning Representations_.
- Mikolov, T., Sutskever, I., Chen, K., Corrado, G. S., & Dean, J. (2013). Distributed representations of words and phrases and their compositionality. _Advances in neural information processing systems_, _26_.