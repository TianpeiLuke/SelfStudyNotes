---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/theory
  - math/probability
keywords:
  - i_map
  - minimal_i_map
topics:
  - probabilistic_graphical_model
name: Minimal I-Map
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Minimal I-Map

>[!important] Definition
>A graph $\mathcal{K}$ is a **minimal $I$-map** for a set of independencies $\mathcal{I}$ if 
>- it is an *$I$-map* for $\mathcal{I}$, i.e. $$\mathcal{I}(\mathcal{K}) \subseteq \mathcal{I}$$
>- and the *removal* of even a single *edge* from $\mathcal{K}$ renders it *not an $I$-map*, i.e. $$(\forall e \in \mathcal{K}),\; \mathcal{I}\left(\mathcal{K} - e\right) \not\subseteq \mathcal{I}.$$

^665356

- [[Conditional Independence]]
- [[I-Map and Independence Assertion]]
- [[Graph Operations and Subgraph]]
- [[Minimal and Maximal Property of Graph]]


## Explanation


## Minimal I-Map for Bayesian Network



## Minimal I-map for Markov Network

![[Markov Blanket and Local Markov Independence#^18e7c9]]

- [[Markov Blanket and Local Markov Independence]]



-----------
##  Recommended Notes and References



- [[D-Separation in Bayesian Network]]
- [[Conditional Independence]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[Independent Random Variables]]


- [[Graph Property]]
- [[Graph]]
- [[Probabilistic Graphical Models]]


- [[Probabilistic Graphical Models by Koller]] pp 60, 121
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
