---
tags:
  - concept
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
  - deep_learning/generative_models
keywords:
  - autoregressive_language_model
  - causal_language_model
  - text_generation
  - beam_search
  - top_p_sampling
  - top_k_sampling
  - temperature_sampling
topics:
  - natural_language_processing/large_language_models
  - deep_learning/generative_models
  - deep_learning/large_language_models
name: Decoding and Sampling from Large Language Models
date of note: 2024-11-25
---

## Concept Definition

>[!important]
>**Name**: Decoding and Sampling from Large Language Models

![[Large Language Model and Pretrained Language Models#^2f4e77]]

- [[Large Language Model and Pretrained Language Models]]
- [[Generative Pre-trained Transformer or GPT]]
- [[Text-to-Text Transfer Transformer or T5 for Translation]]

>[!important] Definition
>The core of the *generation process* for large language models is the task of choosing  the single word to generate next based on the *context* and based on the *probabilities*  that the model assigns to possible words. 
>
>- This task of *choosing* a word to generate  based on the *model’s probabilities* is called **decoding**.

- [[Max-Product Variable Elimination]]
- [[Max-Product Belief Propagation for Clique Tree]]
- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]

### Decoding-based Text Generation

>[!important] Definition
>Given probability assignments from language model $p(w|w_{t-1} \,{,}\ldots{,}\,w_{1})$,  the task of **decoding** is to choose a sequence of tokens $$(\hat{w}_{t} \,{,}\ldots{,}\,\hat{w}_{t-k}) \in \arg\max p(w_{t} \,{,}\ldots{,}\,w_{t-k})$$
>
>
>The process of *decoding* is *sequential*, where we choose the *next word* conditioned *previous choices*.
>- This process is called the **autoregressive generation**; or **causal language model generation.**

- [[Greedy Decoding for Causal Language Model Generation]]
- [[Beam Search for Causal Decoding of Language Model]]
- [[Autoregressive Models]]


### Sampling-based Text Generation

>[!important] Definition
>The **sampling method** choose a *random word* based on their assigned probability from model.
>- The direct method is the **random sampling** $$w_{t} \sim p(w|\;w_{t-1}\,{,}\ldots{,}\,w_{1})$$
>	- This method has challenges since it may generate words in the *tails of distribution.*
>- Instead, the most commonly used sampling method emphasize two most *important __tradeoff__ factors*: 
>	- **quality**, and
>	- **diversity**


- [[Top-k Sampling for Large Language Model Generation]]
- [[Top-p Sampling or Nucleus Sampling for Large Language Model Generation]]
- [[Temperature Sampling for Large Language Model Generation]]

>[!quote]
>The sampling methods we introduce below each have parameters that enable  **trading off** two important factors in generation: **quality** and **diversity**. 
>- Methods  that emphasize the **most probable words** tend to produce generations that are rated  by people as *more accurate*, more *coherent*, and more *factual*, but also more *boring*  and more *repetitive*. 
>- Methods that give a bit more weight to the **middle-probability words** tend to be more *creative* and more *diverse*, but less *factual* and more likely to  be *incoherent* or otherwise *low-quality*.
>  
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 208  

## Explanation





-----------
##  Recommended Notes and References


- [[Speech and Language Processing by Jurafsky]] pp 207
- [[Deep Learning Foundations and Concepts by Bishop]] pp 206 - 210