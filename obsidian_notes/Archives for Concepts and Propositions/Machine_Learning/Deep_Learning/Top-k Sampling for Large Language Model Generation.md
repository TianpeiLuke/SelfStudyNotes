---
tags:
  - concept
  - deep_learning/generative_models
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
keywords: 
topics: 
name: 
date of note: 2024-11-24
---

## Concept Definition

>[!important]
>**Name**: Top-k Sampling for Large Language Model Generation

![[Greedy Decoding for Causal Language Model Generation#^41dfb7]]

>[!important] Definition
>Let $$p(w_{t}\;|\;w_{t-1}\,{,}\ldots{,}\,w_{1})$$ be a language model (such as LLM).
>
>The **top-k sampling** is a simple generalization of the *greedy decoding*. 
>- Instead of choosing the single highest probable token, the **top-k sampling** choose *top k most probable tokens* to generate $$\{ \hat{w}_{t}^{(1)} \,{,}\ldots{,}\, \hat{w}_{t}^{(k)}\} \implies p(\hat{w}_{t}^{(1)} \;|\;w_{t-1}\,{,}\ldots{,}\,w_{1}) \,{\ge}\ldots{\ge}\,p(\hat{w}_{t}^{(k)} \;|\;w_{t-1}\,{,}\ldots{,}\,w_{1})\, \ge p(\hat{w}_{t}^{(k+1)} \;|\;w_{t-1}\,{,}\ldots{,}\,w_{1})  $$
>  
>More formally, it is described by the following steps
>- *Require*: a *language model*   $p(w_{t}\;|\;w_{t-1}\,{,}\ldots{,}\,w_{1})$ for all $t$
>- *Require*: the *vocabulary set* $\mathcal{V}$
>- *Require*: the sampling parameter $k$
>- For $t=1\,{,}\ldots{,}\,T$
>	- Collect the words in *context* $$w_{<t} := (w_{t-1}\,,w_{t-2} \,{,}\ldots{,}\,)$$
>	- For each word $w\in \mathcal{V}$
>		- Compute the likelihood of this word *given the context* $$p_{t}(w) := p(w\;|\;w_{<t})$$
>	- **Sort** the words by their **likelihood** $$p_{t}(w^{(1)}) \ge p_{t}(w^{(2)}) \,{\ge}\ldots{\ge}\,$$
>	- Keep only the **top k words** $$V := \{ w^{(1)} \,{,}\ldots{,}\, w^{(k)}\} \subset \mathcal{V}$$
>	- **Normalize the score** of $k$ words so that it is a discrete distribution $$\hat{p}_{t}(i) := \frac{p_{t}(w^{(i)})}{\sum_{j=1}^{k}p_{t}(w^{(j)})}, \quad i=1\,{,}\ldots{,}\,k$$
>	- **Randomly sample** words $w_{t}$ according to $\hat{p}_{t}(i)$, i.e. $$w_{t} \in V \sim \hat{p}_{t}(i).$$
>	- Expand the context as $$w_{<t+1} := \{ w_{t}\,, w_{t-1}\,,w_{t-2} \,{,}\ldots{,}\,\}$$

- [[Greedy Decoding for Causal Language Model Generation]]
- [[Decoding and Sampling from Large Language Models]]
- [[Large Language Model and Pretrained Language Models]]

## Explanation

>[!info]
>If $k=1$, the **top-1 sampling** is the **greedy decoding.**


>[!info]
>The **top-k selection** is very close to 
>- the **truncation method** 
>- and the **fitness proportional selection** 
>
>in the **parent selection** in **evalutionary computation** where the *fitness function* is defined as the likelihood given context.

- [[Parent Selection for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]

>[!quote]
>One **problem** with *top-k sampling* is that $k$ is **fixed**, but the shape of the *probability  distribution* over words *differs in different contexts*. 
>- If we set $k = 10$, sometimes  the top $10$ words will be very likely and include most of the probability mass, but  other times the probability distribution will be *flatter* and the top $10$ words will only  include a *small part* of the *probability mass*.
>  
>  
>-- [[Speech and Language Processing by Jurafsky]] pp 209  


## Other Variants of Sampling

- [[Top-p Sampling or Nucleus Sampling for Large Language Model Generation]]
- [[Temperature Sampling for Large Language Model Generation]]


-----------
##  Recommended Notes and References


- [[Generative Pre-trained Transformer or GPT]]
- [[Artificial Neural Network and Deep Learning]]

- [[Speech and Language Processing by Jurafsky]] pp 208
- [[Deep Learning Foundations and Concepts by Bishop]] pp 386 - 387
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]