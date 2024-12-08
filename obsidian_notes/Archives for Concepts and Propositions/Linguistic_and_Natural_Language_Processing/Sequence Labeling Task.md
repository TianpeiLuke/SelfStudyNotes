---
tags:
  - concept
  - natural_language_processing/sequence_labeling
keywords:
  - sequence_labeling
topics:
  - natural_language_processing/sequence_labeling
name: Sequence Labeling Task
date of note: 2024-11-17
---

## Concept Definition

>[!important]
>**Name**: Sequence Labeling Task

>[!important] Definition
>The task of **sequence labeling**  is to assign a label for *each token* in the sequence.
>
>$$(w_{1}\,{,}\ldots{,}\,w_{T}) \to (y_{1}\,{,}\ldots{,}\,y_{T})$$
>so that 
>$$
>\begin{array}{cccc}
> y_{1} & y_{2} & \ldots & y_{T} \\[5pt] 
> \uparrow &  \uparrow & &  \uparrow  \\
> w_{1} & w_{2} & \ldots & w_{T} 
>\end{array}
>$$
>where $y_{t}\in \mathcal{Y}$

^571afc


- [[Classification Problem]]


## Explanation


>[!info]
>**Sequence labeling** follow a "*many-to-many*" architecture.
>

![[rnn_sequence_one_sequence.png]]


- [[Encoder-Decoder Sequence-to-Sequence Architecture]]


## Models


- [[Support Vector Machine Kernel Expansion and RKHS]]
- [[Positive Definite Kernel Examples]]

- [[Probabilistic Graphical Models]]

- [[Dynamic Bayesian Network]]
- [[Kalman Filter Discrete-Time]]
- [[Hidden Markov Model]]
- [[Conditional Random Field]]


- [[Recurrent Neural Network]]
- [[Long-Short Term Memory Network or LSTM]]
- [[Gated Recurrent Units in Neural Network]]
- [[Encoder-Decoder Sequence-to-Sequence Architecture]]


- [[Large Language Model and Pretrained Language Models]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Generative Pre-trained Transformer or GPT]]


## Examples

- [[Masked Language Modeling as Language Model Training Task]]
- [[Part-of-Speech Tagging]]
- [[Name Entity Recognition]]
- [[Semantic Role Labeling]]



-----------
##  Recommended Notes and References





- [[Speech and Language Processing by Jurafsky]] pp 235 - 236