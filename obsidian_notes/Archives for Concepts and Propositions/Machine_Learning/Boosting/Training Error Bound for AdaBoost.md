---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/boosting
keywords:
  - adaboost
  - training_error_bound_adaboost
topics:
  - machine_learning_theory
name: Training Error Bound for AdaBoost
date of note: 2024-07-29
---

## Concept Definition

>[!important]
>**Name**: Training Error Bound for AdaBoost

![[AdaBoost Algorithm#^1982f3]]

![[Empirical Risk Minimization#^a84128]]


>[!important] Theorem
>Assume $\epsilon_{t} < \frac{1}{2}$ for all $t$ and let $$\gamma_{t} = \frac{1}{2} - \epsilon_{t}.$$ Let $D_{1}$ be an arbitrary *initial distribution* over the *training set*.
>
>Then the **weighted training error** of **AdaBoost**’s combined classifier $H$ with respect to $D_{1}$ is **bounded** as
>$$
>  L_{ D_{1} }\left(H\right) \le \prod_{t=1}^{T}\sqrt{ 1 - 4 \gamma_{t}^2 } \le \exp \left( -2\sum_{t=1}^{T}\gamma_{t}^2 \right).
>$$

- [[Empirical Risk Minimization]]
- [[Partition Function for AdaBoost]]

>[!info] Proof
>Let $$F(x) = \sum_{t=1}^{T}\alpha_{t}\,h_{t}(x).$$ 


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


>[!info]
>Note that 
>$$
>\mathbb{1}\left\{ H(x) \neq y \right\} = \mathbb{1}\left\{ y\,F(x) \le 0 \right\} \le e^{- y\,F(x)}
>$$

>[!info]
>$$
>\begin{align*}
>  \mathbb{E}_{ D_{1} }\left[ \mathbb{1}\left\{ H(x) \neq y \right\} \right] &= \sum_{i=1}^{m}D_{1}(i)\; \mathbb{1}\left\{ H(x_{i}) \neq y_{i} \right\}  \\
>  &\le \sum_{i=1}^{m}D_{1}(i)\;e^{-y_{i}\,F(x_{i})}\\
>  &= \sum_{i=1}^{m}D_{T+1}(i)\,\prod_{s=1}^{T}Z_{s} \\
>  &= \prod_{s=1}^{T}Z_{s} 
>\end{align*}
>$$

>[!info]
>$$
>\begin{align*}
>Z_{t} &:= \sum_{i=1}^{m}D_{t}(i)\,e^{ - \alpha_{t}\, y_{i}\,h_{t}(x_{i})}\\[5pt]
>&= \sum_{i: h_{t}(x_{i}) = y_{i}}^{m}D_{t}(i)\,e^{ - \alpha_{t}} + \sum_{i: h_{t}(x_{i}) \neq y_{i}}^{m}D_{t}(i)\,e^{ \alpha_{t}}\\[5pt]
>&= e^{-\alpha_{t}}(1 -  \epsilon_{t}) + e^{\alpha_{t}}\,\epsilon_{t}\\
>&= e^{-\alpha_{t}}\left( \frac{1}{2} + \gamma_{t} \right) + e^{\alpha_{t}}\left( \frac{1}{2} - \gamma_{t} \right)\\[5pt]
>&= \sqrt{ 1 - 4\gamma_{t}^2 }, \quad \text{ let }\alpha_{t} = \frac{1}{2}\log \left( \frac{\frac{1}{2} + \gamma_{t} }{\frac{1}{2} - \gamma_{t} } \right)
>\end{align*}
>$$

>[!info]
>Thus
>$$
>\begin{align*}
>  \mathbb{E}_{ D_{1} }\left[ \mathbb{1}\left\{ H(x) \neq y \right\} \right] &= \prod_{s=1}^{T}Z_{s} \\
>  &\le \prod_{s=1}^{T}\sqrt{ 1 - 4 \gamma_{s}^2 } \\
>  &\le  \exp \left( -2\sum_{t=1}^{T}\gamma_{t}^2 \right)
>\end{align*}
>$$
>where the last inequality is due to $$1 + x \le e^{x}$$ Q.E.D.

- [[Basic Inequalities and Cramér–Chernoff Method]]


## Explanation





-----------
##  Recommended Notes and References


- [[Partition Function for AdaBoost]]
- [[AdaBoost Algorithm]]
- [[Exponential Loss Minimization for AdaBoost]]

- [[Empirical Risk Minimization]]
- [[Log-Partition Function of Exponential Family]]



- [[Foundations of Machine Learning by Mohri]]
- [[Boosting Foundations and Algorithms by Schapire]]  pp 54 - 57
- [[Elements of Statistical Learning by Hastie]]