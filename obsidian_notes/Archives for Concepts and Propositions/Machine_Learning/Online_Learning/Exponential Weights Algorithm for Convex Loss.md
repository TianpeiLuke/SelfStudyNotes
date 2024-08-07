---
tags:
  - concept
  - machine_learning/online_learning
  - online_learning/algorithms
keywords:
  - exponential_weightes_algorithm
  - online_learning
topics:
  - online_learning
name: Exponential Weights Algorithm
date of note: 2024-08-05
---

## Concept Definition

>[!important]
>**Name**: Exponential Weights Algorithm or *Exponential Weighted Average* Algorithm

>[!important] Definition
>The **exponential weights algorithm (EWA)** or **exponential weighted average algorithm** is described as follows:
>- *Input*: outcome space $\mathcal{Y} \subset [0,1]$
>- *Input*: decision space $\mathcal{D} \subset [0,1]$, that is **compact** and **convex**
>- *Input*: a set of $k$ experts 
>- *Input*: a set of weights $\left\{ w_{i} \right\}$ for $k$ experts 
>- *Input*: a loss function $$\ell: \mathcal{D} \times \mathcal{Y} \to [0,1]$$ that is a **convex function** in its **first argument**.
>- *Input*: *learning rate* $\eta >0$
>- *Initialize* weights $w_{i}^{(1)} = 1$,  $i=1\,{,}\ldots{,}\,k$
>- For $t = 1\,{,}\ldots{,}\,T$:
>	- Each *expert* $i=1\,{,}\ldots{,}\,k$ **predicts** $f_{i}^{(t)}\in \mathcal{D}$
>	- Compute the **weighted average** of experts' predictions $$\hat{y}_{t} = \frac{\sum_{i=1}^{k}w_{i}^{(t)}f_{i}^{(t)}}{\sum_{i=1}^{k}w_{i}^{(t)}}$$
>	- *Observe* outcome $y_{t}\in \mathcal{Y}$
>	- Each **expert** $i=1\,{,}\ldots{,}\,k$ incurs a **loss**  $$\ell(f_{i}^{(t)}, y_{t})$$
>	- **Update** weight via **exponential update** $$w_{i}^{(t+1)} = w_{i}^{(t)}\exp \left( - \eta\;\ell(f_{i}^{(t)}, y_{t}) \right)$$
>	- *Forecaster* incurs a *loss* $\ell(\hat{y}_{t}, y_{t}).$

^05f7e9

- [[Weighted Majority Algorithm for Binary Loss]]
- [[Prediction with Expert Advice]]

## Regret Analysis

- [[Regret Analysis for Exponential Weights Algorithm]]


## Optimization Perspective

>[!important]
>The **EWA** can be seen as solving an online convex optimization problem via **generalized proximal algorithm** and **mirror descent**

![[Exponential Weights Algorithm as Mirror Descent#^9a4b7d]]

- [[Exponential Weights Algorithm as Mirror Descent]]
- [[Mirror Descent Algorithm]]

## Generalization

![[Weighted Average Forecast via Potential#^668a02]]

- [[Potential Function for Weighted Average Forecast]]
- [[Weighted Average Forecast via Potential]]




-----------
##  Recommended Notes and References


- [[Potential Function for Weighted Average Forecast]]
- [[Weighted Average Forecast via Potential]]
- [[Weighted Majority Algorithm for Binary Loss]]

- [[EXP3 or Exponential Weights Algorithm for Exploration and Exploitation]]


- [[Sequential Game Perspective for AdaBoost]]

- [[Convex Function]]

- [[Prediction Learning and Games by Cesa-Bianchi]] pp 5, 14, 36
- [[Bandit Algorithms by Lattimore]] pp 131 - 136
- [[Foundations of Machine Learning by Mohri]] pp 156 - 159