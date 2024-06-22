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

>[!important]
>It is important to distinguish concepts of **metric** from **norm** and **inner product**
>
>- A metric is a pure **topological property**
>- A norm and inner product require additional **algebraic structure** so that the set $M$ is a *vector space*.


## Example

>[!example] 
>Any **normed vector space** $(V, \lVert \cdot \rVert)$  is a metric space with metric $$d(x, y) := \lVert x - y \rVert.$$

- [[Norm and Normed Space]]

>[!example] 
>Any **inner product space** $(V, \left\langle \cdot , \cdot \right\rangle)$  is a metric space with metric $$d(x, y) := \sqrt{\left\langle x - y , x - y \right\rangle}.$$

- [[Inner Product Space]]


>[!example]
>Given a **Polish space** $\mathcal{X}$, for each $p \ge 1$,  define a bounded space $\mathscr{P}_{p}(\mathcal{X})$ where 
>$$
>\mathscr{P}_{p}(\mathcal{X}) := \left\{ \mu \in \mathcal{M}_{+}(\mathcal{X}):  \int_{\mathcal{X}} |x|^p d\mu < \infty  \right\} \subset \mathcal{M}_{+}(\mathcal{X}).
>$$
>
>For $p \ge 1$, the **$p$-Wasserstein distance**  between measures $\alpha, \beta \in \mathcal{M}_{+}(X)$ is defined as 
>$$
>\mathcal{W}_{p}(\alpha, \beta) := \left( \min_{\pi \in \Pi(\mathcal{X} \times \mathcal{Y})} \mathbb{E}_{(X,Y) \sim \pi}\left[ d^p(X, Y) \right]  \right)^{\frac{1}{p}}
>$$ 
>where $d(x, y)$ is a metric in $\mathcal{X}$.
>
>Then the **Wasserstein space**  $\mathbb{W}_{p} := (\mathscr{P}_{p}(\mathcal{X}), \mathcal{W}_{p})$ is a *metric space*.







-----------
##  Recommended Notes and References

- [[Norm and Normed Space]]
- [[Inner Product Space]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)