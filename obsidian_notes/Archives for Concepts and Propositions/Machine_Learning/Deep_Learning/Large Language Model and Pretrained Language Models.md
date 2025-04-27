---
tags:
  - concept
  - deep_learning/architecture
  - deep_learning/models
  - natural_language_processing/large_language_models
  - large_language_models
  - pretrained_language_models
  - masked_language_models
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

### Encoder-Only Architecture or Masked Language Model

>[!important] Definition
>A **encoder-only transformer language model** is a transformer model based on encoders:
>- It corresponds to a **contextual embedding** of words based on its context.
>- The models are trained for a **masked language modeling** task
>	- Instead of predicting the *following word*, we *mask* a word in the *middle* and predict the word given words *on both sides.*
>- The *encoder-only transformer language model* is also called the **masked language model.**

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
- [[Sentence-BERT for Sentence Embedding]]

### Decoder-Only Architecture or Autoregressive Language Models

>[!important] Definition
>A **decoder-only transformer language model** is a transformer model based on decoders:
>- The decoder models are **autoregressive language models**.
>- In order to generate texts, we provide an input piece of text called **prompt**, and then the decoder will continue generate text *token by token*, *conditioned* on the prompt.
>- It corresponds to a **conditional generation** of words based on previous words.
>- A *decoder-only transformer model* with *large-scale parameter size* (typically over one billion parameters) is often referred to as the **large language model.**
>- These models are trained using **next word prediction**.

^2f4e77

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
- [[Greedy Decoding for Causal Language Model Generation]]
- [[Beam Search for Causal Decoding of Language Model]]




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
- [[Greedy Decoding for Causal Language Model Generation]]
- [[Beam Search for Causal Decoding of Language Model]]

>[!example]
>An important *encoder-decoder* transformer model is the **text-to-text transfer transformer** or **T5 model.**

- [[Text-to-Text Transfer Transformer or T5 for Translation]]


## Explanation

![[llm_components.png]]

- Minaee, S., Mikolov, T., Nikzad, N., Chenaghlu, M., Socher, R., Amatriain, X., & Gao, J. (2024). Large language models: A survey. _arXiv preprint arXiv:2402.06196_.


## Self-Supervised Training 

- [[Self-Supervised Training of Large Language Model and Teacher Forcing]]
- [[Self-Supervised Learning]]
- [[Masked Language Modeling as Language Model Training Task]]
- [[Next Sentence Prediction as Language Model Training Task]]


## Text Generation via Decoding and Sampling of LLM

- [[Decoding and Sampling from Large Language Models]]
- [[Greedy Decoding for Causal Language Model Generation]]
- [[Beam Search for Causal Decoding of Language Model]]
- [[Top-k Sampling for Large Language Model Generation]]
- [[Top-p Sampling or Nucleus Sampling for Large Language Model Generation]]
- [[Temperature Sampling for Large Language Model Generation]]


## Supervised Fine Tuning and Human Alignment

- [[Parameter Efficient Fine Tuning or PEFT for Large Language Model]]
- [[Reinforcement Learning with Human Feedbacks or RLHF for LLM]]
- [[Direct Preference Optimization for Alignment in LLM]]
- [[Supervised Fine-Tuning or Instruction Fine-Tuning of LLM]]
- [[Supervised Fine-Tuning and Preference Alignment for LLM]]


## Efficient Training and Inference

- [[Zero Redundancy Optimizer or ZeRO for Optimized Training of LLM]]


## Applications from LLM

![[llm_capacity_survey_2024.png]]

- Minaee, S., Mikolov, T., Nikzad, N., Chenaghlu, M., Socher, R., Amatriain, X., & Gao, J. (2024). Large language models: A survey. _arXiv preprint arXiv:2402.06196_.

- [[Information Extraction]]
	- [[Name Entity Recognition]]
	- [[Relation Extraction]]
	- [[Event Extraction]]
- [[Information Retrieval]]


## PLM and LLM Variants

![[llm_timeline_2024.png]]

- Zhao, W. X., Zhou, K., Li, J., Tang, T., Wang, X., Hou, Y., ... & Wen, J. R. (2023). A survey of large language models. _arXiv preprint arXiv:2303.18223_.

![[llm_model_survey_2024.png]]

![[llm_model_survey_timeline_2024.png]]

- [[touvronLlamaOpenFoundation2023]]
- Minaee, S., Mikolov, T., Nikzad, N., Chenaghlu, M., Socher, R., Amatriain, X., & Gao, J. (2024). Large language models: A survey. _arXiv preprint arXiv:2402.06196_.






-----------
##  Recommended Notes and References

- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]
- [[Scaling Law of Large Language Model]]
- [[Pre-Training and Fine-Tuning Paradigm for Transfer Learning]]


- [[Encoder-Decoder Sequence-to-Sequence Architecture]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Generative Pre-trained Transformer or GPT]]
- [[Text-to-Text Transfer Transformer or T5 for Translation]]
- [[liuRoBERTaRobustlyOptimized2019]]
- [[touvronLlamaOpenFoundation2023]]

- [[Speech and Language Processing by Jurafsky]] pp 203 - 220, 223
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 815 - 816, 880
- [[Deep Learning Foundations and Concepts by Bishop]] pp 382 - 394



- Zhao, W. X., Zhou, K., Li, J., Tang, T., Wang, X., Hou, Y., ... & Wen, J. R. (2023). A survey of large language models. _arXiv preprint arXiv:2303.18223_.
- Min, B., Ross, H., Sulem, E., Veyseh, A. P. B., Nguyen, T. H., Sainz, O., ... & Roth, D. (2023). Recent advances in natural language processing via large pre-trained language models: A survey. _ACM Computing Surveys_, _56_(2), 1-40.