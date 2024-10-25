---
tags:
  - concept
  - deep_learning/sequential_networks
  - deep_learning/models
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





-----------
##  Recommended Notes and References




- [[Recurrent Neural Network]]
- [[Gated Recurrent Units in Neural Network]]
- [[Long-Short Term Memory Network]]
- [[Residual Neural Network]]

- [[Linear Dynamic System]]


- [[Deep Learning by Goodfellow]] pp 383 - 384
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] 