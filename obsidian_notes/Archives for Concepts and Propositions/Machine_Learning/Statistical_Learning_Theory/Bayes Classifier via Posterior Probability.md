---
tags:
  - concept
  - machine_learning/theory
keywords:
  - posterior_measure
  - bayes_classifier
topics:
  - machine_learning_theory
name: Bayes Classifier via Posterior Probability
date of note: 2024-08-30
---

## Concept Definition

>[!important]
>**Name**: Bayes Classifier via Posterior Probability

![[Empirical Risk Minimization#^0c98ce]]

![[Empirical Risk Minimization#^cf1946]]

![[Bayes Error and Bayes Classifier#^e55817]]

>[!important] Definition
>Let $\mathcal{P}$ be a joint distribution over $\mathcal{X} \times \mathcal{Y}$ and $\mathcal{P}(Y|X)$ be the *posterior distribution* of $Y$ given $X$.
>
>Define the **Bayes decision function** as 
>$$
>\begin{align*}
> h^{*}(x) = \left\{\begin{array}{cl}1 & \text{ if }\eta(x) > \dfrac{1}{2} \\[5pt] 0& \text{ otherwise}\end{array} \right.
>\end{align*}
>$$
>where $\eta(x)$ is  *posterior probability function* 
>$$
>\eta(x) =\mathcal{P}(Y=1 | x)
>$$

- [[Bayes Error and Bayes Classifier]]
- [[Prior and Posterior Measure]]

>[!important] Theorem
>Let $\mathcal{P}$ be a joint distribution over $\mathcal{X} \times \{ 0,1 \}$ and $\mathcal{P}(Y|X)$ be the **posterior distribution** of $Y$ given $X$.  Denote $h^{*}$ as the **Bayes decision function.**
>
>Then for any measurable function $h: \mathcal{X} \to \{ 0,1 \}$, 
>$$
>L_{\mathcal{P}}(h^{*}) := \mathcal{P}\left\{ h^{*}(X) \neq Y \right\} \le \mathcal{P}\left\{ h(X) \neq Y \right\} := L_{\mathcal{P}}(h).
>$$
>That is, $h^{*}$ is the **Bayes classifier.**

- [[Measurable Function]]

## Explanation

>[!info]
>This theorem shows that the information about a **classification problem** is completely *encoded* by the **posterior distribution** $\mathcal{P}(Y|X)$ **alone** not the data distribution $\mathcal{P}(X)$.
>
>Knowing the posterior distribution is **sufficient** to obtain the optimal classification rule.






-----------
##  Recommended Notes and References

- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 25
- [[Foundations of Machine Learning by Mohri]] pp 22 - 23, 47, 61, 67, 74 - 78
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Probabilistic Theory of Pattern Recognition by Devroye]] pp 10 - 12