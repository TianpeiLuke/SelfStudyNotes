---
tags:
  - concept
  - deep_learning/architecture
  - deep_learning/models
  - natural_language_processing/large_language_models
keywords:
  - large_language_models
  - pretrained_language_models
topics:
  - deep_learning/large_language_models
  - deep_learning/generative_models
  - deep_learning/sequential_networks
  - deep_learning/discriminative_models
  - natural_language_processing/large_language_models
name: Large Language Model and Pretrained Language Models
date of note: 2024-10-21
---

## Concept Definition

>[!important]
>**Name**: Large Language Model and Pretrained Language Models


>[!important] Definition
>The goal of a **pre-trained language model** is to *pre-train* on a large corpus of text and then to *fine-tune* the pretrained model for a broad range of *downstream tasks*.

### Encoder-Only Transformer Architecture

>[!important] Definition
>A **encoder-only transformer language model** is a transformer model based on encoders:
>- It corresponds to a **contextual embedding** of words based on its context.
>- The models are trained for a **masked language modeling** task
>	- Instead of predicting the *following word*, we *mask* a word in the *middle* and predict the word given words *on both sides.*

![[causal_and_masked_transformer.png]]

![[causal_and_masked_matrix.png]]

>[!important]
> *Encoder-only architecture* is used in tasks such as
>- **sequence labeling** including
>	- **name entity recognition** [[Name Entity Recognition]]
>	- **part-of-speech tagging** [[Part-of-Speech Tagging]]
>	- **semantic role labeling** [[Semantic Role Labeling]]
>- **text classification** including
>	- **sentiment analysis** [[Sentiment Analysis]]
>	- **topic modeling** [[Topic Models]]

![[bert_architecture.png]]

>[!example]
>The most important *encoder-only* transformer model is **Bidirectional Encoder Representation from Transformer or BERT**

- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[devlinBERTPretrainingDeep2019]]
- [[liuRoBERTaRobustlyOptimized2019]]

### Decoder-Only Transformer Architecture

>[!important] Definition
>A **decoder-only transformer language model** is a transformer model based on decoders:
>- The decoder model is a **autoregressive generative model**.
>- In order to generate texts, we provide an input piece of text called **prompt**, and then the decoder will continue generate text *token by token*, *conditioned* on the prompt.
>- It corresponds to a **conditional generation** of words based on previous words.
>- A *decoder-only transformer model* with *large-scale parameter size* (typically over one billion parameters) is often referred to as the **large language model.**
>- These models are trained using **next word prediction**.

>[!important]
> *Decoder-only architecture* is used in tasks such as
>- **text generation** including
>	- **text summarization** 
>	- **chatbot** and **dialogue generation**
>	- **code generation**
>- **text classification** including
>	- **sentiment analysis** [[Sentiment Analysis]]
>	- **topic modeling** [[Topic Models]]
>- **information retrieval** including
>	- **retrieval augmented generation**


![[gpt_architecture.png]]

>[!example]
>The most important *decoder-only* transformer model is the **Generative Pretrained Transformer (GPT)** series:
>- The **GPT-3** and its instruct fine-tuned version **ChatGPT** opened the new era of LLM in 2020.

- [[Generative Pre-trained Transformer or GPT]]
- [[Autoregressive Models]]
- [[Greedy Decoding for Language Model]]
- [[Beam Search as Greedy Decoding]]




### Encoder-Decoder Transformer Architecture

>[!important] Definition
>A **encoder-decoder transformer language model** is a transformer model based on *encoder-decoders sequence-to-sequence models*:
>- The encoder part of the model provide *contextualized embedding*
>- The decoder part of the model is an *autoregressive generative model*.
>- The embedding is provided to each layer of decoder, with a *cross-attention embedding.*

>[!important]
> *Encoder-decoder architecture* is used in tasks such as
>- **text generation** including
>	- **text summarization** 
>	- **chatbot** and **dialogue generation**
>	- **code generation**
>- **machine translation**

![[transformer.png]]

- [[Text-to-Text Transfer Transformer or T5 for Translation]]
- [[Greedy Decoding for Language Model]]
- [[Beam Search as Greedy Decoding]]

>[!example]
>An important *encoder-decoder* transformer model is the **text-to-text transfer transformer** or **T5 model.**

- [[Text-to-Text Transfer Transformer or T5 for Translation]]


## Explanation




## LLM Generation

- [[Autoregressive or Causal Language Model Generation]]
- [[Top-k Sampling for Large Language Model Generation]]
- [[Top-p Sampling or Nucleus Sampling for Large Language Model Generation]]

## Supervised Fine Tuning and Reinforcement Learning with Human Feedback

- [[Parameter Efficient Fine Tuning or PEFT for Large Language Model]]
- [[Reinforcement Learning with Human Feedbacks or RLHF for LLM]]
- [[Supervised Fine-Tuning vs Reinforcement Learning with Human Feedbacks]]



-----------
##  Recommended Notes and References

- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]
- [[Scaling Law of Large Language Model]]


- [[Encoder-Decoder Sequence-to-Sequence Architecture]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Generative Pre-trained Transformer or GPT]]
- [[Text-to-Text Transfer Transformer or T5 for Translation]]
- [[liuRoBERTaRobustlyOptimized2019]]
- [[touvronLlamaOpenFoundation2023]]

- [[Speech and Language Processing by Jurafsky]] pp 203 - 220, 223
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 390 - 394
- [[Deep Learning Foundations and Concepts by Bishop]] pp 382 - 394