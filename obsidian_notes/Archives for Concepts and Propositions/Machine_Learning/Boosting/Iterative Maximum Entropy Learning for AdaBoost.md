---
tags:
  - concept
  - machine_learning/models
  - boosting
  - machine_learning/algorithms
  - machine_learning/boosting
keywords:
  - boosting
  - adaboost
  - ensemble_method
  - maximum_entropy_learning
topics:
  - machine_learning_models
  - machine_learning_algorithm
name: Maximum Entropy Learning for AdaBoost
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Iterative Maximum Entropy Learning for AdaBoost

>[!important] Definition
>The **AdaBoost** algorithm can be formulated as an **iterative I-projection Algorithm**. 
>- *Require*: a hypothesis set $\mathcal{H} \in \left\{ -1, +1 \right\}^{\mathcal{X}}$
>- *Require*: a collection of **binary labeled data** $$\left\{ (x_{i}, y_{i}), \; i=1 \,{,}\ldots{,}\, m\right\}$$ where $x_{i}\in \mathcal{X}$ and $y_{i}\in \left\{ -1, +1 \right\}$
>- *Require*: a **uniform** *sample distribution* $$U = \frac{1}{m}[1 \,{,}\ldots{,}\,1] \in \mathbb{R}^{m}$$
>- Initialize $D_{1} = U$
>- For $t=1,\,2\,{,}\ldots{,}\,$
>	- Use the *weak hypothesis* $h_{t}\in \mathcal{H}$ to **define** one of the **constraints** in the following optimization problem.
>	- Learn the *sample distribution* $D_{t+1}$ by solving the **maximum entropy learning problem**
>	  $$
>	  \begin{align*}
>	  \min_{D \in \mathscr{P}} \;\;& \mathbb{KL}\left( D \left\|\right. D_{t} \right) \\
>	  \text{s.t. }\;\;& \mathbb{E}_{ D }\left[ Y\,h_{t}(X) \right] = \sum_{i=1}^{m}D(i)y_{i}h_{t}(x_{i}) = 0
>	  \end{align*}
>	 $$
>	- **Greedy Constraint Selection**: choose $h_{t}\in \mathcal{H}$ so that $$\max_{h\in \mathcal{H}}\;\left\{ \min_{D: \sum_{i=1}^{m}D(i)y_{i}h(x_{i}) = 0} \mathbb{KL}\left( D \left\|\right. D_{t} \right)\right\} = \max_{h\in \mathcal{H}}\;\mathbb{KL}\left( D_{t+1} \left\|\right. D_{t} \right)$$


- [[Information Projection and Moment Projection]]
- [[Maximum Entropy Learning]]
- [[Margin-based Loss Function]]
- [[AdaBoost Algorithm]]
- [[Sequential Game Perspective for AdaBoost]]

>[!important] Definition
>The **AdaBoost** algorithm solves the **maximum entropy learning** problem at each iteration $t=1\,{,}\ldots{,}\,$
>$$
>\begin{align*}
>\min_{D \in \mathscr{P}} \;\;& \mathbb{KL}\left( D \left\|\right. D_{t} \right) \\
>\text{s.t. }\;\;& \mathbb{E}_{ D }\left[ Y\,h_{t}(X) \right] = \sum_{i=1}^{m}D(i)y_{i}h_{t}(x_{i}) = 0
>\end{align*}
>$$
>where 
>- $$h_{t}\in \mathcal{H}$$ is the hypothesis learned at epoch $t$
>- and $D_{t} \in \mathscr{P}$ is the **empirical distribution** of data $\mathcal{D}$ weighted by $w_{i}^{(t)} :=  D_{t}(i).$ $$D_{t} = \frac{1}{\sum_{i=1}^{n}w_{i}^{(t)}} \sum_{i=1}^{n}w_{i}^{(t)}\,\delta_{X_{i}}$$

- [[Empirical Process and Empirical Measure]]


## Explanation

>[!important] Definition
>From a broader perspective, Euclidean distance (squared) and relative entropy both turn out to be instances of a more general class of distance functions called **Bregman distances** for which it is known that such an *iterative projection algorithm* will be effective. 
>
>In the general case, the algorithm is known as **Bregman’s algorithm**.

- [[Generalized Proximal Method]]
- [[Mirror Descent Algorithm]]
- [[Bregman Divergence]]
- [[Bregman Projection]]


## Iterative Least Square

- [[Logistic Regression Solution via Iterative Reweighted Least Square]]
- [[Least Absolute Deviations Solution via Iterative Re-weighted Least Square]]



-----------
##  Recommended Notes and References


- [[Information Projection and Moment Projection]]
- [[Maximum Entropy Learning]]
- [[AdaBoost Algorithm]]
- [[Gradient Boosting Trees]]

- [[Ensemble Learning]]

- [[Log-Partition Function of Exponential Family]]


- [[Empirical Risk Minimization]]
- [[Empirical Process and Empirical Measure]]


- [[Generalized Proximal Method]]
- [[Entropy Minimization Algorithm]]
- [[Incremental Algorithm]]


- [[Boosting Foundations and Algorithms by Schapire]]  pp 231
- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Elements of Information Theory by Cover]]