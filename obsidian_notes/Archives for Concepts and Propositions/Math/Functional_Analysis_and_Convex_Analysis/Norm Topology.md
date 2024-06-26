---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
  - math/topology
keywords:
  - norm_topology
topics:
  - functional_analysis
  - linear_algebra
name: Norm Topology
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  Norm Topology


>[!important] Definition
>Let $(X, \lVert \cdot \rVert )$ be a *normed vector space.* The **norm topology** of $X$ is the *natural topology* on *metric space* where the metric $d: X \times X \to \mathbb{R}$ is defined as $d(x, y) := \lVert x - y \rVert$.
>
>That is, the **basis** of *the norm topology* is the **$\epsilon$-ball**  
> $$
> \begin{align}
> B_{\lVert \cdot \rVert }(x, \epsilon) := \left\{ y \in X: \lVert y -x \rVert < \epsilon     \right\}, \quad \forall x\in X, \epsilon >0
> \end{align}
> $$

- [[Metric Topology and epsilon-ball]]

## Explanation





-----------
##  Recommended Notes and References

- [[Norm and Normed Space]]
- [[Basis of Topology]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)