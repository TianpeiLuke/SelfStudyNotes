---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - metric_space
topics:
  - functional_analysis
  - topology
name: metric space
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Metric Space


>[!important] Defintion
>A **metric space** is a set $M$ and a real-valued function $d(\cdot , \cdot): M \times M \rightarrow \mathbb{R}$  which satisfies: $\forall x, y, z \in M$
> 
> 1. **Non-Negativity** $d(x, y) \ge 0$
> 2. **Definiteness** $d(x, y) = 0$ if and only if $x = y$
> 3. **Symmetric** $d(x, y) = d(y, x)$
> 4. **Triangle Inequality** $d(x, z) \le d(x, y) + d(y, z)$
>
>The function $d$ is called a **metric** on $M$. The metric space $M$ equipped with metric $d$ is denoted as $(M, d)$.


## Explanation





-----------
##  Recommended Notes and References

- [[Norm and Normed Space]]
- [[Inner Product Space]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)