---
tags:
  - concept
  - machine_learning/models
  - boosting
  - machine_learning/algorithms
  - machine_learning/boosting
keywords:
  - boosting
  - ensemble_method
  - maximum_entropy_learning
  - gradient_boost
topics:
  - machine_learning_models
  - machine_learning_algorithm
name: Iterative Maximum Entropy Learning for Gradient Boosting
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Iterative Maximum Entropy Learning for Gradient Boosting

![[Gradient Boosting Algorithm#^dad77c]]

- [[Gradient Boosting Algorithm]]

![[Maximum Entropy Learning#^7f19cd]]


>[!important] Definition
>Denote $\mathscr{P}:= \mathscr{P}(\mathcal{X}, \mathcal{Y})$ be the space of all probability measures on $(X,Y)$.
>
>The **Gradient Boost** algorithm solves the **maximum entropy learning** problem at each iteration $t=1\,{,}\ldots{,}\,$
>$$
>\begin{align*}
>\min_{D \in \mathscr{P}} \;\;& \mathbb{KL}\left( D \left\|\right. D_{0} \right) \\
>\text{s.t. }\;\;& \lVert\; \mathbb{E}_{ D }\left[\, \phi \left(Y\,h_{j}(X) \right)\, \right] - \mathbb{E}_{ \mathcal{D}_{n} }\left[ \phi \left( Y\,h_{j}(X)\right) \right] \;\rVert \le \lambda, \quad j=1\,{,}\ldots{,}\, t
>\end{align*}
>$$
>where 
>- $$h_{t}\in \mathcal{H} \subset \mathcal{Y}^{\mathcal{X}} $$ is the hypothesis learned at epoch $t$
>- $\phi: \mathcal{Y}\to \mathbb{R}$ is the *margin-based loss* $$L_{\phi}(Y, h_{j}(X)) := \phi \left(Y\,h_{j}(X)\right)$$
>- and $D_{n} \in \mathscr{P}$ is the **empirical distribution** of data $\mathcal{D}$ $$D_{n} = \frac{1}{n}\sum_{i=1}^{n}\delta_{X_{i},Y_{i}}$$

- [[Information Projection and Moment Projection]]
- [[Maximum Entropy Learning]]
- [[Margin-based Loss Function]]
- [[Iterative Maximum Entropy Learning for AdaBoost]]

## Explanation








-----------
##  Recommended Notes and References


- [[Maximum Entropy Learning]]
- [[AdaBoost Algorithm]]
- [[Gradient Boosting Trees]]

- [[Ensemble Learning]]

- [[Log-Partition Function of Exponential Family]]


- [[Empirical Risk Minimization]]
- [[Empirical Process and Empirical Measure]]



- [[Boosting Foundations and Algorithms by Schapire]]  pp 5
- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Elements of Information Theory by Cover]]