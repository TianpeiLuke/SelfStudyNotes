---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/theory
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/inference
keywords:
  - variational_inference
  - probabilistic_graphical_model
  - clique_tree
topics:
  - probabilistic_graphical_model
name: Variational Inference for Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Variational Inference for Graphical Model

![[Maximum Entropy Learning of Clique Tree PGM#^f81f88]]

![[Variational Inference for Clique Tree#^5fe294]]


- [[Variational Inference for Clique Tree]]
- [[Maximum Entropy Learning of Clique Tree PGM]]







## Explanation

>[!quote]
>This theorem characterizes the **solution** of the *optimization problem* in terms of **fixed-point equations** that must hold when we find a **maximal** $\mathcal{Q}$. These fixed-point equations define the *relationships that must hold* between the different *parameters* involved in the optimization problem. Most importantly, equation (11.10) defines each **message** in terms of **other messages**, allowing an easy **iterative approach** to solving the *fixed point equations*. These same themes appear in all the approaches we will discuss later in this chapter.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 390

- [[Fixed Point of Map]]
- [[Contraction Map Principle]]
- [[Sum-Product Message Passing Algorithm for Clique Tree]]
- [[Belief-Update Message Passing Algorithm for Clique Tree]]






-----------
##  Recommended Notes and References


- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]


- [[Variational Inference for Clique Tree]]
- [[Maximum Entropy Learning of Clique Tree PGM]]
- [[Evidence Lower Bound]]
- [[Variational Inference vs EM Algorithm]]



- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network Distribution to Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 387 - 393
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 73 - 92
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
