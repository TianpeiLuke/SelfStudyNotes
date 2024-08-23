---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/boosting
keywords:
  - exponential_loss
  - adaboost
topics:
  - boosting
  - machine_learning_models
name: Exponential Loss Minimization for AdaBoost
date of note: 2024-07-29
---

## Concept Definition

>[!important]
>**Name**: Exponential Loss Minimization for AdaBoost

![[AdaBoost Algorithm#^1982f3]]

>[!important] Definition
>The **exponential loss** is defined by $$L(y, f(x)) = \exp \left( - y f(x) \right)$$ where $f: \mathcal{X} \to \mathcal{Y}$.

>[!important] Definition
>Given a collection of **binary labeled data** $\left\{ (x_{i}, y_{i}), \; i=1 \,{,}\ldots{,}\, m\right\}$ where $x_{i}\in \mathcal{X}$ and $y_{i}\in \left\{ -1, +1 \right\},$  the **exponential loss minimization** solves the following problem
>$$
>\min_{F \in \mathcal{F}} \frac{1}{m}\sum_{i=1}^{m}\exp \left( -y_{i} F(x_{i})\right) = \frac{1}{m}\sum_{i=1}^{m}\exp \left( -y_{i} \sum_{t=1}^{T}\alpha_{t}\,h_{t}(x_{i})\right). 
>$$
>where $\mathcal{F}$ is the class of functions that is a *combination* of $h_{t}\in \mathcal{H}$ and $$F(x) := \sum_{t=1}^{T}\alpha_{t}\,h_{t}(x).$$
>
>Note that the *exponential loss* is a **surrogate loss** for the **empirical loss**.
>$$
>\mathbb{1}\left\{ F(x_{i}) \neq y_{i} \right\} = \mathbb{1}\left\{ y_{i}F(x_{i}) \le 0 \right\} \le \exp \left( - y_{i}F(x_{i}) \right)
>$$
>Therefore, solving the exponential loss minimization leads to the *empirical risk minimization*.

- [[Surrogate Loss Minimization]]
- [[Characteristic Function of Set]]
- [[Empirical Risk Minimization]]

### AdaBoost as Greedy Stagewise Exponential Loss Minimization

>[!important] Proposition
>The **AdaBoost** algorithm is a **greedy algorithm** that minimizes the **exponential loss**. 
>
>In particular, it works as follows:
>- *Require*: a collection of **binary labeled data** $\left\{ (x_{i}, y_{i}), \; i=1 \,{,}\ldots{,}\, m\right\}$ where $x_{i}\in \mathcal{X}$ and $y_{i}\in \left\{ -1, +1 \right\}$
>- *Initialize*: $F_{0} = 0$.
>- For $t= 1 \,{,}\ldots{,}\,T:$
>	- Choose $h_{t}\in \mathcal{H}$ and $\alpha_{t}\in \mathbb{R}$ so that $$(h_{t}, \alpha_{t}) \in \arg\min_{(h, \alpha)}\left\{ \frac{1}{m}\sum_{i=1}^{m}\exp \left( -y_{i}\left( F_{t-1}(x_{i}) + \alpha\,h(x_{i}) \right) \right) \right\} $$
>	- Update $$F_{t} = F_{t-1} + \alpha_{t}\,h_{t}$$
>- *Output*: $F_{T}.$

^8d14db

- [[Forward Stagewise Additive Modeling]]


### Dual Formulation and Minimizing the Log-Partition Function

![[Partition Function for AdaBoost#^bc0a1f]]

![[Partition Function for AdaBoost#^7a663d]]

>[!important]
>For any round $t$, and for all examples $i$, 
>$$
>\frac{1}{m}\exp \left( -y_{i} F_{t-1}(x_{i})\right) = D_{t}(i)\,\left( \prod_{s=1}^{t-1}Z_{s} \right)
>$$
>where 
>- $D_{1}(i) = \frac{1}{m}.$
>- $D_{t}$ is the sample weight updated at round $t$ for the **AdaBoost.** $$D_{t}(i) = \frac{D_{t-1}(i)\,\exp\left( -\alpha_{t-1}\,y_{i}\,h_{t-1}(x_{i}) \right)}{Z_{t-1}}$$ 
>- $Z_{t}$ is the **partition function** at round $t$.

- [[Partition Function for AdaBoost]]
- [[Training Error Bound for AdaBoost]]

>[!info]
>$$
>\begin{align*}
> \frac{1}{m}\sum_{i=1}^{m}\exp \left( -y_{i}F_{t}(x_{i}) \right) &= \frac{1}{m}\sum_{i=1}^{m}\exp \left( -y_{i}\left( F_{t-1}(x_{i}) + \alpha_{t}\,h_{t}(x_{i}) \right) \right) \\
> &= \sum_{i=1}^{m}D_{t}(i)\left( \prod_{s=1}^{t-1}Z_{s} \right)\exp \left( - \alpha_{t}\,y_{i}\,h_{t}(x_{i}) \right) \\
> &\propto \sum_{i=1}^{m}D_{t}(i)\exp \left( - \alpha_{t}\,y_{i}\,h_{t}(x_{i}) \right) := Z_{t}
>\end{align*}
>$$

>[!important] Definition
>At round $t$, given $D_{t}$ and $h_{t}$, the **exponential loss minimization** problem is **equivalent** to minimizing the **(log) partition function** $Z_{t}$
>$$
> \min_{\alpha}\, \log Z_{t} = \log  \sum_{i=1}^{m}D_{t}(i)\exp \left( - \alpha_{t}\,y_{i}\,h_{t}(x_{i}) \right)
>$$



## Explanation

>[!important] 
>It is easy to show that 
>$$
>f^{*}(x) := \arg\max_{f(x)} \mathbb{E}_{ Y|x }\left[ e^{- Y\, f(x)} \,\Big|\,x \right] = \frac{1}{2}\log \frac{\mathcal{P}(Y= 1 | x)}{\mathcal{P}(Y=-1 | x)}.
>$$
>Thus the estimation of Adaboost is estimating **one-half** of the **log-odds** of $\mathcal{P}(Y=1|x).$






-----------
##  Recommended Notes and References


- [[Convex Optimization Problem]]
- [[Incremental Algorithm]]
- [[Incremental Gradient Algorithm]]
- [[Incremental Aggregated Gradient Algorithm]]


- [[AdaBoost Algorithm]]
- [[Empirical Risk Minimization]]
- [[Log-Partition Function of Exponential Family]]


- [[Foundations of Machine Learning by Mohri]]
- [[Boosting Foundations and Algorithms by Schapire]]  pp 177
- [[Elements of Statistical Learning by Hastie]] pp  343 - 350