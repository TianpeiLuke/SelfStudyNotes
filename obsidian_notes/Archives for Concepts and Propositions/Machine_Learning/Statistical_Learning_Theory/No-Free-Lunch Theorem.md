---
tags:
  - concept
  - machine_learning/theory
keywords:
  - no_free_lunch_theorem
topics:
  - machine_learning_theory
name: No-Free-Lunch Theorem
date of note: 2024-08-30
---

## Concept Definition

>[!important]
>**Name**: No-Free-Lunch Theorem

![[Empirical Risk Minimization#^a84128]]

![[PAC Learnable and Agnostic PAC Learnable#^500325]]


>[!important] No-Free-Lunch Theorem
>Let $\mathcal{A}$ be **any learning algorithm** for the task of *binary classification* with respect to the 0−1 loss over a domain $\mathcal{X}$.  Let $m$ be any number smaller than $|\mathcal{X}|/2$, representing a *training set size*. 
>
>Then, there *exists* a distribution $\mathcal{P}$ over $\mathcal{X} \times \{0, 1\}$ such that: 
>- There **exists** a function $f : \mathcal{X} \to \{0, 1\}$ with $$L_{\mathcal{P}}(f) = 0.$$ 
>- With **probability** of **at least** $1/7$ over the choice of $\mathcal{D}_{m} \sim \mathcal{P}$ we have that $$L_{\mathcal{P}}(\mathcal{A}(\mathcal{D}_{m})) \ge \frac{1}{8}.$$

^33dd5e

- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Empirical Risk Minimization]]


## Explanation

>[!important] 
>This theorem states that for **every learner**, there **exists a task** on which it **fails**, even though that task can be successfully learned by **another learner**.
>
>-- [[Understanding Machine Learning by Shalev-Shwartz]] pp 37

^2cabf5

>[!quote]
>The No-Free-Lunch theorem states that **there is no universal learner**. Every learner has to be specified to *some task*, and use some *prior knowledge* about that task, in order to succeed.
>
>-- [[Understanding Machine Learning by Shalev-Shwartz]] pp 41


## Prior Knowledge and Inductive Bias

>[!info]
>The No-free-lunch theorem implies that if we **lack of prior knowledge** when selecting the hypothesis class $\mathcal{H}$,  any algorithm that chooses its output from hypotheses in $\mathcal{H}$, and in particular the ERM predictor, will **fail** on **some** *learning task*. Therefore, this class is **not PAC learnable**.

>[!important] Corollary
>Let $\mathcal{X}$ be an **infinite domain** set and let $\mathcal{H}$ be the set of **all functions** from $\mathcal{X}$ to $\{0, 1\}$. 
>
>Then, $\mathcal{H}$ is **not PAC learnable**.

- [[Inductive Bias in Machine Learning]]


>[!quote]
>How can we *prevent* such failures? We can escape the hazards foreseen by the *No-Free-Lunch theorem* by using our **prior knowledge** about a **specific learning task**, to avoid the distributions that will cause us to fail when learning that task. Such prior knowledge can be expressed by **restricting our hypothesis class**. 
>
>But how should we choose a good hypothesis class? On the one hand, we want to believe that this class includes the hypothesis that has *no error at all* (in the **PAC setting**), or at least that the *smallest error achievable* by a hypothesis from this class is indeed rather *small* (in the **agnostic setting**). On the other hand, we have just seen that we cannot simply choose the richest class – the class of all functions over the given domain.
>
>-- [[Understanding Machine Learning by Shalev-Shwartz]] pp 40


- [[Bias-Complexity Tradeoff and Overfitting]]



-----------
##  Recommended Notes and References


- [[Empirical Risk Minimization]]
- [[Bayes Error and Bayes Classifier]]
- [[Estimation Error and Approximation Error]]
- [[PAC Learnable and Agnostic PAC Learnable]]


- [[Understanding Machine Learning by Shalev-Shwartz]] pp 37 - 40