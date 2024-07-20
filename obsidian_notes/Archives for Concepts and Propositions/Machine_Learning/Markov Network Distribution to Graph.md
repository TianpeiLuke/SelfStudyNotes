---
tags:
  - concept
  - probabilistic_graphical_models/theory
keywords:
  - markov_network
topics:
  - probabilistic_graphical_model
name: Markov Network Distribution to Graph
date of note: 2024-07-19
---

## Concept Definition

>[!important]
>**Name**: Markov Network Distribution to Graph

### Markov Blanket

![[Markov Blanket and Local Markov Independence#^18e7c9]]

![[Markov Blanket and Local Markov Independence#^cc196a]]

>[!important] Theorem
>Let $\mathcal{P}$ be a **positive distribution**, and let $\mathcal{H}$ be defined by introducing an edge $\{ X, Y \}$ for all $X, Y$ for which the following equation holds $$\mathcal{P} \not\vDash \left(X \perp Y\,|\, \mathcal{X} - \{ X, Y \}\right).$$
>
>Then the **Markov network** $\mathcal{H}$ is the **unique minimal $I$-map** for $\mathcal{P}$.

- [[Minimal I-Map]]

>[!important] Theorem
>Let $\mathcal{P}$ be a **positive distribution**.
>
>For each node $X$,  let $\text{MB}_{\mathcal{P}}(X)$ be the **minimal** *set of nodes* $U$ satisfying equation 
>$$\left(X \perp \left(\mathcal{X} - \{ X, U \}\right)\;|\;U\right) \in \mathcal{I}(\mathcal{P}).$$
>
>Then the **Markov network** $\mathcal{H}$ is the **unique minimal $I$-map** for $\mathcal{P}$.

- [[Markov Blanket and Local Markov Independence]]




## Explanation





-----------
##  Recommended Notes and References


- [[Separation in Markov Network]]
- [[Markov Blanket and Local Markov Independence]]
- [[I-Map and Independence Assertion]]
- [[Markov Network on Undirected Graph]]

- [[Bayesian Network Distribution to Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 120