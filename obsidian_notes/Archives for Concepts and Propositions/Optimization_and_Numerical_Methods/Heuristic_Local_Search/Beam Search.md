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
name: Beam Search
date of note: 2024-11-24
---

## Concept Definition

>[!important]
>**Name**: Beam Search

### Greedy Decoding

>[!important] Definition
>The task of **greedy decoding** is to *generate* a new sample at each iteration $t \in T$ given *history* based on the *highest conditional likelihood* at $t$
>$$
>\hat{w}_{t} = \arg\max_{w\in \mathcal{V}}\;p(w\,|\,w_{<t}) = \arg\max_{w\in \mathcal{V}}\;p(w\,|\,w_{t-1}\,{,}\ldots{,}\,w_{1})
>$$ 
>where $\mathcal{V}$ is the vocabulary set.

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

- [[Beam Search for Causal Decoding of Language Model]]

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


-----------
##  Recommended Notes and References


- [[Tabu Search]]


- [[Artificial Intelligence Modern Approach by Russell]] pp 125, 174
- [[Speech and Language Processing by Jurafsky]] pp 206, 274 - 277
- [[Deep Learning Foundations and Concepts by Bishop]]  pp 386
- [[Probabilistic Graphical Models by Koller]] pp 595, 675, 685, 693, 1158
- Wikipedia [Beam_search](https://en.wikipedia.org/wiki/Beam_search)