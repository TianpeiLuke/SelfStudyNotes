---
tags:
  - concept
  - machine_learning/theory
keywords:
  - bayes_error
  - bayes_optimal
  - bayes_optimal_classification
  - bayes_classifier
topics:
  - machine_learning_theory
name: Bayes Error
date of note: 2024-08-30
---

## Concept Definition

>[!important]
>**Name**: Bayes Error and Bayes Optimal Classification

![[Empirical Risk Minimization#^0c98ce]]

![[Empirical Risk Minimization#^cf1946]]


>[!important] Definition
>Let  $\mathcal{P}$ be a distribution over $\mathcal{X} \times \mathcal{Y}$,  
>
>The **Bayes error** or **Bayes risk** $L^{*}$ is defined as the *infimum of the errors* achieved by *all measurable functions* $h : \mathcal{X} \to \mathcal{Y}$:  
>$$
> L^{*} = \inf_{h \in \mathcal{Y}^{\mathcal{X}} \text{ measurable}} L_{\mathcal{P}}(h).
>$$  
>
>A hypothesis $h$ with $L(h) = L^{*}$ is called a **Bayes hypothesis** or **Bayes classifier**.

^e55817

- [[Empirical Risk Minimization]]
- [[Measurable Function]]

## Explanation

>[!info]
>**Bayes Error** is a **functional of underlying distribution** $\mathcal{P}$ only and it does not depend on choice of function $h$ or function class $\mathcal{H}$.
>$$
> \begin{align*}
>  L^{*} & \equiv  L^{*}(\mathcal{P}).
> \end{align*}
>$$  
>Intuitively, it reflects how *hard* the learning problem} is *intrinsically* since it determines the *lower bound* of *generalization error*.






-----------
##  Recommended Notes and References


- [[Bayes Classifier via Posterior Probability]]
- [[Statistical Decision Problem]]


- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[PAC-Bayes Learnable]]


- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 25
- [[Foundations of Machine Learning by Mohri]] pp 22 - 23, 47, 61, 67, 74 - 78
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Probabilistic Theory of Pattern Recognition by Devroye]] pp 09 - 12