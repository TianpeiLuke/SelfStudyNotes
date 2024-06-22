---
tags:
  - concept
  - math/functional_analysis
  - math/convex_analysis
  - optimization/theory
keywords:
  - separation_theorem_convex
topics:
  - functional_analysis
  - convex_analysis
name: Eidelheit's Separation Theorem
date of note: 2024-05-08
---

## Theorem

>[!important]
>**Name**:   Eidelheit's Separation Theorem

>[!important] Eidelheit's Separation Theorem
>Let $K_1$ and $K_2$ be **convex sets** in $X$ such that $K_1$ has *interior points* and $K_2$ contains *no interior point of $K_1$.*
>
>Then there is a **closed hyperplane** $H$ **separating** $K_1$ and $K_2$; i.e., there exists $f \in X^{*}$ such that 
>$$
> \begin{align*}
> \sup_{x \in K_1}f(x)  \leq \inf_{x \in K_2}f(x) 
> \end{align*}
>$$ 
>
>In other words, $K_1$ and $K_2$ lie in *opposite half-spaces* determined by $H$.

- This theorem is equivalent to [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]]
- [[Functional Analysis by Reed]]


## Explanation

>[!info]
>Note that *one point set* is *trivially convex*, so the above theorem will reduce to [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]]. 

## Theorems of Alternatives

- One of consequence of the separation theorem is **the existence** of *feasible solution* in **a system of inequalities** with **convex constraints**. Check [[Theorems of Alternatives]]



-----------
##  Recommended Notes and References

- [[Lower Bound and Infimum of Set]]
- [[Upper Bound and Supremum of Set]]
- [[Convex Set]]

- [[Dual Normed Space and Dual Banach Space]]
- [[Dual Representation of Convex Set]]
- [[Support functional of Convex Set]]


- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)

- [[Convex Optimization by Boyd]]
- [[Optimization by Vector Space Methods by Luenberger]]