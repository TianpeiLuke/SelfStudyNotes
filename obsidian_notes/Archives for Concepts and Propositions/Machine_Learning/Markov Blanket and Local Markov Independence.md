---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/theory
keywords:
  - markov_blanket
  - local_independence
topics:
  - probabilistic_graphical_model
name: Markov Blanket and Local Independence Assertion
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Markov Blanket and Local Independence Assertion

![[I-Map and Independence Assertion#^775ffa]]

### Pairwise Independent Assumptions

>[!important] Definition
>Let $\mathcal{H}$ be a *Markov network*. 
>
>We define the **pairwise independencies** *associated with* $\mathcal{H}$ to be 
>$$
>\mathcal{I}_{p}(\mathcal{H}) := \left\{ (X \perp Y \,|\, \mathcal{X} - \{ X, Y \}): \;\; X\text{-}Y\text{ path} \not\in \mathcal{H} \right\} 
>$$

^cc196a

- [[I-Map and Independence Assertion]]
- [[Conditional Independence]]
- [[Paths in Graph and Length of Path]]

### Markov Blanket 

>[!important] Definition (graph-based)
>For a given graph $\mathcal{H}$, we define the **Markov blanket** of $X$ *in* $\mathcal{H}$, denoted as $$\text{MB}_{\mathcal{H}}(X),$$ to be the *neighbors of* $X$ in $\mathcal{H}$.

>[!important] Definition (distribution-based)
>A set $U$ is a **Markov blanket** of $X$ *in a distribution* $\mathcal{P}$ if 
>- $X \in U$
>- $U$ is a *minimal set* of nodes such that $$\left(X \perp \left(\mathcal{X} - \{ X, U \}\right)\;|\;U\right) \in \mathcal{I}(\mathcal{P}).$$
>
>We denote this minimal set $U$ as $\text{MB}_{\mathcal{P}}(X)$.

^18e7c9

- [[Minimal and Maximal Property of Graph]]

### Local Independent Assumptions

>[!important] Definition
>For a given graph $\mathcal{H}$, we define the **local independencies** *associated with* $\mathcal{H}$ to be 
>$$\mathcal{I}_{\ell}(\mathcal{H}) := \left\{ \left(X \perp \mathcal{X} - \{ X,\, \text{MB}_{\mathcal{H}}(X) \}\;|\;\text{MB}_{\mathcal{H}}(X)\right):\; X \in \mathcal{X} \right\} $$
>
>In other words, the local independencies state that $X$ is *independent* of the *rest of the nodes* in the graph *given its immediate neighbors*.



### Relations

>[!important] Proposition
>For any **Markov network**  $\mathcal{H}$, and any distribution $\mathcal{P}$
>
>The **local independency property** leads to **pairwise independency property**, i.e.  $$\left(\mathcal{P} \vDash \mathcal{I}_{\ell}(\mathcal{H})\right) \implies \left(\mathcal{P} \vDash \mathcal{I}_{p}(\mathcal{H})\right).$$


>[!important] Proposition
>For any **Markov network**  $\mathcal{H}$, and any distribution $\mathcal{P}$
>
>The **(global) independency property** leads to **local independency property**, i.e.  $$\left(\mathcal{P} \vDash \mathcal{I}(\mathcal{H})\right) \implies \left(\mathcal{P} \vDash \mathcal{I}_{\ell}(\mathcal{H})\right).$$

>[!important] Theorem
>Let $\mathcal{P}$ be a **positive distribution**. 
>
>If $\mathcal{P}$ satisfies the **pairwise independency property**, then $\mathcal{P}$ satisfies the **(global) independency property**, i.e.  $$\left(\mathcal{P} \vDash \mathcal{I}_{p}(\mathcal{H})\right) \implies \left(\mathcal{P} \vDash \mathcal{I}(\mathcal{H})\right).$$ 
>or equivalently
>$$\text{sep}_{\mathcal{H}}(X; Y \,|\, Z) \implies \left( \mathcal{P} \vDash (X \perp Y\,|\,Z)\right)$$



## Explanation




-----------
##  Recommended Notes and References


- [[I-Map and Independence Assertion]]
- [[Separation in Markov Network]]
- [[Markov Network on Undirected Graph]]


- [[Separation of Graph]]
- [[Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 69
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 562 - 564