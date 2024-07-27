---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - schur_complement
  - inverse_block_matrix
topics:
  - matrix_analysis
  - linear_algebra
name: Schur Complement and Inversion of Block Matrix
date of note: 2024-07-23
---

## Concept Definition

>[!important]
>**Name**: Schur Complement and Inversion of Block Matrix

>[!important] Definition
>Suppose that $m, n \in \mathbb{N}$, and a matrix $M \in \mathbb{R}^{(m+n) \times (m+n)}$ can be partitioned into four *blocks* as
>$$
>\begin{align*}
> M &= \left[\begin{array}{cc}
> A & B\\
> C& D
>\end{array}\right] 
>\end{align*}
>$$
>where $A \in \mathbb{R}^{m\times m}$, $B\in \mathbb{R}^{m\times n}$, $C \in \mathbb{R}^{n\times m}$ and $D \in \mathbb{R}^{n\times n}.$
>
>If $D$ is *invertible*, then the **Schur complement** of block $D$ of *the matrix* $M$ is defined as 
>$$
> M / D := A - B\,D^{-1}\,C
>$$
>and $M / D \in \mathbb{R}^{n\times n.}$
>
>Similarly, if $A$ is *invertible*, then the **Schur complement** of block $A$ of *the matrix* $M$ is defined as 
>$$
> M / A := D - C\,A^{-1}\,B .
>$$
>and $M / A \in \mathbb{R}^{m \times m}.$

^eb8bd3


>[!important] Definition
>Suppose that $m, n \in \mathbb{N}$, and a matrix $M \in \mathbb{R}^{(m+n) \times (m+n)}$ can be partitioned into four *blocks* as
>$$
>\begin{align*}
> M &= \left[\begin{array}{cc}
> A & B\\
> C& D
>\end{array}\right] 
>\end{align*}
>$$
>where $A \in \mathbb{R}^{m\times m}$, $B\in \mathbb{R}^{m\times n}$, $C \in \mathbb{R}^{n\times m}$ and $D \in \mathbb{R}^{n\times n}.$
>
>If $D$ is *singular*, then the **generalized Schur complement** of block $D$ of *the matrix* $M$ is defined as 
>$$
> M / D := A - B\,D^{\dagger}\,C
>$$
>where  $D^{\dagger}$ is the **generalized inverse** $$D\,D^{\dagger}\,D = D$$

- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]

## Explanation


## Block Matrix Inversion

>[!important] Theorem (Inversion of Block Matrix)
>Suppose that $m, n \in \mathbb{N}$, and a matrix $M \in \mathbb{R}^{(m+n) \times (m+n)}$ can be partitioned into four *blocks* as
>$$
>\begin{align*}
> M &= \left[\begin{array}{cc}
> A & B\\
> C& D
>\end{array}\right] 
>\end{align*}
>$$
>where $A \in \mathbb{R}^{m\times m}$, $B\in \mathbb{R}^{m\times n}$, $C \in \mathbb{R}^{n\times m}$ and $D \in \mathbb{R}^{n\times n}.$
>
>- If $M$ is **invertible** and $D$ is **invertible**, then 
>$$
>\begin{align*}
> M^{-1} &= \left[\begin{array}{cc}
>A & B \\
>C & D
>\end{array}\right]^{-1} \\[5pt]
>&=\left[\begin{array}{cc}
> \left(M / D\right)^{-1} & -\left(M / D\right)^{-1} B\,D^{-1}\\
>-D^{-1}\,C\,\left(M / D\right)^{-1}  & D^{-1} + D^{-1}\,C\,\left(M / D\right)^{-1}\,B\,D^{-1}
>\end{array}\right]
>\end{align*}
>$$
>where $M / D$ is the **Schur complement** of $D$ of $M$.
>- If $M$ is **invertible** and $A$ is **invertible**, then 
>$$
>\begin{align*}
> M^{-1} &= \left[\begin{array}{cc}
>A & B \\
>C & D
>\end{array}\right]^{-1} \\[5pt]
>&=\left[\begin{array}{cc}
> A^{-1} + A^{-1}\,B\,\left(M / A\right)^{-1}\,C\,A^{-1}& -A^{-1}\,B\,\left(M / A\right)^{-1}\\
> -\left(M / A\right)^{-1}\,C\,A^{-1} & \left(M / A\right)^{-1}
>\end{array}\right]
>\end{align*}
>$$
>where $M / A$ is the **Schur complement** of $A$ of $M$.

^0d76ad

>[!example]
>For $m=n=1$, the inverse of $2\times 2$ matrix
>$$
>M^{-1} = \frac{1}{AD - BC}\left[\begin{array}{cc}
> D & -B\\
> -C & A
>\end{array}\right] 
>$$ 

