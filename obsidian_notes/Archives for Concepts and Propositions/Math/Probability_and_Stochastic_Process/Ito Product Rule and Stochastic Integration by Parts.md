---
tags:
  - concept
  - math/stochastic_process
keywords:
  - ito_product_rule
topics:
  - stochastic_process
name: Itô Product Rule
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Itô Product Rule

>[!important] Theorem (Itô's Product Rule)
>Suppose 
>$$
>\begin{align*}
>dX_{1} &= F_{1}\,dt + G_{1}\,dW\\
>dX_{2} &= F_{2}\,dt + G_{2}\,dW
>\end{align*}
>$$
>for $F_{i},G_{i} \in \mathbb{L}^2(0,T).$
>
>Then 
>$$
>\begin{align*}
>d\left( X_{1}\,X_{2} \right) &= X_{2}\,dX_{1} + X_{1}\,dX_{2} + G_{1}\,G_{2}\,dt.
>\end{align*}
>$$
>We refer to above formula as **Itô's product rule** or **product formula.**
>
>The third term 
>$$G_{1}\,G_{2}\,dt$$
>is called the **Itô correction term**.

- [[Stochastic Differential]]
- [[Ito Stochastic Integration]]
- [[Progressively Measurable Stochastic Process]]
- [[Brownian Motion Wiener Process]]
- [[Quadratic Variation and Covariation of Stochastic Process]]


>[!important] Theorem (Itô's Product Rule in multi-dimensional setting)
>Suppose that $X_{t}$ has a *stochastic differential*
>$$
>dX^{i}_{t} = F^{i}\,dt + G^{i}_{t}\,dW_{t},
>$$
>for $F^i, G^i\in \mathbb{L}^2(0,T),$  and $i=1 \,{,}\ldots{,}\,n.$
>
>Then 
>$$
>\begin{align*}
>d\left( X_{1}\,X_{2} \right) &= X_{2}\,dX_{1} + X_{1}\,dX_{2} + \sum_{k=1}^{m}G_{1}^{k}\,G_{2}^{k}\,dt.
>\end{align*}
>$$


## Expansion

>[!important] 
>To remember the product rule,
>we have
>$$
>d\left( X_{1}\,X_{2} \right) = X_{1}\,dX_{2} + X_{2}\,dX_{1} + dX_{1}\,dX_{2}
>$$
>where we use the following formula
>$$
>\begin{align*}
>(dt)^2 &= 0\\
>dt\,dW^k &=0, \quad k=1 \,{,}\ldots{,}\,m\\
>dW^k\,dW^l &= \delta_{k,l}\,dt, \quad k,l=1 \,{,}\ldots{,}\,m
>\end{align*}
>$$


>[!important]
>The integrated version is
>$$
>\begin{align*}
> \int_{s}^{t}X_{2}\,dX_{1} &=  - \int_{0}^{t} X_{1}\,dX_{2} -  \int_{0}^{t} G_{1}\,G_{2}\,dt  +  X_{1}(t)\,X_{2}(t) -  X_{1}(s)\,X_{2}(s).
>\end{align*}
>$$
>It is the **Itô integration-by-part formula**.

- [[Integration by Parts]]
- [[Integration by Parts of Itô Stochastic Integration]]

>[!important]
>If $G_{1} = 0$ or $G_{2} = 0$, the **corrected term vanishes** and the integrated version is
>$$
>\begin{align*}
> \int_{s}^{t}X_{2}\,dX_{1} &=  - \int_{0}^{t} X_{1}\,dX_{2} +  X_{1}(t)\,X_{2}(t) -  X_{1}(s)\,X_{2}(s).\\
> \implies \int_{s}^{t}X_{2}\,F_{1}\,dt &=  - \int_{0}^{t} X_{1}\,F_{2}\,dt +  X_{1}(t)\,X_{2}(t) -  X_{1}(s)\,X_{2}(s)
>\end{align*}
>$$
>It is the ordinary **integration-by-part formula**.







-----------
##  Recommended Notes and References

- [[Ito Chain Rule and Ito Formula]]

- [[Ito Stochastic Integration]]
- [[Ito Stochastic Integration of Step Process]]
- [[Progressively Measurable Stochastic Process]]
- [[Brownian Motion Wiener Process]]



- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]