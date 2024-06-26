---
tags:
  - concept
  - math/functional_analysis
  - math/stochastic_process
keywords:
  - haar_wavelet_function
  - schauder_function
topics:
  - functional_analysis
  - stochastic_process
name: Schauder Function
date of note: 2024-06-05
---

## Concept Definition

>[!important]
>**Name**: Schauder Function

![[Haar Wavelet Function#^e6b662]]

- [[Haar Wavelet Function]]

>[!important] Definition
>The *indefinite integral* of Haar wavelet function
>$$
>s_{k}(t) := \int_{0}^{t}h_{k}(s)ds
>$$
>is called the **$k$-th Schauder function.**
>
>Note that 
>$$s_{0}(t) = 0, \quad \text{ and } \quad s_{1}(t) = t$$

^8d5f5c


## Explanation


## The Faber–Schauder System

>[!important] Theorem
>The system of Schauder functions $$\{ s_{k}(t),\;\; k=0,1,\,{,}\ldots{,}\, \}$$ forms a **Schauder basis** in the space of *continuous function* $\mathcal{C}[0,1].$
>
>That is, every continuous function $f\in \mathcal{C}[0,1]$ can be **uniquely represented** as 
>$$
>f(t) = a_{0} + \sum_{k=1}^{\infty}a_{k}\,s_{k}(t)
>$$
>in terms of norm topology.

- [[Schauder Basis of Normed Space]]


>[!important] Proposition
>For any $s, t \ge 0$, 
>$$
>\sum_{k=1}^{\infty}s_{k}(t)s_{k}(s) = t \wedge t = \min\{s,t\}
>$$

- [[Continuous Function]]
- [[Schauder Basis of Normed Space]]




-----------
##  Recommended Notes and References

- [[Haar Wavelet Function]]
- [[Coordinate Representation of Brownian Motion]]


- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Introduction to Measure Theory by Tao]]

- [[Introduction to Stochastic Differential Equations by Evans]]

- Wikipedia [Haar wavelet](https://en.wikipedia.org/wiki/Haar_wavelet)