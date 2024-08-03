---
tags:
  - concept
  - math/probability
  - machine_learning/models
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/theory
keywords:
  - gibbs_distribution
topics:
  - probability
  - machine_learning_models
  - probabilistic_graphical_model
name: Gibbs Distribution
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Gibbs Distribution

>[!important] Definition
>A distribution $\mathcal{P}_{\Phi}$ is called a **Gibbs distribution** *parameterized* by a set of *factors* $$\Phi = \left\{ \phi_{i}(D_{i}),\, i=1\,{,}\ldots{,}\,k \right\},$$ if it is defined as follows:
>$$
>\mathcal{P}_{\Phi}= \frac{1}{Z}\hat{\mathcal{P}}_{\Phi} := \frac{1}{Z}\prod_{i=1}^{k}\phi(D_{i})
>$$ 
>where
>- the **unnormalized measure** is defined as $$\hat{\mathcal{P}}_{\Phi} := \prod_{i=1}^{k}\phi(D_{i})$$
>- and the **partition function** is defined as $$Z = \sum_{x\in \mathcal{X}}\hat{\mathcal{P}}_{\Phi}(x)$$

^ea2e18

- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Probability Distribution of Random Variable]]
- [[Markov Network on Undirected Graph]]


## Explanation



-----------
##  Recommended Notes and References



- [[Restricted Boltzmann Machine]]
- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- [[Probability Space]]


- [[Gibbs measure]]
- [[Probabilistic Graphical Models by Koller]] pp 108

- Wikipedia [Gibbs measure](https://en.wikipedia.org/wiki/Gibbs_measure)