---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
keywords:
  - bayesian_network
  - probabilistic_graphical_model
  - directed_acyclic_graph
topics:
  - machine_learning_models
  - probabilistic_graphical_model
name: Bayesian Network on Directed Acyclic Graph
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Bayesian Network on Directed Acyclic Graph

>[!important] Definition
>A **Bayesian network (BN)** or **Bayes net** or **Belief network** is a *probabilistic graphical model* that represents a set of *variables* and their *conditional independence relation* via a *directed acyclic graph (DAG)*.

### Bayesian Network via Conditional Independence Assumptions


>[!important] Definition
>A **Bayesian network structure** $\mathcal{G}:= (\mathcal{V}, \mathcal{E})$ is a directed acyclic graph whose nodes represent index of *random variables* $X_{1} \,{,}\ldots{,}\,X_{n}$. Let
>-  $Pa(i)$ denote the **parents** of node $i$ in $\mathcal{G}$, and 
>- $\text{NonDescendant}(i)$ denote the variables in the graph that are **not descendant** of node $i$.
>
>Then $\mathcal{G}$ encodes the following set of *conditional independence assumptions*, called the **local dependencies**, and denoted as $\mathcal{I}_{l}(\mathcal{G})$:
>$$
>\mathcal{I}_{l}(\mathcal{G}) = \left\{ (X_{i} \perp X_{\text{NonDescendant}(i)} \;|\; X_{Pa(i)}): i\in \mathcal{V}  \right\} 
>$$
>That is, the *local dependencies* states that each node $X_{i}$ is *conditionally independent* with its *nondescendants* given its *parents*.

- [[I-Map and Independence Assertion]]
- [[Conditional Independence]]
- [[Directed Acyclic Graph]]


### Bayesian Network via Factorized Joint Probability Distribution

>[!important] Definition
>Let $\mathcal{G} := (\mathcal{V}, \mathcal{E})$ be the *directed acyclic graph*, where $\mathcal{V}$ is a node index set and $\mathcal{E} \subset \mathcal{V} \times \mathcal{V}$ consists of directed links $(u,v)$ from $u$ to $v$.  
>
>- The *joint probability density function* $P$ on $(X_{v}, v\in \mathcal{V})$ is said to **factorize according to $\mathcal{G}$** if
>$$
> P(x_{v}\,,\, v\in \mathcal{V}) = \prod_{v\in \mathcal{V}}P(x_{v}\,|\, x_{Pa(v)})
>$$
>where $Pa(v)$ is the index set of all **parent nodes** of $v$ in $\mathcal{G}$   $$Pa(v) = \{ u \in \mathcal{V}: (u, v) \in \mathcal{E} \}.$$
>
>- The equation above is called **the chain rule** of *Bayesian network* and the individual factors $$P(x_{v}\,|\, x_{Pa(v)}), \quad v\in \mathcal{V}$$ are called the **conditional probability density function (C.P.D)** or **local probability models**.
>- A **Bayesian network** is a pair $(\mathcal{G}, P)$ where $P$ *factorizes according to* $\mathcal{G}$, and where $P$ is specified as a set of *CPDs* associated with nodes in $\mathcal{G}$. We denote $P$ as $P_{\mathcal{G}}$.
>

^9d991d


- [[Probabilistic Graphical Models]]
- [[Directed Acyclic Graph]]
- [[Parent Children Descendant Ancestry in Graph]]

## Explanation

>[!quote]
>In *Bayesian network*, the graph $\mathcal{G}$ can be viewed in *two different ways*:
>- as a **data structure** that provides the skeleton for representing a *joint distribution* compactly in a **factorized way**;
>- as a *compact representation* for *a set of* **conditional independence assumptions** about a distribution.
>  
>-- [[Probabilistic Graphical Models by Koller]] pp 51 - 52  


>[!quote]
>A **BN** structure $G$ encodes a set of **conditional independence assumptions**; *every distribution* for which $G$ is an $I$-map must *satisfy these assumptions*. This property is the key to allowing the **compact factorized representation** ...
>
>-- [[Probabilistic Graphical Models by Koller]] pp 61


## Local Probabilistic Models

- [[Local Probabilistic Models]]


## Factorization to I-Map

>[!important] Theorem
>Let $\mathcal{G}$ be a **Bayesian network** over a set of random variables $\mathcal{X}$, and let $\mathcal{P}$ be a *joint distribution* over $\mathcal{X}$. 
>
>If $\mathcal{P}$ **factorizes** according to $\mathcal{P}$, then $\mathcal{G}$ is an **$I$-map** for $\mathcal{P}$, i.e. $$\mathcal{I}(\mathcal{G}) \subseteq \mathcal{I}(\mathcal{P}).$$

- [[I-Map and Independence Assertion]]
- [[Product Measure]]







-----------
##  Recommended Notes and References

- [[Graph]]
- [[Directed Graph]]
- [[Directed Acyclic Graph]]

- [[Markov Network on Undirected Graph]]
- [[Probabilistic Graphical Models]]

- [[Probabilistic Graphical Models by Koller]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning Foundations and Concepts by Bishop]] pp 326
- [[Deep Learning by Goodfellow]] pp 554 - 556
