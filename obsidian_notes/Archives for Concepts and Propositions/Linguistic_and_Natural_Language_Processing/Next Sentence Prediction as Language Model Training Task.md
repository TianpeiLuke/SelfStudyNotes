---
tags:
  - concept
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
keywords:
  - next_sentence_prediction_nlp
topics:
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
name: Next Sentence Prediction as Language Model Training Task
date of note: 2024-11-27
---

## Concept Definition

>[!important]
>**Name**: Next Sentence Prediction as Language Model Training Task

>[!important] Definition
>In the task of **Next Sentence Prediction (NSP)**, the model is presented with *pairs* of sentences and is asked to *predict* whether each pair consists of an actual pair of *adjacent sentences* from the training corpus or a pair of *unrelated sentences*.
>$$
>y_{i}(s_{1}, s_{2}) = \left\{ 
>\begin{array}{cl}
> 1 & \text{ if }s_{1} \text{ is adjacent to }s_{2} \\[5pt] 
> 0 & \text{ if }s_{1}, s_{2} \text{ are unrelated}
>\end{array}
>\right.
>$$

^48fb58

- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Large Language Model and Pretrained Language Models]]
- [[Self-Supervised Training of Large Language Model and Teacher Forcing]]

>[!example]
>In **BERT**, 
>- *$50\%$ of training pairs* consists of positive pairs, 
>- and in the other *$50\%$*, the second sentence of a pair was *randomly selected* from elsewhere in the corpus.

^3c0dea

>[!important] Definition
>In **NSP training**, two additional *special tokens* are introduced:
>- `[CLS]` is *prepended* to the input sentence pair, 
>- `[SEP]` is placed *between* the adjacent sentences, and *after* the final token of second sentence.
>- The *embeddings* representing the *first sentence* and *second sentence* of input are *added* to the word and positional embeddings to distinguish two sentences. $$E(w_{i}^{(j)}) = E(w_{i}) + E(s^{j})$$
>- In the training, let $$h_{L}^{CLS} \in \mathbb{R}^{d}$$ be the output of the last transformer layer associated with token `[CLS]`
>	- $h_{L}^{CLS}$ represents the **next sentence prediction**.
>
>As with MLM, a new head called **NSP head** is introduced.
>- The **NSP head** consists of a learned set of *binary classification weights* $$W_{\text{NSP}} \in \mathbb{R}^{2\times d}$$
>- The binary prediction is given by $$y^{i} =  \sigma\left( W_{\text{NSP}}\,h_{L}^{CLS} \right)$$
>- The *cross-entropy loss* is used to compute the **NSP loss** $$\begin{align*}L(\theta) &= \sum_{i: Y_{i} = 1}\left[ -\log y^{i} \right]  +  \sum_{i: Y_{i} = 0}\left[ -\log \left\{1 - y^{i} \right\}\right]\end{align*}$$
>	- This loss follows the *Noise Contrastive Loss (NCE)* for representation learning

^c626ba

- [[Logistic Regression]]
- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]
- [[Softmax Function and Log-Sum-Exp Function]]
- [[Cross-Entropy Loss Function]]
- [[Noise Contrastive Estimation]]

![[next_sentence_prediction_loss.png]]

>[!info]
>The output of **NSP head** is of dimension $$(\cdot, 2)$$


## Explanation

>[!info]
>The **RoBERTa** model dropped the *next sentence prediction task.*




-----------
##  Recommended Notes and References


- [[liuRoBERTaRobustlyOptimized2019]]
- [[devlinBERTPretrainingDeep2019]]
- [[Masked Language Modeling as Language Model Training Task]]

- [[Speech and Language Processing by Jurafsky]] pp 228 - 230