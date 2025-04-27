---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/representation
  - probabilistic_graphical_models/inference
  - MAP_Inference
  - exact_inference
keywords:
  - bayesian_network
  - statistical_inference
topics:
  - probabilistic_graphical_model
name: Complexity of Exact MAP Inference in Bayes Net
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Complexity of Exact MAP Inference in Bayes Net

### Decide Existence of Assignment above a Probability Threshold

>[!important] Definition (BN-MAP-DP)
>Define the *MAP inference* problem **BN-MAP-DP** problem.
>
>Given a **Bayesian network** $\mathcal{B} := (\mathcal{G}, \mathcal{P})$ over $\mathcal{X}$, a number $\tau$, decide whether there *exists* **assignment** $x$ to $\mathcal{X}$ such that $$\mathcal{P}_{\mathcal{B}}\left(\mathcal{X} = x\right) > \tau.$$

- [[Bayesian Network on Directed Acyclic Graph]]

>[!important] Theorem
>The decision problem **BN-MAP-DP** is **$NP$-complete.**

### Decide Existence of Marginal Assignment above a Probability Threshold

>[!important] Definition (BN-margMAP-DP)
>Define the *marginal MAP inference* problem **BN-margMAP-DP** problem.
>
>Given a **Bayesian network** $\mathcal{B} := (\mathcal{G}, \mathcal{P})$ over $\mathcal{X}$, a number $\tau$,  and a subset $\mathcal{Y} \subset \mathcal{X}$,  decide whether there *exists* **assignment** $y$ to $\mathcal{Y}$ such that $$\mathcal{P}_{\mathcal{B}}\left(\mathcal{Y} = y\right) > \tau.$$

>[!important] Theorem
>The decision problem **BN-margMAP-DP** is **$NP$-complete.**
>
>In fact, the decision problem **BN-margMAP-DP** is **harder than** the *$NP$-complete problem* as it involves both *maximization* and *summation*. 


### Decide Existence of Assignment above a Probability Threshold for Polytree


>[!important] Theorem
>The following the *MAP inference* problem for polytree Bayesian network is **$NP$-hard.**
>
>Given a **polytree Bayesian network** $\mathcal{B} := (\mathcal{G}, \mathcal{P})$ over $\mathcal{X}$, a number $\tau$,  and a subset $\mathcal{Y} \subset \mathcal{X}$,  decide whether there *exists* **assignment** $x$ to $\mathcal{X}$ such that $$\mathcal{P}_{\mathcal{B}}\left(\mathcal{Y} = y\right) > \tau.$$









## Explanation





-----------
##  Recommended Notes and References


- [[Complexity of Exact Marginal and Conditional Inference in Bayes Net]]

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Graph]]

- [[Statistical Inference Problem]]

- [[Probabilistic Graphical Models by Koller]] pp 551 - 552
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]

