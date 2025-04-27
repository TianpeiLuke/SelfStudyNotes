---
tags:
  - concept
  - deep_learning/generative_models
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
  - top_p_sampling
  - nucleus_sampling
keywords:
  - top_p_sampling
  - nucleus_sampling
topics:
  - deep_learning/large_language_models
name: Top-p Sampling or Nucleus Sampling for Large Language Model Generation
date of note: 2024-11-24
---

## Concept Definition

>[!important]
>**Name**: Top-p Sampling or Nucleus Sampling for Large Language Model Generation

![[Greedy Decoding for Causal Language Model Generation#^41dfb7]]

- [[Greedy Decoding for Causal Language Model Generation]]

>[!important] Definition
>The **top-p sampling** or **nucleus sampling** keeps not the top $k$ words, but the *top $p$ percentage* of the *probability mass*.
>
>The **top-p sampling** is described by the following steps:
>- *Require*: a *language model*   $p(w_{t}\;|\;w_{t-1}\,{,}\ldots{,}\,w_{1})$ for all $t$
>- *Require*: the *vocabulary set* $\mathcal{V}$
>- *Require*: the sampling parameter $p$
>- For $t=1\,{,}\ldots{,}\,T$
>	- Collect the words in *context* $$w_{<t} := (w_{t-1}\,,w_{t-2} \,{,}\ldots{,}\,)$$
>	- For each word $w\in \mathcal{V}$
>		- Compute the likelihood of this word *given the context* $$p_{t}(w) := p(w\;|\;w_{<t})$$
>	- **Sort** the words by their **likelihood** $$p_{t}(w^{(1)}) \ge p_{t}(w^{(2)}) \,{\ge}\ldots{\ge}\,$$
>	- Select the **top-p vocabulary set** $$V^{(p)} := \{ w^{(1)} \,{,}\ldots{,}\, w^{(m^{*})}\}$$ as the *smallest set* of words such that $$\begin{align*}V^{(p)} &:= \arg\min_{V}\left\{|V|:\; \sum_{w \in V }p(w\;|\;w_{<t}) \ge p \right\} \\[7pt] \iff m^{*} &=\arg\min_{m}\left\{ m\in \mathbb{N}:\; \sum_{j=1}^{m}p(w^{(j)}\;|\;w_{<t}) \ge p \right\}  \end{align*}$$
>	- **Normalize the score** of $m^{*}$ words so that it is a discrete distribution $$\hat{p}_{t}(i) := \frac{p_{t}(w^{(i)})}{\sum_{w^{(j)} \in \mathcal{V}^{(p)} }p_{t}(w^{(j)})}, \quad i=1\,{,}\ldots{,}\,m^{*}$$
>	- **Randomly sample** words $w_{t}$ according to $\hat{p}_{t}(i)$, i.e. $$w_{t} \in V^{(p)} \sim \hat{p}_{t}(i).$$
>	- Expand the context as $$w_{<t+1} := \{ w_{t}\,, w_{t-1}\,,w_{t-2} \,{,}\ldots{,}\,\}$$


- [[Generative Pre-trained Transformer or GPT]]
- [[Large Language Model and Pretrained Language Models]]
- [[Decoding and Sampling from Large Language Models]]


## Explanation

>[!quote]
>by *measuring probability* rather than the number of words, the hope is that the  measure will be **more robust** in very *different contexts*, **dynamically** *increasing* and  *decreasing* the pool of word candidates.
>
>-- [[Speech and Language Processing by Jurafsky]] pp 209


>[!info]
>The **top-p selection** is very close to 
>- the **truncation method** 
>- and the **fitness proportional selection** 
>
>in the **parent selection** in **evalutionary computation** where the *fitness function* is defined as the likelihood given context.

- [[Parent Selection for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]


## Other Variants

- [[Top-k Sampling for Large Language Model Generation]]




-----------
##  Recommended Notes and References

- [[Top-k Sampling for Large Language Model Generation]]

- [[Gibbs Sampling for Graphical Model]]
- [[Artificial Neural Network and Deep Learning]]

- [[Speech and Language Processing by Jurafsky]] pp 209
- [[Deep Learning Foundations and Concepts by Bishop]] pp 386 - 387
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]