---
tags:
  - concept
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
  - natural_language_processing/sequence_labeling
  - fine_tuning
  - sequence_labeling
  - BERT
  - bidirectional_encoder_representation_from_transformer
keywords:
  - fine_tuning_bert
  - sequence_labeling
topics:
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
name: Fine-Tuning for Sequence Labeling via BERT
date of note: 2024-11-28
---

## Concept Definition

>[!important]
>**Name**: Fine-Tuning for Sequence Labeling via BERT

![[Pre-Training and Fine-Tuning Paradigm for Transfer Learning#^7e9176]]

![[Pre-Training and Fine-Tuning Paradigm for Transfer Learning#^036480]]

### Sequence Labeling

![[Sequence Labeling Task#^571afc]]

- [[Sequence Labeling Task]]
- [[Classification Problem]]
- [[Encoder-Decoder Sequence-to-Sequence Architecture]]

>[!important] Definition
>In **sequence labeling**, we pass the final contextual embedding $$h_{L}^{i}\in \mathbb{R}^{d}$$ for *each token* to a **classification head**
>- Each classification head corresponds to a logistic regression or neural network $$u_{i} = \text{softmax}\left(W_{K}\,h_{L}^{i}\right), \quad i=1\,{,}\ldots{,}\,T$$ where $$W_{K}\in \mathbb{R}^{|\mathcal{Y}|\times d}$$
>- A *greedy decoding* method would find token as $$y_{i} = \arg\max_{k}(u_{i})$$

- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Masked Language Modeling as Language Model Training Task]]
- [[Logistic Regression]]
- [[Softmax Function and Log-Sum-Exp Function]]
- [[Greedy Decoding for Causal Language Model Generation]]
- [[Beam Search for Causal Decoding of Language Model]]

![[sequence_labeling_ner_bert.png]]


## Explanation

>[!info]
>**Sequence labeling** follow a "*many-to-many*" architecture.
>


![[rnn_sequence_one_sequence.png]]





## Applications

### Part-of-Speech Tagging

- [[Part-of-Speech Tagging]]

### Name Entity Recognition

- [[Name Entity Recognition]]

### Semantic Role Labeling

- [[Semantic Role Labeling]]



-----------
##  Recommended Notes and References


- [[Pre-Training and Fine-Tuning Paradigm for Transfer Learning]]
- [[Large Language Model and Pretrained Language Models]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]


- [[Transfer Learning]]
- [[Foundational Models for Transfer Learning]]




- [[Speech and Language Processing by Jurafsky]] pp 234 - 236
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1041
- [[Deep Learning Foundations and Concepts by Bishop]] pp 3, 22, 189, 392