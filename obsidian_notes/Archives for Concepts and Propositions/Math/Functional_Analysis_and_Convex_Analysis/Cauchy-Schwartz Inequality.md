---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
keywords:
  - cauchy_schwartz_inquality
topics:
  - functional_analysis
  - linear_algebra
name: Cauchy-Schwartz's inequality
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Cauchy-Schwartz's Inequality


>[!important] Cauchy-Schwartz's Inequality
>Let $V$ be an *inner product space.* For $x,y \in V$,
>$$
> \begin{align*}
> \lvert  \left\langle x\,,\,y \right\rangle \rvert &\le \sqrt{\left\langle x\,,\,x \right\rangle } \sqrt{ \left\langle y\,,\,y \right\rangle  } := \lVert x\rVert \, \lVert y\rVert .
> \end{align*}
>$$ 
>where the **equality** holds if and only if $x$ and $y$ are linearly dependent.

^11b65d

>[!info]
>This inequality is fundamental to inner product space since its proof only uses the definition of inner product. 

- [[Pythagorean Theorem and Parallelogram Law]]
## Explanation

>[!important]
>The consequence of Cauchy-Schwartz inequality is that the following definition of **the angle** between two vectors make sense
>$$
>\cos(\theta) = \frac{\left\langle x\,,\, y \right\rangle}{\sqrt{\left\langle x \,,\,x \right\rangle }\; \sqrt{\left\langle y\,,\,y \right\rangle}} \in [-1, 1]
>$$



## Generalization

>[!important]
>The Cauchy-Schwartz's Inequality is the special case of Hölder Inequality when $$p=q=\frac{1}{2}. $$

- [[Hölder Inequality]]


-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Inner Product Space]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)