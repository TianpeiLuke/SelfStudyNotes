---
tags:
  - concept
  - machine_learning/theory
keywords:
  - estimation_error
  - approximation_error
topics:
  - machine_learning_theory
name: Estimation Error and Approximation Error
date of note: 2024-08-30
---

## Concept Definition

>[!important]
>**Name**: Estimation Error and Approximation Error

![[Empirical Risk Minimization#^0c98ce]]

![[Empirical Risk Minimization#^cf1946]]

### Excess Error

>[!important] Definition
>The **excess risk** of a *hypothesis* $h\in \mathcal{H}$ is defined as the difference between the *generalization error* of a given hypothesis $h$ and the *optimal generalization error* within $\mathcal{H}$ under the *empirical risk minimization*
>$$
> L_{\mathcal{P}}(h) - \inf_{h\in \mathcal{H}}L_{\mathcal{P}}(h)
>$$

- [[Empirical Risk Minimization#Agnostic Setting]]

### Decomposition of Total Risk

>[!important] Definition
>The **total risk** is defined as the *difference* between the *generalization error* of a hypothesis $h\in \mathcal{H}$ and the Bayes error $L^{*}$ . It can be decomposed into two parts: 
>$$
>\begin{align*}
> L(h)  - L^{*} &=\underbrace{\left(L(h)  - \inf_{h \in \mathcal{H}}L(h)\right)}_{\text{\emph{estimation error}}} + \underbrace{\left(\inf_{h \in \mathcal{H}}L(h) - L^{*}\right)}_{\text{\emph{approximation error}}}.
> \end{align*} 
>$$
>- The **estimation error** is defined as the *excess risk* of choosing a hypothesis $h\in \mathcal{H}$ as compared to the minimal risk achievable in $\mathcal{H}$: $$L(h)  - \inf_{h \in \mathcal{H}}L(h)$$
>	- It measures the quality of the hypothesis $h$ with respect to the *best-in-class hypothesis*.
>- The **approximation error** is defined as the difference between the *minimum risk* achievable by a predictor *in the hypothesis class* $\mathcal{H}$ and the minimum risk for all hypotheses.  $$\inf_{h \in \mathcal{H}}L(h) - L^{*}$$
>	-  It measures *how well* the *Bayes error* can be *approximated* using the *hypothesis class*. 
>	- This latter term may be bounded in a *distribution-free manner*, and a *rate of convergence* results that only depends on the *structure* of $\mathcal{H}$.

^15fb90

- [[Bayes Error and Bayes Classifier]]

## Explanation

>[!info]
>The *the excess risk* is defined as the **regret** of choosing $h\in \mathcal{H}$ as compared to the *optimal hypothesis* in $\mathcal{H}$.
>
>This is for the **agnostic setting** for PAC learning.

- [[Regret for Online Learning]]
- [[No-Regret Learning]]

>[!info]
>The **optimal rule** in the above definition is with respect to a *given hypothesis class* $\mathcal{H}$, 

>[!info]
>The **approximation error** is determined by the choice of hypothesis class $\mathcal{H}$, which is reduced when the *size* and the *complexity of hypothesis class* $\mathcal{H}$ is increased. 
>
>The **estimation error** can be reduced by choosing a better *learning algorithm*.

>[!info]
>When *ERM* hypothesis is chosen, the **estimation error** is due to the difference between empirical error and the generalization error
>$$
>L(h_{ERM})  - \inf_{h \in \mathcal{H}}L(h)
>$$
>The quality of this estimation depends on the **training set size** and on the size, or **complexity**, of the *hypothesis class*.

- [[Empirical Risk Minimization]]

## Bias-Complexity Tradeoff and Strutrual Risk Minimization

- [[Bias-Complexity Tradeoff and Overfitting]]
- [[Structural Risk Minimization]]


-----------
##  Recommended Notes and References



- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]

- [[Regret for Online Learning]]
- [[No-Regret Learning]]


- [[Understanding Machine Learning by Shalev-Shwartz]] pp 40
- [[Foundations of Machine Learning by Mohri]] pp 26