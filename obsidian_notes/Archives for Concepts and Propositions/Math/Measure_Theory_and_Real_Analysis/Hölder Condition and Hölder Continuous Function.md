---
tags:
  - concept
  - math/real_analysis
keywords:
  - hölder_condition
  -  hölder_continuous_function
topics:
  - real_analysis
name: Hölder Condition and Hölder Continuous Function
date of note: 2024-06-12
---

## Concept Definition

>[!important]
>**Name**: Hölder Condition and Hölder Continuous Function

>[!important] Definition
>Let $(\mathcal{X}, d_{X})$ and $(\mathcal{Y}, d_{Y})$ be two *metric spaces*.
>
>A function $f: \mathcal{X} \to \mathcal{Y}$ satisfies a **Hölder condition**, or **Hölder continuous**, when there exist some real number $C \ge 0$ and $0 < \alpha \le 1$, such that 
>$$d_{Y}(f(x), f(y)) \le C\, \left( d_{X}(x, y) \right)^{\alpha}.$$
>for any $x, y \in \mathcal{X}$

- [[Metric Space]]
- [[Continuous Function]]

## Explanation

>[!info]
>If $\alpha=1$, the function is [[Lipschitz Continuous Function]].

>[!important]
>Relationship between other continuity conditions
>$$
>\text{continuouly differentiable }\subset \text{ Lipschitz continuous }\subset \text{ Hölder continuous } \subset \text{ uniformly continuous } \subset \text{ continuous }
>$$

- [[Summary of Spaces of Continuous Functions]]






-----------
##  Recommended Notes and References

- [[Continuous Function]]
- [[Lipschitz Continuous Function]]
- [[Absolutely Continuous Function]]
- [[Uniform Continuity Theorem]]
- [[Hölder Space]]

- [[Sample Path of Brownian Motion]]


- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]
- Wikipedia [Hölder Condition](https://en.wikipedia.org/wiki/H%C3%B6lder_condition)