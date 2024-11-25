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
name: Beam Search for Causal Decoding of Language Model
date of note: 2024-11-24
---

## Concept Definition

>[!important]
>**Name**: Beam Search for Causal Decoding of Language Model

### Greedy Decoding

>[!important] Definition
>The task of **greedy decoding** is to *generate* a new sample at each iteration $t \in T$ given *history* based on the *highest conditional likelihood* at $t$
>$$
>\hat{w}_{t} = \arg\max_{w\in \mathcal{V}}\;p(w\,|\,w_{<t}) = \arg\max_{w\in \mathcal{V}}\;p(w\,|\,w_{t-1}\,{,}\ldots{,}\,w_{1})
>$$ 
>where $\mathcal{V}$ is the vocabulary set.

>[!quote]
>A problem with **greedy decoding** is that what looks *high probability* at word $t$ might  turn out to have been the *wrong choice* once we get to word $t + 1$.
>
>-- [[Speech and Language Processing by Jurafsky]] pp 274

- [[Greedy Decoding for Causal Language Model Generation]]

### Beam Search via Breadth-First-Search

>[!important] Definition
>*Beam search* uses **breadth-first search** to build its [search tree](https://en.wikipedia.org/wiki/Tree_traversal "Tree traversal"). 
>- At each level of the tree, it generates all *successors* of the states at the *current level*, *sorting* them in increasing order of heuristic cost.
>- However, it only stores a *predetermined number*, $\beta$, of best states at each level (called the **beam width**). 
>	- Only those states are expanded next. 
>	- The greater the beam width, the fewer states are pruned.

- [[Breadth-First Search]]

![[beam_search_tree.png]]

### Beam Search in LLM

>[!important] Definition
>The **beam search** algorithm improves over the *greedy decoding* for LLM in following way
>- The *beam search algorithm* maintains a set of $\beta$ candidate hypothesis, $$C_{t} := \{ \hat{w}_{1:t-1}^{(1)} \,{,}\ldots{,}\, \hat{w}_{1:t-1}^{(\beta)} \}$$  where $\beta$ is called the **beam width.**
>	- Each candidate hypothesis consists of a sequence of tokens $\hat{w}_{1:t-1}^{(j)}$ up to step $t-1$.
>
>- Then these sequences are fed through the network to obtain $$p(\hat{w} | \hat{w}_{<t})$$ 
>- For each sequence $\hat{w}_{1:t}^{(j)}$, we find the $\beta$ *most probable token values* $$\{ \hat{w}_{t}^{(j, 1)} \,{,}\ldots{,}\,  \hat{w}_{t}^{(j, \beta)}:\; p(\hat{w}_{t}^{(j, 1)}\;|\;\hat{w}_{1:t-1}^{(j)}) \,{\ge}\ldots{\ge}\,p(\hat{w}_{t}^{(j, \beta)}\;|\;\hat{w}_{1:t-1}^{(j)}) \}$$
>	- There are $\beta^{2}$ *extended sequence* $$\hat{w}_{<t+1}^{i,j} := (\hat{w}_{t}^{(j, i)},\, \hat{w}_{t-1}^{(j)} \,{,}\ldots{,}\,\hat{w}_{1}^{(j)}),\quad i=1\,{,}\ldots{,}\,\beta,\; j=1\,{,}\ldots{,}\,\beta$$
>- *Prune* the list with the $\beta$ *most probable hypotheses* $C_{t+1}$ based on the *total probability of extended sequence* $$C_{t+1} := \left\{\hat{w}_{<t+1}^{i,j}\,: \; p(\hat{w}_{<t+1}^{i,j}) \ge p^{(\beta)}(w_{t}\,{,}\ldots{,}\,w_{1})  \right\} $$ 

- [[Large Language Model and Pretrained Language Models]]


>[!quote]
>Because the probability of a sequence is obtained by multiplying the probabilities at each step of the sequence and since these probability are always less than or equal to one, a long sequence will generally have a *lower probability* than a *short one*, **biasing** the results towards **short sequences**. 
>
>For this reason the sequence probabilities are generally **normalized** by the corresponding *lengths of the sequence* before making comparisons. 
>
>Beam search has cost $$O(\beta\,|\mathcal{V}|\,T ),$$ 
>- which is again **linear** in the *sequence length*. 
>- However, the **cost** of generating a sequence is **increased** by a factor of $\beta$, 
>- and so for very large language models, where the **cost of inference** can become significant, this makes *beam search much less attractive*.
>  
>  
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 386  


## Explanation

>[!important]
>The **beam search algorithm** maintains multiple choices *until later* when we can see which one is best.



>[!info]
>A *beam width* of $1$ corresponds to a **hill climbing.**

- [[Greedy Search and Hill Climbing]]

>[!info]
>In contrary to the **greedy decoding**, we can use *dynamic programming algorithm* such as  **Viterbi algorithm**. 

- [[Dynamic Programming Algorithms]]
- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]

>[!important]
>Both **greedy decoding** and **beam search** corresponds to the **autoregressive generation** as it generate *next token* based on *previous generated tokens*.

- [[Autoregressive Models]]
- [[Decoding and Sampling from Large Language Models]]


## Alternative Inference Method via Sampling

- [[Top-k Sampling for Large Language Model Generation]]
- [[Top-p Sampling or Nucleus Sampling for Large Language Model Generation]]
- [[Temperature Sampling for Large Language Model Generation]]





-----------
##  Recommended Notes and References


- [[Tabu Search]]


- [[Speech and Language Processing by Jurafsky]] pp 206, 274 - 277
- [[Deep Learning Foundations and Concepts by Bishop]]  pp 386
- Wikipedia [Beam_search](https://en.wikipedia.org/wiki/Beam_search)