---
tags:
  - concept
  - math/functional_analysis
  - math/convex_analysis
  - optimization/theory
keywords:
  - support_functional
topics:
  - functional_analysis
  - convex_analysis
name: support functional of convex set
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:   Support Functional

>[!important] Definition
>Let $K$ be a *convex set* in a *real normed vector space* $X$. The functional
>$$
> \begin{align*}
> h(f) &:= \sup_{x \in K}f(x)
> \end{align*}
>$$  
>defined on $X^{*}$ is called **the support functional** of $K$. 

>[!info]
>The support functional  lies in the **dual of dual space** $h \in X^{**}$.

- [[Convex Set]]
- [[Dual Normed Space and Dual Banach Space]]

## Explanation

>[!important]
>The **support functional** of a *convex set* $K$ **completely specifies the set** (to within *closure*}
>$$
> \begin{align*}
> \overline{K} &= \bigcap_{f \in X^{*}}\set{x: f(x) \leq h(f)}.
> \end{align*}
>$$ 

^ab1379

- [[Dual Representation of Convex Set]]
- [[Separation Theorem]]



-----------
##  Recommended Notes and References

- [[Convex Set]]
- [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]]


- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)