---
tags:
  - concept
  - deep_learning/sequential_networks
  - deep_learning/models
  - bidirectional_recurrent_neural_network
  - recurrent_neural_network
  - bidirectional_rnn
keywords:
  - bidirectional_rnn
  - bidirectional
topics:
  - deep_learning/models
name: Bidirectional Recurrent Neural Network
date of note: 2024-08-31
---

## Concept Definition

>[!important]
>**Name**: Bidirectional Recurrent Neural Network

![[Recurrent Neural Network#^81c4ad]]





![[bidirectional_rnn.png]]


## Explanation

>[!quote]
>As the name suggests, **bidirectional RNNs** combine 
>- an RNN that *moves forward* through time, beginning from the *start* of the sequence, 
>- with another RNN that *moves backward through time*, beginning from the end of the sequence.
>
>Figure 10.11 illustrates the typical bidirectional RNN, with 
>- $h(t)$ standing for the *state* of the sub-RNN that *moves forward* through time 
>- and $g(t)$ standing for the *state* of the sub-RNN that *moves backward* through time. 
>  
>This allows the *output units* $o(t)$ to compute a *representation* that depends on **both the past and the future** but is most sensitive to the *input values* around time $t$, without having to specify a *fixed-size window* around t (as one would have to do with a feedforward network, a convolutional network, or a regular RNN with a fixed-size look-ahead buffer).
>
>-- [[Deep Learning by Goodfellow]] pp 384

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]


### Compared with PLM

- [[Bidirectional Encoder Representation from Transformer or BERT]]


## Example

### ELMo or Embeddings from Language Models


- [[EMLo or Embeddings from Language Models for Word Embedding]]
- [[Contextual Embeddings and Word Sense]]
- [[Word Embedding]]



-----------
##  Recommended Notes and References





- [[Recurrent Neural Network]]
- [[Gated Recurrent Units in Neural Network]]
- [[Long-Short Term Memory Network or LSTM]]
- [[Residual Neural Network]]

- [[Linear Dynamic System]]
- [[Autoregressive Models]]

- [[Deep Learning by Goodfellow]] pp 383 - 384
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] 
- Matthew E. Peters, Mark Neumann, Mohit Iyyer, Matt Gardner, Christopher Clark, Kenton Lee, and Luke Zettlemoyer. 2018. [Deep Contextualized Word Representations](https://aclanthology.org/N18-1202). In _Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long Papers)_, pages 2227–2237, New Orleans, Louisiana. Association for Computational Linguistics.
- Liu, Q., Kusner, M. J., & Blunsom, P. (2020). A survey on contextual embeddings. _arXiv preprint arXiv:2003.07278_.