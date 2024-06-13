---
tags:
  - concept
  - math/functional_analysis
keywords:
  - inner_product_space
topics:
  - functional_analysis
name: inner product space
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Inner Product Space


>[!important] Definition
>A *complex vector space* $V$ is called an **inner product space** if there is a *complex-valued function* $\left< \cdot, \cdot \right>: V \times V \rightarrow \mathbb{C}$ that satisfies the following four conditions for an $x, y, z \in V$ and $a,b \in \mathbb{C}$:
> 1. **Positive Definiteness**: $\left< x, x\right> \ge 0$ and $\left< x, x \right> = 0$ if and only if $x = 0$
> 2. **Linearity**:  $\left< a\,x + b\,y, z\right> = a\left< x, z\right> + b\left< y, z\right>$ 
> 3. **Hermitian**:  $\left< x, y\right> = \overline{\left< y, x\right>}$
> 
> The function  $\left< \cdot, \cdot \right>$  is called an **inner product**.

>[!info]
>Some definitions place the linearity definition in the **second argument**, i.e.
>2. **Linearity**:  $\left< x,  a\,y + b\,z\right> = a\left< x, y\right> + b\left< x, z\right>$
>
>These two definitions are *equivalent* under a *Hermitian operation.*   



## Explanation

>[!info]
>For *real vector space*, an inner product is a **symmetric covariant $2$-tensor**, or a **symmetric bilinear form**.

- [[Symmetric Tensor]]
- [[Covariant Tensor on Vector Space]]



## Properties

>[!important]
>The geometric interpretation of inner product is **the angle** between two vectors. That is, 
>$$
>\cos(\theta) = \frac{\left\langle x\,,\, y \right\rangle}{\sqrt{\left\langle x \,,\,x \right\rangle }\; \sqrt{\left\langle y\,,\,y \right\rangle}}
>$$

- [[Cauchy-Schwartz Inequality]]

>[!info]
>Only when the angle is introduced, we can introduce an *Euclidean-like* geometry in the space. 



>[!important] Proposition
>Every **inner product space** $V$ is a **normed** *linear space* with the norm 
>$$
>\lVert x \rVert  = \sqrt{\left\langle  x\,,\,x    \right\rangle}
>$$

- [[Norm and Normed Space]]

>[!important]
>Note that normed vector space is also metric space. So inner product space is **metric space.**
>$$
>\begin{align*}
> d(x, y) &:= \lVert x - y \rVert = \sqrt{\left\langle x-y \,,\, x-y \right\rangle}.
> \end{align*}
>$$ 


>[!info]
>*Inner product space* is the only class of vector spaces with *Euclidean* **geometry** since it defines both **angle** and **distance.**




-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Metric Space]]
- [[Norm and Normed Space]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)