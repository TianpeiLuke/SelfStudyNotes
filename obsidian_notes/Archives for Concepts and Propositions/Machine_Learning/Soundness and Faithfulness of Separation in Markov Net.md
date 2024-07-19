---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/theory
keywords:
  - d_separation_graphical_model
  - conditional_independence
topics:
  - probabilistic_graphical_model
name: Soundness and Faithfulness of Separation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Soundness and Faithfulness of Separation in Markov Network

![[Separation in Markov Network#^d1b32f]]


- [[Separation in Markov Network]]
- [[Walk and Trail in Graph]]

### Soundness 

>[!important] Theorem
>Let $\mathcal{P}$ be a distribution over $\mathcal{X}$, and $\mathcal{H}$ be a **Markov network** over $\mathcal{X}$.
>
>If $\mathcal{P}$ is a Gibbs distribution that **factorizes** over $\mathcal{H}$, then $\mathcal{H}$ is an **$I$-map** for $\mathcal{P}$.
>
>That is, for any three disjoint sets of random variables $X, Y, Z$, 
>$$
> \text{sep}_{\mathcal{H}}(X; Y \,|\, Z) \implies \mathcal{P} \vDash \left(X \perp Y \,|\, Z\right)
>$$

- [[I-Map and Independence Assertion]]
- [[Conditional Independence]]
- [[Double Turnstile]]


### Faithfulness 

>[!important] Theorem
>Let $\mathcal{P}$ be a **positive distribution** over $\mathcal{X}$, and $\mathcal{H}$ be a **Markov network** over $\mathcal{X}$.
>
>If $\mathcal{H}$ is an **$I$-map** for $\mathcal{P}$, then $\mathcal{P}$ is a Gibbs distribution that **factorizes** over $\mathcal{H}$.

- [[Hammersley-Clifford Theorem]]

### Completeness

>[!important] Theorem
>Let $\mathcal{H}$ be a **Markov network** structure. 
>
>If $X$ and $Y$ are **not separated** given $Z$ in $\mathcal{H}$, then $X$ and $Y$ are **dependent** given $Z$ in some distribution $\mathcal{P}$ that **factorizes** over $\mathcal{H}$.






## Explanation




-----------
##  Recommended Notes and References


- [[D-Separation in Bayesian Network]]
- [[Markov Network on Undirected Graph]]


- [[Separation of Graph]]
- [[Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 69
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 562 - 564