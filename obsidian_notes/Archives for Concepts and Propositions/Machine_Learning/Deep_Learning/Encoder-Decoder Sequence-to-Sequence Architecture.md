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
  - deep_learning/sequential_networks
name: Encoder-Decoder Sequence-to-Sequence Architecture
date of note: 2024-08-31
---

## Concept Definition

>[!important]
>**Name**: Encoder-Decoder Sequence-to-Sequence Architecture

### Sequence-to-Sequence Models

>[!quote]
>In this section we introduce a new model, the **encoder-decoder model**, which is used  when we are taking an *input sequence* and *translating* it to an *output sequence* that is  of a *different length* than the input, and doesn’t align with it in a word-to-word way. ..
>
>... encoder-decoder models are used especially for tasks like **machine translation**, where the input sequence and output sequence can have different lengths  and the mapping between a token in the input and a token in the output can be very *indirect* (in some languages the verb appears at the beginning of the sentence; in other languages at the end).
>
>*Encoder-decoder networks*, sometimes called **sequence-to-sequence networks**, are models capable of generating *contextually appropriate*, *arbitrary length*, output sequences given an input sequence. Encoder-decoder networks have been applied  to a very wide range of applications including 
>- **summarization**, 
>- **question answering**,  and 
>- **dialogue**, 
>- but they are particularly popular for **machine translation**.  
>
>The **key idea** underlying these networks is 
>- the use of an *encoder network* that  takes an input sequence 
>- and creates a *contextualized representation* of it, often called  the **context**. 
>- This representation is then passed to a **decoder** which generates a task-specific output sequence.
>  
>-- [[Speech and Language Processing by Jurafsky]] pp 175  

![[encoder_decoder.png]]

>[!important] Definition
>**Encoder-decoder networks** consist of three conceptual components: 
>1. An **encoder** that accepts an input sequence, $x_{1:n}$, and generates a corresponding sequence of *contextualized representation* $$h_{1:n} = F(x_{1:n}; w)$$
>2. A **context vector**, $c$, which is a function of $h_{1:n}$, and conveys the *essence* of  the input to the *decoder*. $$c = \sigma(h_{1:n})$$
>3. A **decoder**, which accepts $c$ as input and generates an *arbitrary length sequence* of *hidden states* $h_{1:m}$, from which a corresponding sequence of *output states* $y_{1:m}$, can be obtained. $$\left\{\begin{array}{l} h_{t} = H(c, h_{t-1}, y_{t-1};\,v), \\[5pt]  y_{t} = \sigma(h_{t})\end{array}\right.$$
>	- Just as with encoders, decoders can be realized  by any kind of sequence architecture.

- [[Autoregressive Models]]

### RNN

![[encoder_decoder_sequence_sequence.png]]


![[rnn_sequence_one_sequence.png]]

- [[Recurrent Neural Network]]
- [[Gated Recurrent Units in Neural Network]]
- [[Long-Short Term Memory Network or LSTM]]
- [[Residual Neural Network]]
- [[Bidirectional Recurrent Neural Network]]
- [[Autoregressive Models]]

- [[Sequence Classification and Sequence-Pair Classification]]
- [[Sequence Labeling Task]]

![[sequence_to_sequence_nlp.png]]



### Auto-Encoder

- [[Variational Auto-Encoder or VAE]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]


### Diffusion Network

![[diffusion_network_ddpm.png]]

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]
- [[Continuous-Time Diffusion Network via Stochastic Differential Equations]]


### Transformer Network

![[transformer.png]]

- [[Transformer Network]]
- [[Large Language Model and Pretrained Language Models]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Generative Pre-trained Transformer or GPT]]
- [[Text-to-Text Transfer Transformer or T5 for Translation]]

![[sequence_to_sequence_transformer.png]]


## Explanation


- [[Linear Dynamic System]]



-----------
##  Recommended Notes and References






- [[Deep Learning by Goodfellow]] pp 383 - 384
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] 
- [[Speech and Language Processing by Jurafsky]] pp 174 - 179