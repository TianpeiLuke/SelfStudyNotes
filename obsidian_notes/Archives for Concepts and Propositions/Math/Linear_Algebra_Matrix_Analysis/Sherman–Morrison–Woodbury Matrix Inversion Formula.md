---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - sherman-morrison_matrix_inversion
  - woodbury_formula
topics:
  - matrix_analysis
  - linear_algebra
name: Sherman-Morrison-Woodbury Matrix Inversion Formula
date of note: 2024-07-23
---

## Concept Definition

>[!important]
>**Name**: *Sherman-Morrison-Woodbury* Matrix Inversion Formula

![[Schur Complement and Inversion of Block Matrix#^eb8bd3]]

![[Schur Complement and Inversion of Block Matrix#^0d76ad]]


### Sherman-Morrison Formula

>[!important] Theorem (Sherman-Morrison Formula)
>Let $A\in \mathbb{R}^{n\times n}$ be **invertible matrix** and $u, v\in \mathbb{R}^{n}$ be vectors. 
>
>Then $A + u\,v^{T}$ is **invertible** and 
>$$
>\left(A + u\,v^{T}\right)^{-1} = A^{-1} - \frac{A^{-1} u v^{T} A^{-1} }{1 + v^{T}A^{-1}u}
>$$

### Woodbury Identity

>[!important] Woodbury Identity
>The **Woodbury identity** is 
>$$
>\left(A + U\,D\,V\right)^{-1} = A^{-1} - A^{-1}\,U\left(D^{-1} + V\,A^{-1}\,U\right)^{-1}\,V\,A^{-1}
>$$


>[!info]
>Let $U=u$, $V=v^{T}$, and $D= I$, we have the **Sherman-Morrison Formula**


>[!important]
>Some useful **extensions**
>$$
>\begin{align*}
>\left(A + U\,D\,U^{T}\right)^{-1} &= A^{-1} - A^{-1}\,U\left(D^{-1} + U^{T}\,A^{-1}\,U\right)^{-1}\,U^{T}\,A^{-1} \\[5pt]
>(\text{Kailath Variant})\;\; (A + B\,C)^{-1} &= A^{-1} - A^{-1}\,B\,\left(I + C\,A^{-1}\,B\right)^{-1}\,C\,A^{-1} \\[5pt]
>(\text{Push-through Identity})\;\; (I + UV)^{-1}\,U &= U\left(I + VU\right)^{-1} \\[5pt]
> (I + A\,B)^{-1} &= I - A\,\left(I + BA\right)^{-1}\,B\\[5pt]
> (I + U\,\Lambda\, U^{T})^{-1} &= I - U\,\left(\Lambda^{-1} + I\right)^{-1}\,U\\[5pt]
> \left(I + A^{-1}\right)^{-1} &= A\,\left(I + A\right)^{-1} \\[5pt]
> \left(A^{-1} + B^{-1}\right)^{-1} &= A\,\left(A + B\right)^{-1}\,B = B\,\left(A + B\right)^{-1}\,A \\[5pt]
> \left(A^{-1} + B^{-1}\right) &= A^{-1}\,\left(A + B\right)\,B^{-1}  \\[5pt]
>\end{align*}
>$$


## Explanation

>[!info]
>Consider the partitioned matrix
>$$
>\begin{align*}
> M &= \left[\begin{array}{cc}
> A & B\\
> C& -D^{-1}
>\end{array}\right] 
>\end{align*}
>$$
>then 
>$$
>M / (-D^{-1}) := A - B\,\left(-D^{-1}\right)^{-1}\,C = A + B\,D\,C
>$$
>and
>$$
>M / A := -D^{-1} - C\,A^{-1}\,B.
>$$
>The **Woodbury identity** can be seen as the matching on the upper-left block of two **block matrix inversion formula**
>$$
>\left(M / (-D^{-1})\right)^{-1} = A^{-1} + A^{-1}\,B\,\left(M / A\right)^{-1}\,C\,A^{-1}
>$$
>which is equal to
>$$
>\left(A + B\,D\,C\right)^{-1} = A^{-1} - A^{-1}\,B\,\left(D^{-1} + C\,A^{-1}\,B\right)^{-1}\,C\,A^{-1}
>$$

- [[Schur Complement and Inversion of Block Matrix]]

## Applications


>[!info]
>**Sherman-Morrison Formula** can be used as **rank-1 update** formula for *online matrix computation*. 

![[BFGS Algorithm#^09e0ca]]

- [[BFGS Algorithm]]
- [[Limited Memory BFGS]]



>[!info]
>**Woodbury Identity** is used in **Kalman filter** update.

- [[Kalman Filter Discrete-Time]]


-----------
##  Recommended Notes and References

- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Schur Complement and Inversion of Block Matrix]]
- [[Matrix]]
- [[General Linear Group]]

- [[Matrix Analysis by Horn]] pp 19
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 48
- Wikipedia [Woodbury_matrix_identity](https://en.wikipedia.org/wiki/Woodbury_matrix_identity)
- Wikipedia [Sherman-Morrison_formula](https://en.wikipedia.org/wiki/Sherman%E2%80%93Morrison_formula)