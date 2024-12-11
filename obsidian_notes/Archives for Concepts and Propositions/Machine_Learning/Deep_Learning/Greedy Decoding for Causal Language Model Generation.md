---
tags:
  - concept
  - natural_language_processing/large_language_models
  - probabilistic_graphical_models/inference
  - algorithm/search
  - algorithm/stochastic_search
keywords:
  - beam_search
  - greedy_decoding
topics:
  - algorithm/search
  - natural_language_processing/large_language_models
  - probabilistic_graphical_model
name: Greedy Decoding for Language Model
date of note: 2024-11-24
---

## Concept Definition

>[!important]
>**Name**: Greedy Decoding for Language Model

>[!important] Definition
>Let $$p(w_{t}\;|\;w_{t-1}\,{,}\ldots{,}\,w_{1})$$ be a language model.
>
>The task of **greedy decoding** is to *generate* a new sample at each iteration $t \in T$ given *history* based on the *highest conditional likelihood* at $t$
>$$
>\hat{w}_{t} = \arg\max_{w\in \mathcal{V}}\;p(w\,|\,w_{<t}) = \arg\max_{w\in \mathcal{V}}\;p(w\,|\,w_{t-1}\,{,}\ldots{,}\,w_{1})
>$$ 
>where $\mathcal{V}$ is the vocabulary set.
>- The **greedy decoding** is an **autoregressive generation** process.

^41dfb7

- [[Greedy Heuristic Algorithms]]

>[!quote]
>A problem with **greedy decoding** is that what looks *high probability* at word $t$ might  turn out to have been the *wrong choice* once we get to word $t + 1$.
>
>-- [[Speech and Language Processing by Jurafsky]] pp 274

- [[Autoregressive Models]]
- [[n-Gram Model and Language Model]]



## Explanation


>[!info]
>A *beam width* of $1$ corresponds to a **hill climbing.**

- [[Greedy Search and Hill Climbing]]

>[!important]
>Both **greedy decoding** and **beam search** corresponds to the **autoregressive generation** as it generate *next token* based on *previous generated tokens*.

- [[Decoding and Sampling from Large Language Models]]



-----------
##  Recommended Notes and References


- [[Greedy Heuristic Algorithms]]


- [[Speech and Language Processing by Jurafsky]] pp 206, 274 - 277
- Wikipedia [Beam_search](https://en.wikipedia.org/wiki/Beam_search)