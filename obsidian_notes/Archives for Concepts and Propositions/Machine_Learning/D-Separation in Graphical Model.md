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
name: D-Separation in Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: D-Separation in Graphical Model

>[!important] Definition
>Let $\mathcal{G}$ be a *Bayesian network* structure, and $$X_{1}e_{1}\cdots X_{n-1}e_{n-1}X_{n}$$ be a *trail* in $\mathcal{G}$, 
>- where $e_{i} := (X_{i}, X_{i+1})$ is a directed edge (either $X_{i} \to X_{i+1}$ or $X_{i} \leftarrow X_{i+1}$). 
>  
>Let $Z$ be a subset of *observed variables*. The trail $X_{1}e_{1}\cdots e_{n-1}X_{n}$ is **active** given $Z$ if
>- whenever there exists a **$v$-structure** $$X_{i-1} \rightarrow X_{i} \leftarrow X_{i+1},$$ then *$X_{i}$* or *one* of its *descendants* are in $Z$;
>- and *no* other node *along the trail* is in $Z$.

^c42526

- [[Walk and Trail in Graph]]

>[!important] Definition
>Let $\mathcal{X}, \mathcal{Y}, \mathcal{Z}$ be three sets of nodes in $\mathcal{G}$. 
>
>We say that $\mathcal{X}$ and $\mathcal{Y}$ are **d-separated** *given* $\mathcal{Z}$, denoted as $$d\text{-sep}_{\mathcal{G}}\left(\mathcal{X};  \mathcal{Y} \,|\, \mathcal{Z}\right)$$ if there is *no active trails* between any two nodes $X\in \mathcal{X}$, and $Y \in \mathcal{Y}$ given $\mathcal{Z}$. 

^ede428


>[!important] Definition
>We use $\mathcal{I}(\mathcal{G})$ to denote the set of independencies that correspond to **d-separation**:
>$$
>\mathcal{I}(\mathcal{G}) := \left\{ (\mathcal{X} \perp \mathcal{Y} \,|\, \mathcal{Z}):\; \text{d-sep}_{\mathcal{G}}(\mathcal{X}; \mathcal{Y} \,|\, \mathcal{Z}) \right\}. 
>$$
>This set is also called the set of **global Markov independencies**.

- [[I-Map and Independence Assertion]]
- [[Conditional Independence]]


## Explanation

>[!info]
>We see that $\mathcal{X}$ and $\mathcal{Y}$ are **d-separated** *given* $\mathcal{Z}$ if
>- either $\mathcal{Z}$ **separates** $\mathcal{X}$ and $\mathcal{Y}$ in graph $\mathcal{G}$.
>- or there exists a **common effect structure** where the **effect** or its **descendant** is **observed**.

- [[Separation of Graph]]

## Soundness and Faithfulness of D-Separation

- [[Soundness and Faithfulness of D-Separation]]


-----------
##  Recommended Notes and References

- [[Separation of Graph]]
- [[I-Map and Independence Assertion]]
- [[Conditional Independence]]
- [[Bayesian Network on Directed Acyclic Graph]]


- [[Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 69
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 562 - 564