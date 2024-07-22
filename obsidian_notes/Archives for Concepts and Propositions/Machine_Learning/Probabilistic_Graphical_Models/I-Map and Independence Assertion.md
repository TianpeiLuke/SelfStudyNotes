---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/theory
  - math/probability
keywords:
  - i_map
  - independence_assertion
topics:
  - probabilistic_graphical_model
name: I-Map and Independence Assertion
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: I-Map and Independence Assertion

>[!important] Definition
>Let $\mathcal{P}$ be a distribution over $\mathcal{X}$. 
>
>We define $\mathcal{I}(\mathcal{P})$ to be *the set* of **(conditional) independence assertions** of the form
>$$
>\mathcal{P} \vDash (X \perp Y \,|\, Z)
>$$
>that hold in $\mathcal{P}$

- [[Conditional Independence]]


>[!important] Definition
>Let $\mathcal{G}$ be a graph. Then $\mathcal{G}$ encodes the following set of *conditional independence assumptions*, called the **local independencies**, and denoted as $\mathcal{I}_{\ell}(\mathcal{G})$:
>$$
>\left( X_{i} \perp X_{\text{NonDescendant}_{G}(i)} \,|\,X_{Pa(i)}\right)\quad \forall i\in \mathcal{V}.
>$$
>where 
>- *NonDescendant$_{G}(i)$* is the set of all vertices $i$ in $\mathcal{G}$ such that there *does not exists* a directed path $i\to x$.
>- *Pa$_{G}(i)$* is the set of all vertices $j$ in $\mathcal{G}$ such that there *exists* a directed path $j\to i$.
>  
>  
>That is, the *local dependencies* states that each node $X_{i}$ is *conditionally independent* with its *nondescendants* given its *parents*.
>

^775ffa


>[!important] Definition
>We can now rewrite the statement that “*$\mathcal{P}$ satisfies the local independencies associated with $\mathcal{G}$*” simply as $$\mathcal{I}_{\ell}(\mathcal{G}) \subseteq \mathcal{I}(\mathcal{P}).$$
>
>In this case, we say that $\mathcal{G}$ is an **$I$-map** (**independence map**) for $\mathcal{P}$.


>[!important] Definition
>Let $\mathcal{K}$ be any *graph object* associated with a set of independencies $\mathcal{I}(\mathcal{K})$.
>
>We say that $\mathcal{K}$ is an **$I$-map** for a set of independencies $\mathcal{I}$ if $$\mathcal{I}(\mathcal{K}) \subseteq \mathcal{I}.$$
>
>We say that $\mathcal{G}$ is an **$I$-map** *for* $\mathcal{P}$ if $\mathcal{G}$ is an **$I$-map** for $\mathcal{I}(\mathcal{P}).$


## Explanation





-----------
##  Recommended Notes and References


- [[D-Separation in Bayesian Network]]
- [[Conditional Independence]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[Independent Random Variables]]

- [[Graph]]
- [[Probabilistic Graphical Models]]


- [[Probabilistic Graphical Models by Koller]] pp 60
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
