---
tags:
  - concept
  - machine_learning/boosting
  - machine_learning/models
  - machine_learning/theory
keywords:
  - log_partition_function
  - partition_function
  - exponential_loss
  - adaboost
topics:
  - boosting
  - machine_learning_theory
name: Partition Function for AdaBoost
date of note: 2024-08-01
---

## Concept Definition

>[!important]
>**Name**: Partition Function for AdaBoost

![[AdaBoost Algorithm#^1982f3]]

>[!important] Definition
>The **partition function** or the **normalization factor** corresponding to the **AdaBoost** at round $t$ is defined as 
>$$
>Z_{t} :=  \widehat{\mathbb{E}}_{ (X, Y)\sim D_{t} }\left[\, e^{ - \alpha_{t}\, Y\,h_{t}(X)} \,\right] = \frac{1}{m}\sum_{i=1}^{m}D_{t}(i)\,e^{ - \alpha_{t}\, y_{i}\,h_{t}(x_{i})}
>$$

- [[Log-Partition Function of Exponential Family]]


### Product of Partition Functions

>[!info] 
>Unraveling the recurrence that defined $D_{t+1}$ in terms of $D_{t}$, we have
>$$
>\begin{align*}
> D_{T+1}(i) &= D_{1}(i) \cdot  \prod_{s=1}^{T} \frac{1}{Z_{s}}\,\exp \left( -\alpha_{s}\, y_{i}h_{s}(x_{i}) \right) \\
> &= D_{1}(i) \cdot \frac{1}{\prod_{s=1}^{T}Z_{s}} \exp\left( -y_{i} \sum_{s=1}^{T}\alpha_{s}\, h_{s}(x_{i}) \right) \\[5pt]
> &= D_{1}(i) \cdot \frac{1}{\prod_{s=1}^{T}Z_{s}} \exp\left( -y_{i} F(x_{i}) \right).
>\end{align*}
>$$
>Thus
>$$
>D_{T+1}(i)\,\prod_{s=1}^{T}Z_{s} = D_{1}(i)\exp\left( -y_{i} F(x_{i}) \right).
>$$

^bc0a1f

>[!info]
>$$
>\begin{align*}
>  \mathbb{E}_{ D_{1} }\left[ \mathbb{1}\left\{ H(x) \neq y \right\} \right] &= \sum_{i=1}^{m}D_{1}(i)\; \mathbb{1}\left\{ H(x_{i}) \neq y_{i} \right\}  \\
>  &\le \sum_{i=1}^{m}D_{1}(i)\;e^{-y_{i}\,F(x_{i})}\\
>  &= \sum_{i=1}^{m}D_{T+1}(i)\,\prod_{s=1}^{T}Z_{s} \\
>  &= \prod_{s=1}^{T}Z_{s} 
>\end{align*}
>$$

>[!important]
>The **product of partition functions** up to $T$ rounds is equal to 
>$$
>\begin{align*}
>\prod_{s=1}^{T}Z_{s} &= \sum_{i=1}^{m}D_{1}(i)\exp \left( - y_{i} F(x_{i}) \right)\\
>&=  \mathbb{E}_{ D_{1} }\left[ e^{- Y\,F(X)} \right]
>\end{align*}
>$$
>where $$F(x) = \sum_{t=1}^{T}\alpha_{t}\,h_{t}(x).$$

^7a663d


### Partition Function via Weighted Error Rate

>[!info]
>$$
>\begin{align*}
>Z_{t} &:= \sum_{i=1}^{m}D_{t}(i)\,e^{ - \alpha_{t}\, y_{i}\,h_{t}(x_{i})}\\[5pt]
>&= \sum_{i: h_{t}(x_{i}) = y_{i}}^{m}D_{t}(i)\,e^{ - \alpha_{t}} + \sum_{i: h_{t}(x_{i}) \neq y_{i}}^{m}D_{t}(i)\,e^{ \alpha_{t}}\\[5pt]
>\end{align*}
>$$


>[!important]
>$$
>Z_{t} = e^{-\alpha_{t}}(1 -  \epsilon_{t}) + e^{\alpha_{t}}\,\epsilon_{t}
>$$
>where $$\epsilon_{t} = \sum_{i=1}^{m}D_{t}(i)\,\mathbb{1}\left\{ h_{t}(x_{i}) \neq y_{i} \right\}.$$


## Explanation





-----------
##  Recommended Notes and References


- [[Training Error Bound for AdaBoost]]
- [[Exponential Loss Minimization for AdaBoost]]
- [[AdaBoost Algorithm]]

- [[Log-Partition Function of Exponential Family]]

- [[Boosting Foundations and Algorithms by Schapire]] pp 55, 179
- [[Elements of Statistical Learning by Hastie]] 