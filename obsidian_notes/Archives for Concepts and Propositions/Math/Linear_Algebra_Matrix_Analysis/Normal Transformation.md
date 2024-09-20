---
tags:
  - concept
  - math/linear_algebra
keywords:
  - normal_transform
topics:
  - linear_algebra
name: Normal Transformation
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Normal Transformation

>[!important] Definition
>A linear transformation $A$ on a finite dimensional inner product space $V$  is said to be **normal**  if it *commutes with its adjoint (conjugate transpose)*
>$$
> \begin{align*}
> A^{*}A = A A^{*} 
> \end{align*}
>$$ 

^8471b1

- [[Adjoint of Linear Map]]
- [[Inner Product Space]]


## Explanation

>[!example]
>Every **self-adjoint** linear transform is *normal*
>$$
>A^{*}A = A^2 = A A^{*}
>$$

 - [[Self-Adjoint Linear Map]]

>[!example]
>Every **unitary** or **orthogonal**  transform is *normal*
>$$
>U^{*}U = U U^{*} = I
>$$

- [[Unitary and Orthogonal Transformation]]



-----------
##  Recommended Notes and References



- [[Adjoint of Linear Map]]
- [[Inner Product Space]]



- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)

- [[Matrix Analysis by Horn]] pp 131
- [[Finite Dimensional Vector Spaces by Halmos]]