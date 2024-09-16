---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
  - math/topology
keywords:
  - norm
  - normed_space
topics:
  - functional_analysis
  - linear_algebra
name: norm and normed space
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Semi-Norm and Norm


>[!important] Definition
>A **semi-norm** on a vector space $X$ is a mapping $q: X\rightarrow \mathbb{R}_{+}$ satisfying the following conditions: 
> 1. **homogeneity**: $q(\gamma \mathbf{x}) = |\gamma| q(\mathbf{x})$;
> 2. **the triangle inequality**: $q(\mathbf{x}+\mathbf{y})\le q(\mathbf{x})+ q(\mathbf{y})$.
>
>If furthermore 
> 3. **positive definiteness/positiveness** $q(\mathbf{x})=0 \Rightarrow \mathbf{x}=0$, 
>     
>then $q$ is a **norm**.

^376595


>[!info]
> A **metric** $d: X\times X \rightarrow \mathbb{R}_{+}$ that **induced from a norm** is given by $$d_{\theta}(\mathbf{x}, \mathbf{y})= q_{\theta}(\mathbf{y}-\mathbf{x}),\; \forall \mathbf{x,y}\in X.$$



>[!important]
>**Name**:  Normed Linear Space

>[!important]
>A **normed linear space** is a *vector space*, $V$, over $\mathbb{R}$ (or $\mathbb{C}$) and a function, $\|\cdot\|: V \rightarrow \mathbb{R}$ which satisfies:
> 
> 1. **Non-Negativity**: $\|v\| \ge 0$ for all $v$ in $V$;
> 2. **Positive Definiteness**: $\|v\| = 0$ if and only if $v = 0$;
> 3. **Absolute Homogeneity**: $\|\alpha v\| = |\alpha|\|v\|$ for all $v$ in $V$ and $\alpha$ in $\mathbb{R}$ (or $\mathbb{C}$)
> 4. **Subadditivity / Triangle Inequality** $\| v + w\| \le \| v\| + \| w\|$ for all $v$ and $w$ in $V$
> 
> We denote the **normed linear space** as $(V, \|\cdot\|)$.


## Explanation

>[!important]
>Every *normed vector space* is a **metric space**. 
>
>The metric $d: X \times X \to \mathbb{R}$ is defined as 
>  
> $$
>\begin{align*}
>d(x, y) &= \lVert x - y \rVert, \quad \forall x, y \in X. 
>\end{align*}
> $$

>[!info]
>Normed vector space only defines the notion of **distance**, but **not angle**. So it does not equip **Euclidean  geometry**.










-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Metric Space]]
- [[Inner Product Space]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)