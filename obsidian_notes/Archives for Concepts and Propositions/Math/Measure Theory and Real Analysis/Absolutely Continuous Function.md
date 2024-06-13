---
tags:
  - concept
  - math/real_analysis
keywords:
  - absolutely_continuous_function
topics:
  - real_analysis
name: Absolutely Continuous Function
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Absolutely Continuous Function

>[!important] Definition
>A function $F : \mathbb{R} \rightarrow \mathbb{R}$ is said to be **absolutely continuous** if, for every $\epsilon > 0$, there exists a $\delta > 0$ such that $$\sum_{j=1}^{n}\lvert F(b_j) - F(a_j) \rvert  \le \epsilon$$ whenever $(a_1, b_1) \,{,}\ldots{,}\, (a_n, b_n)$ is a *finite collection* of *disjoint intervals* of **total length** $$\sum_{j=1}^{n}|b_j - a_j| \le \delta.$$


## Explanation


## Properties


>[!important] Proposition
>The followings statements are true:
>
>- Every **absolutely continuous** function is **uniformly continuous** and therefore **continuous.**
> 
>- Every **absolutely continuous** function is of **bounded variation** on every **compact interval** $[a, b]$. 
>	- Thus, by the *Local Bounded Variation Differentiation Theorem*, absolutely continuous functions are **differentiable almost everywhere**.
> 
>- Every **Lipschitz continuous** function is **absolutely continuous**.
>- The **sum** or **product** of two **absolutely continuous functions** on an interval $[a, b]$ remains **absolutely continuous**.

- [[Uniform Continuity Theorem]]
- [[Bounded Variation Function]]
- [[Continuous Function]]


>[!example]
>The function $x \mapsto \sqrt{x}$ is **absolutely continuous**, but **not Lipschitz continuous**, on the interval $[0, 1]$.

>[!example]
>**The Cantor function** is defined as 
>
>It is 
>- **continuous**, 
>- **monotone**, and 
>- **uniformly continuous**, 
>- but **not absolutely continuous**, on $[0, 1]$.


## Differentiability of Indefinite Integral


>[!important] Proposition
> If $f: \mathbb{R} \rightarrow \mathbb{R}$ is **absolutely integrable**, then
> - the *indefinite integral* $$F(x) := \int_{[-\infty,x]} f(y) dy$$ is **absolutely continuous**, and
> - $F$ is **differentiable almost everywhere** with $$F'(x) = f(x)$$ for *almost every* $x$.


## Measure Projection

>[!important] Proposition
>**Absolutely continuous functions** map **null sets** to **null sets**.
>
>If $F : \mathbb{R} \rightarrow \mathbb{R}$ is **absolutely continuous** and $E$ is a **null set** $m(E) = 0$,  then $$F(E) := \set{F(x): x \in E}$$ is also a **null set**.

^9e4dc0

- [[Absolute Continuity for Measures]]







-----------
##  Recommended Notes and References


- [[Absolute Continuity for Measures]]

- [[Uniform Topology on Metric Spaces]]
- [[Bounded Variation Function]]
- [[Continuous Function]]