---
tags:
  - concept
  - statistics/decision_theory
  - machine_learning/theory
keywords:
  - regularization
  - regularized_loss_minimization
topics:
  - machine_learning_theory
  - statistics/decision_theory
name: Regularized Loss Minimization
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: Regularized Loss Minimization

![[Empirical Risk Minimization#^a84128]]


>[!important] Definition
>**Regularized Loss Minimization (RLM)** is a learning rule in which we *jointly minimize* the *empirical risk* and a *regularization* function. 
>
>Formally, a **regularization function** is a mapping $$R: \mathcal{H} \to \mathbb{R}_{+},$$ and the *regularized loss minimization rule* outputs a hypothesis in
>$$
> \begin{align}
> h \in \arg\min_{h \in \mathcal{H}}\set{ L_{\mathcal{D}}(h) + R(h)}.
> \end{align} 
>$$ 

^494e48

- [[Empirical Risk Minimization]]
- [[Tikhonov Regularization in Optimization and Learning]]


## Explanation

>[!important]
>**Regularized loss minimization** shares similarities with **minimum description length** *algorithms* and **structural risk minimization**. 
>
>Intuitively, the "**complexity**" of hypotheses is measured by the value of the *regularization function*, and the algorithm **balances** between *low empirical risk* and "*simpler*," or ``*less complex*," hypotheses.

- [[Structural Risk Minimization]]




-----------
##  Recommended Notes and References

- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]

- [[Structural Risk Minimization]]


- [[Foundations of Machine Learning by Mohri]]
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 137 