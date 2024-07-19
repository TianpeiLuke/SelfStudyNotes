---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/theory
keywords:
  - separation_graphical_model
  - markov_network
topics:
  - probabilistic_graphical_model
name: D-Separation in Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Separation in Markov Network

### Active Trail and Separation in Markov Network

>[!important] Definition
>Let $\mathcal{H}$ be a *Markov network* structure, and $$X_{1}e_{1}\cdots X_{n-1}e_{n-1}X_{n}$$ be a *trail* in $\mathcal{G}$, 
>- where $e_{i} := (X_{i}, X_{i+1})$ is an undirected edge. 
>  
>Let $Z$ be a subset of *observed variables*. The trail $X_{1}e_{1}\cdots e_{n-1}X_{n}$ is **active** given $Z$ if
>-  *no* node $X_{i}$ *in the path* is in $Z$.

- [[Walk and Trail in Graph]]
- [[Separation of Graph]]


>[!important] Definition
>Let $\mathcal{H}$ be a *Markov network* structure, and let $\mathcal{X}, \mathcal{Y}, \mathcal{Z}$ be three sets of nodes in $\mathcal{H}$. 
>
>We say that $\mathcal{X}$ and $\mathcal{Y}$ are **separated** *given* $\mathcal{Z}$, denoted as $$\text{sep}_{\mathcal{H}}\left(\mathcal{X};  \mathcal{Y} \,|\, \mathcal{Z}\right)$$ if there is *no active trails* between any two nodes $X\in \mathcal{X}$, and $Y \in \mathcal{Y}$ given $\mathcal{Z}$. 
>

^d1b32f

>[!info]
>For Markov network structure, the concept **separation** is equivalent to **separation** in graph theory

>[!important] Definition
>We use $\mathcal{I}(\mathcal{H})$ to denote the set of independencies that correspond to **separation**:
>$$
>\mathcal{I}(\mathcal{H}) := \left\{ (\mathcal{X} \perp \mathcal{Y} \,|\, \mathcal{Z}):\; \text{sep}_{\mathcal{H}}(\mathcal{X}; \mathcal{Y} \,|\, \mathcal{Z}) \right\}. 
>$$
>This set is also called the set of **global Markov independencies** associated with $\mathcal{H}$.

^61905e

## Explanation

>[!info]
>In undirected graph, there is **no common effect structure** ($v$-structure). So the definition of active trail is simply a trail that *does not pass through observed subset* $Z$.


### Monotonic Structure of Separation in Markov Network

>[!quote]
>Note that the definition of separation is **monotonic** in $Z$, that is, if $\text{sep}_{\mathcal{H}}(X; Y | Z)$, then $\text{sep}_{\mathcal{H}}(X; Y | Z')$ for any $Z' \supset Z.$ Thus, if we take **separation** as our *definition of the independencies* induced by the network structure, we are effectively **restricting our ability to encode nonmonotonic independence relations**. Recall that in the context of intercausal reasoning in **Bayesian networks**, *nonmonotonic reasoning patterns* are quite useful in many situations for example, when two diseases are independent, but dependent given some common symptom. The nature of the separation property implies that *such independence patterns* **cannot be expressed** in the structure of a **Markov network**.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 115



## Soundness and Faithfulness of Separation

- [[Soundness and Faithfulness of Separation in Markov Net]]






-----------
##  Recommended Notes and References

- [[D-Separation in Bayesian Network]]

- [[I-Map and Independence Assertion]]
- [[Conditional Independence]]
- [[Markov Network on Undirected Graph]]


- [[Separation of Graph]]
- [[Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 115
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 562 - 564