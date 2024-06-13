---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
  - math/topology
keywords:
  - schauder_basis
topics:
  - functional_analysis
  - linear_algebra
name: Schauder basis of normed space
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  *Schauder Basis* of Normed Space and the *Expansion* of element


>[!important] Definition
>**If** a normed space $X$ contains a sequence $(e_i)$ with **the property** that for *every* $x \in X$ there is a **unique** *sequence of scalars* $(u^i)$ such that
>$$
> \begin{align}
> \lim\limits_{n\rightarrow \infty}\left\lVert x - \sum_{i=1}^{n}u^i\,e_i \right\rVert  = 0,
> \end{align}
>$$ 
>then $(e_i)$ is called a **Schauder basis** (or **basis**} for $X$. 

>[!important] Definition
> The series $$\sum_{i=1}^{\infty}u^i\,e_i$$ which has the sum $x$ is then called **the expansion** of $x$ *with respect to* $(e_i)$, and we write
> $$
> \begin{align*}
> x = \sum_{i=1}^{\infty}u^i\,e_i
> \end{align*}
>$$ 


## Explanation





-----------
##  Recommended Notes and References

- [[Norm and Normed Space]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)