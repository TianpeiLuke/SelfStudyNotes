---
tags:
  - concept
  - math/measure_theory
  - statistics/concentration_inequality
keywords:
  - prekopa-leindler_inequality
topics:
  - measure_theory
  - concentration_inequality
name: Prekopa-Leindler Inequality
date of note: 2024-05-24
---

## Concept Definition

>[!important]
>**Name**: Prékopa–Leindler inequality


>[!important] Prékopa–Leindler Inequality
>Let $\lambda \in (0, 1)$, and let $f, g, h : \mathbb{R}^n \to [0, \infty)$ be **non-negative measurable functions** such that for all $x, y \in \mathbb{R}^n$,
>$$
> \begin{align*}
> h\left(\lambda x + (1- \lambda) y\right) &\ge f(x)^{\lambda}g(y)^{1-\lambda}.
> \end{align*}
>$$  
>
>Then
>$$
> \begin{align}
> \int_{\mathbb{R}^n} h(x) dx &\ge \left(\int_{\mathbb{R}^n} f(x) dx\right)^{\lambda}\left(\int_{\mathbb{R}^n} g(x) dx\right)^{1-\lambda}.   
> \end{align}
>$$ 

^63fb27


- [[Absolutely Convergent Integration]]
- [[Measurable Function]]
- [[Lebesgue Measure]]
- [[Convex Combination]]
- [[Log-Concave and Log-Convex Function]]
- [[Brunn-Minkowski Inequality]]

## Explanation





## Corollary

![[Weak Brunn-Minkowski Inequality#^c23089]]

- [[Weak Brunn-Minkowski Inequality]]



-----------
##  Recommended Notes and References

- [[Brunn-Minkowski Inequality]]

- [[Absolutely Convergent Integration]]
- [[Measurable Function]]
- [[Lebesgue Measure]]


- [[Concentration Inequalities by Boucheron]]