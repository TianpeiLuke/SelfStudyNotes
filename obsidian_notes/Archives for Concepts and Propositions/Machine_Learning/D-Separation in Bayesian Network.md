---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/theory
keywords:
  - d_separation_graphical_model
  - conditional_independence
  - bayesian_network
topics:
  - probabilistic_graphical_model
name: D-Separation in Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: D-Separation in Bayesian Network

### Active Trail and D-Separation in Bayesian Network

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
>Let $\mathcal{G}$ be a *Bayesian network* structure, and let $\mathcal{X}, \mathcal{Y}, \mathcal{Z}$ be three sets of nodes in $\mathcal{G}$. 
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

### Active Trail and D-Separation in Markov Network

>[!important] Definition
>Let $\mathcal{G}$ be a *Markov network* structure, and $$X_{1}e_{1}\cdots X_{n-1}e_{n-1}X_{n}$$ be a *trail* in $\mathcal{G}$, 
>- where $e_{i} := (X_{i}, X_{i+1})$ is an undirected edge. 
>  
>Let $Z$ be a subset of *observed variables*. The trail $X_{1}e_{1}\cdots e_{n-1}X_{n}$ is **active** given $Z$ if
>-  *no* node $X_{i}$ *in the path* is in $Z$.

>[!info]
>In undirected graph, there is **no common effect structure** ($v$-structure). So the definition of active trail is simply a trail that *does not pass through observed subset* $Z$.

>[!important] Definition
>Let $\mathcal{G}$ be a *Markov network* structure, and let $\mathcal{X}, \mathcal{Y}, \mathcal{Z}$ be three sets of nodes in $\mathcal{G}$. 
>
>We say that $\mathcal{X}$ and $\mathcal{Y}$ are **separated** *given* $\mathcal{Z}$, denoted as $$d\text{-sep}_{\mathcal{G}}\left(\mathcal{X};  \mathcal{Y} \,|\, \mathcal{Z}\right)$$ if there is *no active trails* between any two nodes $X\in \mathcal{X}$, and $Y \in \mathcal{Y}$ given $\mathcal{Z}$. 
>

>[!info]
>For Markov network structure, the concept **d-separation** is equivalent to **separation** in graph theory

- [[Separation of Graph]]

## Explanation

>[!info]
>We see that $\mathcal{X}$ and $\mathcal{Y}$ are **d-separated** *given* $\mathcal{Z}$ if
>- either $\mathcal{Z}$ **separates** $\mathcal{X}$ and $\mathcal{Y}$ in graph $\mathcal{G}$.
>- or there exists a **common effect structure** where the **effect** or its **descendant** is **observed**.

- [[Separation of Graph]]

### Monotonic Structure of Separation in Markov Network

>[!quote]
>Note that the definition of separation is **monotonic** in $Z$, that is, if $\text{sep}_{H}(X; Y | Z)$, then $\text{sep}_{H}(X; Y | Z')$ for any $Z' \supset Z.$ Thus, if we take **separation** as our *definition of the independencies* induced by the network structure, we are effectively **restricting our ability to encode nonmonotonic independence relations**. Recall that in the context of intercausal reasoning in **Bayesian networks**, *nonmonotonic reasoning patterns* are quite useful in many situations for example, when two diseases are independent, but dependent given some common symptom. The nature of the separation property implies that *such independence patterns* **cannot be expressed** in the structure of a **Markov network**.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 115



## Soundness and Faithfulness of D-Separation

- [[Soundness and Faithfulness of D-Separation in Bayesian Net]]






-----------
##  Recommended Notes and References


- [[Separation in Markov Network]]

- [[I-Map and Independence Assertion]]
- [[Conditional Independence]]
- [[Bayesian Network on Directed Acyclic Graph]]



- [[Separation of Graph]]
- [[Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 69
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 562 - 564