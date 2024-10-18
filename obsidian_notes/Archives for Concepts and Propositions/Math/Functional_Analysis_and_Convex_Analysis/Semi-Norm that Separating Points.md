---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
  - math/topology
keywords:
  - semi-norm
topics:
  - functional_analysis
  - linear_algebra
name: semi-norm that separating points
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Semi-Norm that Separating Points


>[!info] Semi-Norm
>A **semi-norm** on a vector space $X$ is a mapping $q: X\rightarrow \mathbb{R}_{+}$ satisfying the following conditions: 
> 1. **homogeneity**: $q(\gamma \mathbf{x}) = |\gamma| q(\mathbf{x})$;
> 2. **the triangle inequality**: $q(\mathbf{x}+\mathbf{y})\le q(\mathbf{x})+ q(\mathbf{y})$.
>
>If furthermore 
> 3. **positive definiteness/positiveness** $q(\mathbf{x})=0 \Rightarrow \mathbf{x}=0$, 
>     
>then $q$ is a **norm**.

^886fb7

- [[Norm and Normed Space]]

>[!important] Definition
>A family of semi-norms $\{ q_{\alpha} \}_{\alpha\in I}$ is said to **separate points** if 
>$$
>q_{\alpha}(x) = 0, \;\; \forall \alpha \in I \implies x = 0
>$$


## Explanation










-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Metric Space]]
- [[Norm and Normed Space]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)