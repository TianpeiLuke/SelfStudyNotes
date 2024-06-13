---
tags:
  - concept
  - math/measure_theory
  - statistics/concentration_inequality
keywords:
  - isoperimetry_theorem
topics:
  - measure_theory
  - concentration_inequality
name: Isoperimetry Theorem
date of note: 2024-05-24
---

## Theorem

>[!important]
>**Name**: Isoperimetry Theorem

>[!important]
>The classical **isoperimetric theorem** in $\mathbb{R}^n$ states that, among *all sets* with  **a given volume**,  **the Euclidean unit ball minimizes the surface area**.  
>
>This theoerm can be formally stated as below:

>[!important] Isoperimetry Theorem
>Let $A \subset \mathbb{R}^n$ be such that its **volume** is *equal to* a unit ball
>$$\text{Vol}(A) = \text{Vol}(B)$$ where $B := \set{x \in \mathbb{R}^n: d(0, x) < 1}$ is an *unit ball*. 
>
>Then for any $t > 0$,  the **$t$-blowup** of sets 
>$$
> \begin{align}
> \text{Vol}(A_t) &\ge  \text{Vol}(B_t). 
> \end{align}
>$$  
>
>Moreover, if $\text{Vol}(\partial A)$ exists, then **the surface area**
>$$
> \begin{align}
> \text{Vol}(\partial A)  &\ge \text{Vol}(\partial B).  
> \end{align}
>$$ 

- [[Blowup of Sets]]
- [[Surface Area of Sets]]

- [[Lebesgue Measure]]

## Explanation







-----------
##  Recommended Notes and References

- [[Blowup of Sets]]
- [[Surface Area of Sets]]

- [[Concentration Inequalities by Boucheron]]