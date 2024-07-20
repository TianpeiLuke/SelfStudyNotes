---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/representation
  - probabilistic_graphical_models/inference
keywords:
  - bayesian_network
  - statistical_inference
topics:
  - probabilistic_graphical_model
name: Exact Inference in Bayesian Network
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Exact Inference in Bayesian Network

### Decide Support of Marginal 

>[!important] Definition (BN-Pr-DP)
>Define the *conditional probability inference* problem **BN-Pr-DP** problem.
>
>Given a **Bayesian network** $\mathcal{B} := (\mathcal{G}, \mathcal{P})$ over $\mathcal{X}$, a variable $X\in \mathcal{X}$, and a value $x\in \text{Val}(X)$, decide if $$\mathcal{P}_{\mathcal{B}}\left(X = x\right) > 0.$$

- [[Bayesian Network on Directed Acyclic Graph]]


>[!important] Theorem
>The decision problem **BN-Pr-DP** is **$NP$-complete.**

### Compute Marginal 

>[!important] Definition (BN-Pr)
>Define the *conditional probability inference* problem **BN-Pr** problem.
>
>Given a **Bayesian network** $\mathcal{B} := (\mathcal{G}, \mathcal{P})$ over $\mathcal{X}$, a variable $X\in \mathcal{X}$, and a value $x\in \text{Val}(X)$, *compute* $$\mathcal{P}_{\mathcal{B}}\left(X = x\right).$$

>[!important] Theorem
>The computation problem **BN-Pr** is **$\#P$-complete**.

### Approximate Inference

>[!important] Theorem
>The following *approximate inference* problem is **$NP$-hard**:
>
>Given a **Bayesian network** $\mathcal{B} := (\mathcal{G}, \mathcal{P})$ over $\mathcal{X}$, a variable $X\in \mathcal{X}$, and a value $x\in \text{Val}(X)$, *find* a number $\rho>0$ that has *relative error* $\epsilon$ for $\mathcal{P}_{\mathcal{B}}\left(X = x\right).$ That is
>$$
> \frac{\rho}{1 + \epsilon} \le \mathcal{P}_{\mathcal{B}}(X=x)  \le \rho \left(1 + \epsilon\right)
>$$

>[!important] Theorem
>The following *approximate conditional inference* problem is **$NP$-hard** for $\epsilon\in (0, 1/2)$:
>
>Given a **Bayesian network** $\mathcal{B} := (\mathcal{G}, \mathcal{P})$ over $\mathcal{X}$, a variable $X\in \mathcal{X}$,  a value $x\in \text{Val}(X)$ and an *observation* $E =e$ for $E \subset \mathcal{X}$, *find* a number $\rho>0$ that has *absolute error* $\epsilon$ for $\mathcal{P}_{\mathcal{B}}\left(X = x \,|\,E=e\right).$ That is
>$$
>  \lvert\; \mathcal{P}_{\mathcal{B}}(X=x |E=e)  - \rho \;\rvert \le \epsilon.
>$$




## Explanation





-----------
##  Recommended Notes and References

- [[Complexity of Exact MAP Inference in Bayes Net]]

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Graph]]

- [[Statistical Inference Problem]]

- [[Probabilistic Graphical Models by Koller]] pp 288
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]

