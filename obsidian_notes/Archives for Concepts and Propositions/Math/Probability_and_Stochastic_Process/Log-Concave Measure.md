---
tags:
  - concept
  - math/probability
  - math/measure_theory
keywords:
  - log_concave_measure
topics:
  - probability
  - measure_theory
name: Logarithmic Concave Measure
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Log-Concave Measure

![[Log-Concave and Log-Convex Function#^b7fd75]]

![[Log-Concave and Log-Convex Function#^7490df]]

>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be a measurable space. 
>
>A measure $\mu$ is called **logarithmically concave**, if for any $A, B \in \mathscr{F}$, $0 \le \alpha \le 1$, 
>$$
> \mu \left(\alpha A + (1- \alpha) B\right) \ge \mu \left(A\right)^{\alpha}\;\mu \left(B\right)^{1- \alpha}
>$$
>where $A + B$ is *Minkowski sum* of two sets $$A + B =\left\{ a + b:\, \forall a\in A, b\in B \right\}.$$

^81a226

- [[Log-Concave and Log-Convex Function]]
- [[Minkowski Sum of Sets]]

## Explanation

>[!info]
>The c.d.f. of **log-concave distributions** is **log-concave**.

## Maximum Entropy 

>[!important] Proposition
>Every **log-concave distribution** is a solution to a **maximum entropy learning** problem. In other word, 
>$$
>\text{log-concave measure }\implies \text{ maximum entropy measure}
>$$

- [[Maximum Entropy Learning]]
- [[Gibbs measure]]

## Examples

>[!example]
>From [[Weak Brunn-Minkowski Inequality]], we see that the **Lebesgue measure** on $\mathbb{R}^n$ is **log-concave**
>
>Let $A, B \subset \mathbb{R}^n$ be *non-empty* **compact sets**. 
>
>Then for all $\lambda \in [0, 1]$,
>$$
> \begin{align}
> m\left(\lambda A + (1- \lambda) B \right) &\ge m(A)^{\lambda}\; m(B)^{1- \lambda}. 
> \end{align}
> $$



-----------
##  Recommended Notes and References



- [[Convex Set]]
- [[Convex Function]]

- [[Weak Brunn-Minkowski Inequality]]
- [[Gaussian Measure]]
- [[Lebesgue Measure]]

- [[Ehrhard Concave Measure]]

- [[Lectures on Gaussian Processes by Lifshits]]