>[!important]
>If $D$ is *invertible*,  we can compute the **Gauss-Jordan elimination** as
>$$
>\begin{align*}
>M &= \left[\begin{array}{cc}
> A & B\\
> C& D
>\end{array}\right] \\[5pt]
>&= \left[\begin{array}{cc}
>  I_{m}  & B\,D^{-1}\\
> 0& I_{n}
>\end{array}\right]\,\left[\begin{array}{cc}
> M / D & 0\\
> 0 & D
>\end{array}\right]\,\left[\begin{array}{cc}
> I_{m} & 0\\
>D^{-1}\,C & I_{n}
>\end{array}\right]
>\end{align*}
>$$
>
>If  $A$ is *invertible*,  
>$$
>\begin{align*}
>M&= \left[\begin{array}{cc}
>  I_{m}  & 0\\
> C\,A^{-1}& I_{n}
>\end{array}\right]\,\left[\begin{array}{cc}
> A & 0\\
> 0 & M / A
>\end{array}\right]\,\left[\begin{array}{cc}
> I_{m} & A^{-1}\, B\\
> 0& I_{n}
>\end{array}\right]
>\end{align*}
>$$

>[!important]
>If $M$ and $D$ is *invertible*,  we can decompose the inverse of 
>$$
>\begin{align*}
>M &= \left[\begin{array}{cc}
> A & B\\
> C& D
>\end{array}\right] 
>\end{align*}
>$$
>as
>$$
>\begin{align*}
>M^{-1}&= \left[\begin{array}{cc}
>  I_{m}  & 0\\
> - D^{-1}\,C  & I_{n}
>\end{array}\right]\,\left[\begin{array}{cc}
> (M / D)^{-1} & 0\\
> 0 & D^{-1}
>\end{array}\right]\,\left[\begin{array}{cc}
> I_{m} & - B\,D^{-1}\\
>0 & I_{n}
>\end{array}\right]
>\end{align*}
>$$
>
>If $A$ is *invertible*, 
>$$
>\begin{align*}
>M^{-1}&= \left[\begin{array}{cc}
>   I_{m}  & -A^{-1}\,B\\
>0& I_{n}
>\end{array}\right]\,\left[\begin{array}{cc}
> A^{-1} & 0\\
> 0 & (M / A)^{-1}
>\end{array}\right]\,\left[\begin{array}{cc}
> I_{m} & 0\\
> -C\, A^{-1}& I_{n}
>\end{array}\right]
>\end{align*}
>$$

## Determinant of Block Matrix

>[!important] Schur Formula
>Suppose that $m, n \in \mathbb{N}$, and a matrix $M \in \mathbb{R}^{(m+n) \times (m+n)}$ can be partitioned into four *blocks* as
>$$
>\begin{align*}
> M &= \left[\begin{array}{cc}
> A & B\\
> C& D
>\end{array}\right] 
>\end{align*}
>$$
>where $A \in \mathbb{R}^{m\times m}$, $B\in \mathbb{R}^{m\times n}$, $C \in \mathbb{R}^{n\times m}$ and $D \in \mathbb{R}^{n\times n}.$
>
>- If $D$ is **invertible**, then the **determinant** of $M$ can be decomposed into the product of *determinant* of $D$ and *determinant* of **Schur complement** of $D$ $$\det(M) = \det(D) \;\det\left(M / D\right)$$
>- Similarly, if $A$ is **invertible**, then the **determinant** of $M$ can be decomposed into the product of *determinant* of $A$ and *determinant* of **Schur complement** of $A$ $$\det(M) = \det(A) \;\det\left(M / A\right)$$
>  
>This formula is called the **Schur formula**.  



## Positive Definiteness

>[!important] Theorem
>Suppose that $m, n \in \mathbb{N}$, and a **symmetric matrix** $M \in \mathbb{R}^{(m+n) \times (m+n)}$ can be partitioned into four *blocks* as
>$$
>\begin{align*}
> M &= \left[\begin{array}{cc}
> A & B\\
> B^{T} & C
>\end{array}\right] 
>\end{align*}
>$$
>where $A \in \mathbb{R}^{m\times m}$, $B\in \mathbb{R}^{m\times n}$, and $C \in \mathbb{R}^{n\times n}.$
>
>Then: 
>- If $A$ is **invertible**,  then $M$ is **positive definite** *if and only if* **both** $A$ and the *Schur complement* $M / A$ are **positive definite** $$M \succ 0 \;\iff \; A \succ 0, \;\; M / A \succ 0.$$ 
>- If $C$ is **invertible**, then $M$ is **positive definite** *if and only if* **both** $C$ and the *Schur complement* $M / C$ are **positive definite** $$M \succ 0 \;\iff \; C \succ 0, \;\; M / C \succ 0.$$ 
>- If $A$ is **positive definite**, then $M$ is **positive semi-definite** *if and only if*  the *Schur complement* $M / A$ is **positive semi-definite** $$(A \succ 0) \quad   M \succeq 0 \;\iff \;  M / A \succeq 0.$$ 
>- If $C$ is **positive definite**, then $M$ is **positive semi-definite** *if and only if*  the *Schur complement* $M / C$ is **positive semi-definite** $$(C \succ 0) \quad   M \succeq 0 \;\iff \;  M / C \succeq 0.$$ 


- [[Positive Semidefinite Transformation]]

## Conditional Distribution of Gaussian

![[Marginal and Conditional Distribution of Gaussian#^70f047]]

- [[Marginal and Conditional Distribution of Gaussian]]




-----------
##  Recommended Notes and References


- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]
- [[Matrix]]
- [[General Linear Group]]

- [[Linear Regression]]
- [[Least Square Estimation]]


- Wikipedia [Schur_complement](https://en.wikipedia.org/wiki/Schur_complement)