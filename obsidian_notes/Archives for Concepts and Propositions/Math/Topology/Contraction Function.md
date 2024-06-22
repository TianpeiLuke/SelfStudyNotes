---
tags:
  - concept
  - math/topology
  - math/functional_analysis
keywords:
  - contraction_function
topics:
  - topology
name: contraction function
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Contraction Function


>[!important] Definition
>Let $(X, d_{X})$  be a *metric spaces*. A function $f: X \to X$ is a **contraction map** (or **contraction** or **contractor**) if there exists a *constant number* $0 \le k \le 1$ such that for *every* two points $x, y \in X$
>$$
>d_{X}(f(x), f(y)) \le  k\, d_{X}(x, y).
>$$

>[!important]
>If there exists $k<1$ for which
>$$
>d_{X}(f(x), f(y)) \le  k\, d_{X}(x, y),
>$$
>the map $f$ is called **strict contraction map**

## Explanation

>[!important]
>By the [Banach fixed-point theorem](https://en.wikipedia.org/wiki/Banach_fixed-point_theorem "Banach fixed-point theorem") states that *every contraction mapping* on a [non-empty](https://en.wikipedia.org/wiki/Empty_set "Empty set") [complete metric space](https://en.wikipedia.org/wiki/Complete_metric_space "Complete metric space") has a **unique fixed point**.

- [[Contraction Map Principle]]


-----------
##  Recommended Notes and References

- [[Lipschitz Continuous Function]]
- [[Metric Space]]

- [[Fixed Point of Map]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)


- [[Functional Analysis by Reed]]
- [[Real Analysis by Royden]]