---
tags:
  - concept
  - machine_learning/strategy
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
keywords:
  - teacher_forcing_llm
  - self_supervised_training_llm
topics:
  - machine_learning_strategy
  - natural_language_processing/large_language_models
name: Self-Supervised Training of Large Language Model and Teacher Forcing
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Self-Supervised Training of Large Language Model and Teacher Forcing

>[!important] Definition
>The task of **pre-training** large langauge models is done via the **self-supervision** or **self-training**.
>- In self-training for language modeling, we take a corpus of text $$(w_{1}\,{,}\ldots{,}\,w_{T})$$ as training material and at each time step $t$ ask  the model to predict the *next word* (**Next Word Prediction**). $$L(w_{t}, \hat{w}_{t}) := - \mathbb{1}\left\{ \hat{w}_{t} = w_{t} \right\}  \log p( \hat{w}_{t}|w_{<t})$$
>- We call such  a model *self-supervised* because we don’t have to add any special gold labels to  the data; it used the natural sequence of words as its own supervision.

>[!important] Definition
>Consider a corpus of training text $$(w_{1}\,{,}\ldots{,}\,w_{T}).$$
>- Assume the at each $t$, **autoregressive (causal) language model** is given by $$\hat{y}_{t} := p(w_{t}\,|\,w_{t-1}\,{,}\ldots{,}\,w_{1}) := p(w_{t}\,|\,w_{<t}).$$
>	- The language model has a *causal mask* so that it cannot see next word.
>-  The *distribution of next word*  given by the model is $\hat{y}_{t} \in \Delta_{|\mathcal{V}|}$  based on previous words
>- The model prediction is evaluated based on *ground truth word* $w_{t}=x_{i}$ i.e. denote the true distribution of next word as the *one-hot encoding* $$y_{t}(i) := \left\{\begin{array}{cl}1 & \text{if }  w_{t} = x_{i} \\[7pt]  0 & \text{otherwise } \end{array}\right. \implies y_{t} := \delta_{x_{i}} \in \Delta_{|\mathcal{V}|}.$$
> 
>The objective function of  **self-supervision** or **self-training** of language model is given by the *cross-entropy loss*
>$$
>L_{CE}(y_{t}, \hat{y}_{t}) = -\sum_{i: x_{i}\in \mathcal{V}}y_{t}(i)\,\log \hat{y}_{t}(i) := - \mathbb{1}\{w_{t} = x_{i}\}\,\log p(w_{t}\,|\,w_{<t})
>$$
>- At  time $t+1$, the model takes as input the *correct sequence* of tokens $(w_{t}, w_{<t})$, and uses them to compute the *distribution of next word conditioned* on  $w_{<t+1}$, and then evaluate it with the ground truth one-hot distribution.
>- The idea that we always give the model the *correct history sequence* $(w_{t}, w_{<t})$ to predict the next word is called the **teacher forcing.**
>	- This is in contrast to the naive idea that feed the model with *predicted next word* $(\hat{w}_{t}, w_{<t})$

^77c15b

- [[Dirac Measure]]
- [[Large Language Model and Pretrained Language Models]]
- [[Self-Supervised Learning]]
- [[Cross-Entropy Loss Function]]

![[self_supervised_training_llm.png]]


## Explanation

### Compare with Self-Training in RNN

>[!quote]
>Note the key difference between this figure and the earlier RNN-based version  shown in Fig. 8.6. 
>- There the calculation of the outputs and the losses at each step  was **inherently serial** given the *recurrence* in the calculation of the hidden states.  
>- With *transformers*, each training item can be processed **in parallel** since the output  for each element in the sequence is *computed separately*.
>  
>-- [[Speech and Language Processing by Jurafsky]] pp 211  

![[self_train_rnn.png]]

### Compare with Masked Language Modeling

>[!quote]
>We trained **causal transformer language models** in Chapter 9 by making them iteratively predict the next word in a text. 
>
>But *eliminating the causal mask* in attention makes the guess-the-next-word language modeling task trivial—the answer  is directly available from the context—so we’re in need of a new training scheme.  
>- Instead of trying to predict the next word, the model learns to perform a *fill-in-the-blank task*, technically called the **cloze task**.
>  
>-- [[Speech and Language Processing by Jurafsky]] pp 226  

![[masked_language_model_training.png]]

![[Masked Language Modeling as Language Model Training Task#^0229dc]]

- [[Masked Language Modeling as Language Model Training Task]]


-----------
##  Recommended Notes and References


- [[Deep Learning Foundations and Concepts by Bishop]] pp 5, 375
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 743
- [[Deep Learning by Goodfellow]] pp 372 - 373
- [[Speech and Language Processing by Jurafsky]] pp 155, 163,  210 - 211