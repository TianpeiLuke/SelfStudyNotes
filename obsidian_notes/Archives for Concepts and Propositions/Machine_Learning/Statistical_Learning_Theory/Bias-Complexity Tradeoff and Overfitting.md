---
tags:
  - concept
  - machine_learning/theory
keywords:
  - overfitting
  - bias_complexity_tradeoff
topics:
  - machine_learning_theory
name: Bias-Complexity Tradeoff and Overfitting
date of note: 2024-08-30
---

## Concept Definition

>[!important]
>**Name**: Bias-Complexity Tradeoff and Overfitting

![[Empirical Risk Minimization#^0c98ce]]

![[Empirical Risk Minimization#^cf1946]]

![[Bayes Error and Bayes Classifier#^e55817]]

![[Estimation Error and Approximation Error#^15fb90]]

>[!important] Definition
>The *goal* of a learning algorithm is to find a hypothesis $h\in c H$ that *minimizes the total risk*
>$$
>\begin{align*}
> L(h)  - L^{*} &=\underbrace{\left(L(h)  - \inf_{h \in \mathcal{H}}L(h)\right)}_{\text{\emph{estimation error}}} + \underbrace{\left(\inf_{h \in \mathcal{H}}L(h) - L^{*}\right)}_{\text{\emph{approximation error}}}.
> \end{align*} 
>$$
>
>The **bias-complexity tradeoff** is referred to the two conflicting objectives when minimizing the *total risk*:
>- **the approximation error** *decreases* when the *size* and **complexity** of hypothesis class $\mathcal{H}$ *increases*; 
>- **the estimation error** *decreases* when the *size* and **complexity** of hypothesis class $\mathcal{H}$ *decreases*; 

^73e1a0

- [[Estimation Error and Approximation Error]]

>[!important] Definition
>The **overfitting** is a phenomenon that when the *size* and *complexity* of hypothesis class $\mathcal{H}$ is *large*, the optimal hypothesis $h_{ERM}$ from *empirical risk minimization* has **large estimation error**
>$$
>\text{complexity}(\mathcal{H}) \text{ large} \vDash\; L_{D}(h_{ERM}) = 0 \implies  \left(L(h_{ERM})  - \inf_{h \in \mathcal{H}}L(h)\right) \text{ large}
>$$


>[!important] Definition
>The **underfitting** is a phenomenon that when the *size* and *complexity* of hypothesis class $\mathcal{H}$ is *small*, the optimal hypothesis $h_{ERM}$ from *empirical risk minimization* has **large approximation error**
>$$
>\text{complexity}(\mathcal{H}) \text{ small} \implies  \left(\inf_{h \in \mathcal{H}}L(h) - L^{*}\right)\text{ large}
>$$

- [[Structural Risk Minimization]]

## Explanation

>[!quote]
>Learning theory studies how *rich* we can make $\mathcal{H}$ while still maintaining *reasonable estimation error*. In many cases, empirical research focuses on **designing good hypothesis classes** for a certain domain. Here, “good” means classes for which the *approximation error* would *not* be excessively *high*. The idea is that although we are not *experts* and do not know how to construct the optimal classifier, we still have some *prior knowledge* of the specific *problem* at hand, which enables us to design hypothesis classes for which **both the _approximation error_ and the _estimation error_ are not too large.**
>
>-- [[Understanding Machine Learning by Shalev-Shwartz]] pp 41


## Structural Risk Minimization

![[Structural Risk Minimization#^16b921]]

- [[Structural Risk Minimization]]



-----------
##  Recommended Notes and References


- [[Bias-Variance Tradeoff]]

- [[Estimation Error and Approximation Error]]
- [[Bayes Error and Bayes Classifier]]
- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]


- [[Understanding Machine Learning by Shalev-Shwartz]] pp 41
- [[Foundations of Machine Learning by Mohri]] pp 26
- [[Algorithms to Live By Chapter 07 Overfitting]]