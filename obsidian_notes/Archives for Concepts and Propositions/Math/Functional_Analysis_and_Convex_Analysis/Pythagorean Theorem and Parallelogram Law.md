---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
keywords:
  - pythagorean_theorem
topics:
  - functional_analysis
  - linear_algebra
name: Pythagorean Theorem
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Pythagorean Theorem and *Parallelogram Law*


>[!important] Parallelogram Law
>For any $x, y \in (V,  \left\langle \cdot \,,\,  \cdot  \right\rangle )$, 
>$$
> \begin{align*}
> \lVert x + y \rVert^2  + \lVert x - y \rVert^2  &= 2 \lVert x \rVert^2  + 2\lVert y \rVert^2 
> \end{align*}
>$$ 

>[!info]
>With orthonormal basis, we can interpret it in coordinated form.

>[!important] Pythagorean Theorem
>Let $\{x_i\}_{i=1}^{n}$ be an **orthonormal set** in an *inner product space* $V$. Then for all $x \in V$,
>$$
> \begin{align*}
> \lVert x \rVert^2  &= \sum_{i=1}^{n}\lvert \left\langle x_{i}\,,\,x    \right\rangle \rvert^2 + \left\lVert x -  \sum_{i=1}^{n}\left\langle x_{i}\,,\,x    \right\rangle x_i \right\rVert^2 
> \end{align*}
>$$ 

- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Bessel inequality]]
- [[Cauchy-Schwartz Inequality]]

>[!info]
>The converse is true as well.

>[!important] Theorem
>In a *normed space* $(V, \|\cdot \|)$, if **the parallelogram law**
>$$
> \begin{align*}
>\lVert x + y \rVert^2  + \lVert x - y \rVert^2  &= 2 \lVert x \rVert^2  + 2\lVert y \rVert^2 
> \end{align*}
>$$  
>holds, then there *exist*s a **unique inner product** $\langle \cdot ,\ \cdot \rangle$ on $V$ such that 
>$$\lVert x \rVert  = \sqrt{\left\langle  x\,,\,x    \right\rangle}, \quad \forall x \in V.$$ 


## Explanation

>[!info]
>$\left\langle  x_{i}\,,\, x   \right\rangle$ is the **projection vector** of $x$ along the basis axis of $x_{i}$. We can define the **projection vector** of $x$ on the linear subspace spanned by $\{x_i\}_{i=1}^{n}$ as 
>$$
>x_{\parallel} = [\left\langle  x_{1}\,,\, x  \right\rangle \; \,{,}\ldots{,}\,\; \left\langle  x_{n}\,,\, x   \right\rangle]
>$$
>We can define the perpendicular part of the vector $x_{\perp}: = x - x_{\parallel}$
>
>Thus, the Pythagorean Theorem has a simple geometric interpretation: 
>$$ \lVert x \rVert^2  = \lVert x_{\parallel} \rVert^2 + \lVert x_{\perp} \rVert^2 $$ 
>This is also the result of original Pythagorean theorem in Euclidean space.






-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Inner Product Space]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)