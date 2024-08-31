---
tags:
  - concept
  - machine_learning/theory
keywords:
  - fundamental_theorem_statistical_learning
topics:
  - machine_learning_theory
name: Fundamental Theorem of Statistical Learning
date of note: 2024-08-30
---

## Concept Definition

>[!important]
>**Name**: Fundamental Theorem of Statistical Learning

![[Empirical Risk Minimization#^0c98ce]]

![[PAC Learnable and Agnostic PAC Learnable#^a09a6f]]

![[Structural Risk Minimization#^e11f9f]]


>[!important] The Fundamental Theorem of Statistical Learning
>Let $\mathcal{H}$ be a hypothesis class of **binary functions** from $\mathcal{X}$ to $\{ 0,1 \}$, and let the loss function be the **0-1 loss**.
>
>Then, the following are **equivalent**:
>- $\mathcal{H}$ has the **uniform convergence property**.
>- Any **empirical risk minimization (ERM)** rule is a successful **agnostic PAC learner** for $\mathcal{H}$.
>- $\mathcal{H}$ is **agnostic PAC learnable**.
>- $\mathcal{H}$ is **PAC learnable**.
>- Any **ERM** rule is a successful **PAC learner** for $\mathcal{H}$.
>- $\mathcal{H}$ has a **finite VC-dimension.**

^33dd5e

- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Empirical Risk Minimization]]
- [[Structural Risk Minimization]]
- [[Generalization Error Bound for Binary Classification VC Dimension]]


## Explanation



-----------
##  Recommended Notes and References


- [[Empirical Risk Minimization]]
- [[Bayes Error and Bayes Classifier]]
- [[Estimation Error and Approximation Error]]
- [[PAC Learnable and Agnostic PAC Learnable]]


- [[Understanding Machine Learning by Shalev-Shwartz]] pp 37 - 40