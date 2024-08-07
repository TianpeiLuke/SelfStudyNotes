---
tags:
  - concept
  - machine_learning/online_learning
  - online_learning/algorithms
keywords:
  - online_learning
  - weighted_majority_algorithm
topics:
  - online_learning
name: Weighted Majority Algorithm
date of note: 2024-08-05
---

## Concept Definition

>[!important]
>**Name**: Weighted Majority Algorithm for Binary Loss

>[!important] Definition
>The **weighted majority algorithm (WMA)** is described as follows:
>- *Input*: *outcome space* $\mathcal{Y}=\left\{ 0,1 \right\}$ and *decision space* $\mathcal{D} = \left\{ 0,1 \right\}$
>- *Input*: a set of $k$ experts 
>- *Input*: a set of weights $\left\{ w_{i} \right\}$ for $k$ experts 
>- *Input*: a positive parameter $\epsilon \in (0,1)$
>- *Initialize* weights $w_{i}^{(1)} = 1$,  $i=1\,{,}\ldots{,}\,k$
>- For $t = 1\,{,}\ldots{,}\,T$:
>	- Each *expert* $i = 1\,{,}\ldots{,}\,k$ **predicts** $f_{i}^{(t)} \in \left\{ 0,1 \right\}$
>	- Compute the prediction via the **weighted majority vote** $$\hat{y}_{t} = \mathbb{1}\left\{ \frac{\sum_{i=1}^{k}w_{i}^{(t)}f_{i}^{(t)}}{\sum_{i=1}^{k}w_{i}^{(t)}} \ge \frac{1}{2}\right\}$$
>	- **Observe** outcome $y_{t}$
>	- Each **expert** $i=1\,{,}\ldots{,}\,k$ incurs a **binary loss**, $$\ell(f_{i}^{(t)}, y_{t}) := \mathbb{1}\left\{ f_{i}^{(t)} \neq y_{t} \right\} $$
>	- **Update** weight $$w_{i}^{(t+1)} = w_{i}^{(t)}\times \left( 1- \epsilon \right)^{\ell(f_{i}^{(t)}, y_{t})} = \left\{\begin{array}{cc}w_{i}^{(t)}& \text{ if } f_{i}^{(t)} = y_{t}\\ w_{i}^{(t)}\,(1 - \epsilon)& \text{ if } f_{i}^{(t)} \neq y_{t} \end{array}\right.$$
>	- The *forecaster* incurs a loss $$\ell(\hat{y}_{t}, y_{t}) := \mathbb{1}\left\{\hat{y}_{t}\neq y_{t} \right\} .$$


- [[Prediction with Expert Advice]]
- [[Characteristic Function of Set]]



## Explanation



## Exponential



-----------
##  Recommended Notes and References


- [[Exponential Weights Algorithm for Convex Loss]]
- [[Sequential Game Perspective for AdaBoost]]

- [[Convex Function]]

- [[Prediction Learning and Games by Cesa-Bianchi]] pp 5, 36
- [[Foundations of Machine Learning by Mohri]] pp 150 - 152
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 253 - 255