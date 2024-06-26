---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
keywords:
  - dual_normed_space
  - duality
topics:
  - functional_analysis
  - linear_algebra
name: dual normed space
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Dual Normed Space


>[!important] Definition
>The space $\mathcal{L}(X, \mathbb{C})$ of all **bounded linear functionals** on *a normed linear space* $X$ is called the **dual space** of $X$. 
>
>This space $\mathcal{L}(X, \mathbb{C})$ is denoted as $X^{*}$.

## Explanation

>[!info]
>Dual space is the space of complex-valued linear operators on original space. 

>[!important] Proposition
>If $(X, \lVert \cdot \rVert)$ is a *Banach space*,  then the dual space $X^{*}$ is a Banach space.  The **norm** of *dual space* is 
>$$
> \begin{align*}
> \lVert f \rVert_{*}  &:= \sup_{x \neq 0, \, \lVert x \rVert  \le 1} \lvert f(x) \rvert  ,
> \end{align*} 
>$$ 
>for all $f \in X^{*}$.



-----------
##  Recommended Notes and References


- [[Space of Bounded Linear Operators]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Dual Space of Finite Dimensional Vector Space]]

- [[Bounded Linear Functional]]
- [[Norm and Normed Space]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)


- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Real Analysis by Royden]]