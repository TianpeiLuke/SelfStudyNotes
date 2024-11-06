---
tags:
  - concept
  - machine_learning/models
  - boosting
  - machine_learning/algorithms
  - machine_learning/boosting
  - machine_learning/ensemble_methods
keywords:
  - boosting
  - adaboost
  - ensemble_method
topics:
  - machine_learning_models
  - machine_learning_algorithm
name: AdaBoost Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: AdaBoost Algorithm

![[Empirical Risk Minimization#^a84128]]



>[!important] Definition
>The **AdaBoost** algorithm is described as the following:
>- *Require*: a collection of **binary labeled data** $\left\{ (x_{i}, y_{i}), \; i=1 \,{,}\ldots{,}\, m\right\}$ where $x_{i}\in \mathcal{X}$ and $y_{i}\in \left\{ -1, +1 \right\}$
>- **Initialize** with uniform weight distribution $$D_{1} = \frac{1}{m}[1 \,{,}\ldots{,}\,1] \in \mathbb{R}^{m}$$
>- For $t = 1 \,{,}\ldots{,}\,T$:
>	- Train a **weak learner** using distribution $D_{t}$
>	- Get **weak hypothesis** $$h_{t}: \mathcal{X} \to \left\{ -1, +1 \right\}$$
>	- Select $h_{t}$ to **minimize the weighted training error** $$\epsilon_{t} := L_{D_{t}, l}(h_{t}) :=  \widehat{\mathbb{E}}_{ X \sim D_{t} }\left[ \mathbb{1}\left\{ h_{t}(X) \neq l(X) \right\}  \right]$$
>	- Choose **rate** $$\alpha_{t} = \frac{1}{2}\log \left( \frac{1 - \epsilon_{t}}{\epsilon_{t}} \right)$$
>	- **Update weight** based on rate $\alpha_{t}$: for $i = 1\,{,}\ldots{,}\,m$:
>		- $$\begin{align*} D_{t+1}(i) &= \frac{D_{t}(i)}{Z_{t}} \times \left\{\begin{array}{cc} e^{-\alpha_{t}}\; & \text{if }h_{t}(x_{i}) = y_{i} \\ e^{\alpha_{t}}  &\text{if }h_{t}(x_{i}) \neq y_{i} \end{array}\right. \\[8pt] &= \frac{D_{t}(i)\,\exp\left( -\alpha_{t}\,y_{i}\,h_{t}(x_{i}) \right)}{Z_{t}} \end{align*}$$ where $Z_{t}$ is the **partition function** (**normalization factor**) so that $\sum_{i}D_{t+1}(i) = 1.$
>		  
>- *Output* the *final hypothesis* by a **weighted combination** of all learned weak hypotheses: $$H(x) = \text{sgn}\left(  \sum_{t=1}^{T}\alpha_{t}\,h_{t}(x) \right).$$

^1982f3

- [[Empirical Risk Minimization]]
- [[Empirical Process and Empirical Measure]]


## Explanation

>[!important]
>The basic principles behind the *AdaBoost* algorithm are two folds:
>1. A **strong classifier** can be obtained by a **linear combination of weak classifiers**
>2. Each weak classifier only **focuses on a sub-population** that are not learned well by the previous learned models. This is obtained by **increase the importance weight** for the samples that are **misclassified** so that we can learn a hierarchical sequence of classifiers.


## AdaBoost as Sequential Two-Player Zero-Sum Game

- [[Sequential Game Perspective for AdaBoost]]

## AdaBoost as Iterative Maximum Entropy Learning

- [[Iterative Maximum Entropy Learning for AdaBoost]]
- [[Online Learning Perspective for AdaBoost]]

## AdaBoost as Greedy Stagewise Exponential Loss Minimization

- [[Forward Stagewise Additive Modeling]]
- [[Exponential Loss Minimization for AdaBoost]]


## Generalization to Gradient Boost

- [[Functional Gradient Descent]]
- [[Gradient Boosting Algorithm]]


## Ensemble Methods

- [[Bagging and Model Averaging]]
- [[Ensemble Learning]]




-----------
##  Recommended Notes and References


- [[Iterative Maximum Entropy Learning for AdaBoost]]
- [[Ensemble Learning]]
- [[Functional Gradient Descent]]

- [[Log-Partition Function of Exponential Family]]


- [[Classification Problem]]
- [[Empirical Risk Minimization]]
- [[Empirical Process and Empirical Measure]]



- [[Boosting Foundations and Algorithms by Schapire]]  pp 5
- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Elements of Information Theory by Cover]]