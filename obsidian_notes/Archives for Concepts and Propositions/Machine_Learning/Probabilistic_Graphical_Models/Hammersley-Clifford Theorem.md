---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/theory
keywords:
  - hammersley_clifford_theorem
  - markov_network
topics:
  - probabilistic_graphical_model
name: Hammersley-Clifford Theorem
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Hammersley-Clifford Theorem

![[Soundness and Faithfulness of Separation in Markov Net#^6e83aa]]

- [[Soundness and Faithfulness of Separation in Markov Net]]
- [[Separation in Markov Network]]


![[Positive Distribution#^66c0dd]]


>[!important] Hammersley-Clifford Theorem
>Let $\mathcal{P}$ be a **positive** distribution over $\mathcal{X}$ and $\mathcal{H}$ be an undirected graph. 
>
>If $\mathcal{H}$ is an **$I$-map** for $\mathcal{P}$, i.e. 
>$$
>\mathcal{P} \vDash (X \perp Y | Z) \implies \text{sep}_{\mathcal{H}}(X; Y | Z),
>$$
>then $\mathcal{P}$ is a **Gibbs distribution** that **factorizes** over $\mathcal{H}$, i.e.
>$$
> P(X_{v}\,,\, v\in \mathcal{V}) = \frac{1}{Z}\prod_{k=1}^{K}\phi_{k}(X_{D_{k}})
>$$
>where $\left\{ D_{k} \right\}$ is set of the **(maximal) cliques** of graph $\mathcal{H}$.

^1abe0a

- [[Gibbs Distribution]]
- [[Positive Distribution]]

## Explanation

>[!important]
>Unlike for **Bayesian networks**, this direction does not hold in general. As we will show, it holds only under the *additional assumption* that $P$ is a **positive distribution**.

- [[Positive Distribution]]


-----------
##  Recommended Notes and References


- [[Soundness and Faithfulness of Separation in Markov Net]]
- [[Separation in Markov Network]]
- [[Markov Network on Undirected Graph]]


- [[Separation of Graph]]
- [[Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 116
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 166
