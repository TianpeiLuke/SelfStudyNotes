---
tags:
  - concept
  - math/convex_analysis
  - math/information_theory
keywords:
  - log_sum_inequality
topics:
  - convex_analysis
name: Log-Sum Inequality
date of note: 2024-05-08
---

## Concept Definition

>[!important]
>**Name**:  Log-Sum Inequality


>[!important] Log-Sum Inequality
>For non-negative numbers $\boldsymbol{a} = [a_{1} \,{,}\ldots{,}\, a_{n}]$ and $\boldsymbol{b} = [b_{1} \,{,}\ldots{,}\, b_{n}]$, 
>$$
>\begin{align*}
>\sum_{i=1}^n a_{i} \log\left( \frac{a_{i}}{b_{i}}\right) &\ge  \left(\sum_{i=1}^n a_{i}\right) \log\left( \frac{\sum_{i=1}^n a_{i}}{\sum_{i=1}^n b_{i}}\right),
\end{align*}
>$$
>with equality if and only if $a_{i} / b_{i} = const$.

^469056

- [[Jensen Inequality]]


## Explanation

>[!info]
>$$
>\varphi(x) = -\log(x)
>$$
>is a convex function. 

>[!info] Proof
>by Jenson's inequality, 
>$$
>\begin{align*}
>\varphi \left( \frac{\sum_{i=1}^n r_{i}x_{i} }{\sum_{i=1}^n r_{i}}\right) &\le  \frac{\sum_{i=1}^n r_{i} \varphi\left(x_{i}\right)   }{\sum_{i=1}^n r_{i}}
\end{align*}
>$$
>where 
>$$
>r_{i} = \frac{b_{i}}{\sum_{i=1}^n b_{i}}, \quad x_{i} = \frac{a_{i}}{b_{i}}
>$$




-----------
##  Recommended Notes and References

- Wikipedia [Jensen's_inequality](https://en.wikipedia.org/wiki/Jensen%27s_inequality)
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)