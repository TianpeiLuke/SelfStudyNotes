---
tags:
  - concept
  - math/topology
  - statistics/concentration_inequality
  - math/measure_theory
keywords:
  - surface_area_sets
topics:
  - topology
  - measure_theory
  - concentration_inequality
name: Surface Area of Sets
date of note: 2024-05-24
---

## Concept Definition

>[!important]
>**Name**: Surface Area of Sets


>[!important] Definition
>Let $A \subset \mathbb{R}^n$ be a *measurable set* and denote by $\text{Vol}(A)$ its *Lebesgue measure*. 
>
>The **surface area** *of* $A$ is defined by
>$$
> \begin{align*}
> \text{Vol}(\partial A) &= \lim\limits_{t \to 0}\frac{\text{Vol}(A_t) - \text{Vol}(A)}{t},
> \end{align*}
>$$  
>provided that the limit exists. 
>
>Here $A_t$ denotes **the $t$-blowup** of $A$.

- [[Blowup of Sets]]
- [[Minkowski Sum of Sets]]
- [[Metric Space]]
- [[Lebesgue Measure]]

## Explanation





-----------
##  Recommended Notes and References

- [[Lebesgue Measure]]

- [[Blowup of Sets]]
- [[Minkowski Sum of Sets]]
- [[Metric Space]]

- [[Concentration Inequalities by Boucheron]]