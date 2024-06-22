---
tags:
  - concept
  - math/functional_analysis
  - math/convex_analysis
  - optimization/theory
keywords:
  - hahn_banach_theorem
  - mazur_theorem
topics:
  - functional_analysis
  - convex_analysis
name: Geometric Form of The Hahn-Banach Theorem
date of note: 2024-05-08
---

## Theorem

>[!important]
>**Name**:   *Geometric Form* of **The Hahn-Banach Theorem** or **Mazur's Theorem** or **Ascoli–Mazur Theorem**

>[!important] Mazur's Theorem (Geometric Form of The Hahn-Banach Theorem)
>Let $K$ be a **convex set** having a *nonempty interior* in a real *normed vector space* $X$. Suppose $V$ is a **linear variety** in $X$ *containing no interior points* of $K$. 
>
>Then there is a **closed hyperplane** in $X$ **containing $V$** but **containing no interior points** of $K$; i.e., there is an element $f \in X^{*}$ and a constant $c$ such that 
>$$
>f(v) = c, \quad \forall\, v \in V,
>$$
>and 
>$$
>f(k) < c, \quad \forall\, k \in K.
>$$

- The Hahn-Banach Theorem is the basis to develop the Mazur's Theorem. See [[Hahn-Banach Theorem Extension Form]]
- [[Separation Theorem]] is an equivalent theorem but formulated in terms of optimization. 
- Use Minkowski function. See [[Minkowski Functional]]


## Explanation

>[!info]
>The Hahn-Banach Theorem confirms the existence of a **linear separation** between a *convex set (with interior)* and *a point* not in the convex set.

- It is an extension of [[Urysohn Lemma]], which only states the existence of a continuous function that separate disjoint closed sets.

## Other Form of Geometric Hahn-Banach Theorem

>[!info]
>The **geometric form** of the *Hahn-Banach theorem*, in simplest form, says that 

>[!important] Supporting Hyperplane Theorem
>If $x$ is *not an interior point* of a **convex set** $K$ which *contains interior points*, there is a **closed hyperplane** $H$ *containing* $x$ such that $K$ *lies on* **one side** of $H$.

- [[Locally Convex Space]]
- [[Supporting Hyperplane of Convex Set]]
- [[Optimization by Vector Space Methods by Luenberger]]


>[!info] Equivalent Theorem
>Given a **convex set** $K$ containing an interior point, and given a point $x_0$ *not in* $\mathring{K}$, there is a **closed hyperplane** *containing* $x_0$ but *disjoint* from $\mathring{K}$.


>[!info]
>If $X$ is a **$n$-dimensional** vector space, then there are **at most $n+1$** affine hyperplanes that contain $K$ in one side.

- [[Carathéodory Theorem for Convex Hull]]



-----------
##  Recommended Notes and References

- [[Convex Set]]
- [[Urysohn Lemma]]


- [[Functional Analysis by Reed]]
- [[Real Analysis by Royden]] pp 292
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Optimization by Vector Space Methods by Luenberger]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)