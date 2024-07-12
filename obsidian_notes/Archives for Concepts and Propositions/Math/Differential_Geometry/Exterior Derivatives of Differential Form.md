---
tags:
  - concept
  - math/differential_geometry
keywords:
  - exterior_derivative
topics:
  - differential_geometry
name: Exterior Derivatives of Differential Form
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Exterior Derivatives of Differential Form

>[!important] Definition
>Let $\omega = \sum_{J}'\omega_J dx^J$ be a *smooth $k$-form* on an open subset $U\subseteq \mathbb{R}^n$ or $\mathbb{H}^n$.
>
>We define its **exterior derivative** $d\omega$ to be the following **$(k+1)$-form**:
>$$
> \begin{align}
> d\omega := d\left(\sum_{J}'\omega_J dx^J\right) =\sum_{J}' d\omega_J \wedge dx^{J},  
> \end{align}
>$$ 
> where $d\omega_J$ is the *differential* of the *function* $\omega_J$. 

- [[Coordinate Representation of k-Forms]]
- [[Differential k-Form on Manifold]]
- [[Differential as Covector Field]]
- [[Wedge Product]]

>[!info]
> In somewhat more detail, this is
> $$
> \begin{align}
> d\omega := d\left(\sum_{J}'\omega_J dx^J\right) = \sum_{J}'\sum_{i}\frac{\partial \omega_{J}}{ \partial x^i} dx^i \wedge dx^{j_1} \wedge \ldots \wedge dx^{j_k}. 
> \end{align}
>$$ 

### Existence and Uniqueness of Exterior Derivative

>[!important] Theorem (Alternative Definition)
>Suppose $M$ is a smooth manifold with or without boundary. 
>
>There are **unique operators** $d: \Omega^k(M) \rightarrow \Omega^{k+1}(M)$ for all $k$, called **exterior differentiation**, satisfying the following *four properties*:
> 
> - $d$ is **linear** over $\mathbb{R}$.
> - If $\omega \in \Omega^{k}(M)$ and $\eta \in \Omega^{l}(M)$, then
>$$ 
> \begin{align*}
> d(\omega \wedge \eta) &= d\omega \wedge \eta + (-1)^{k}\omega \wedge d \eta.
> \end{align*}
>$$ 
> - **$d \circ d  \equiv 0$.**
> - For $f \in \Omega^0(M) = \mathcal{C}^{\infty}(M)$, $df$ is the **differential** of $f$, given by $df(X) =Xf$.
> 
> In any smooth coordinate chart, $d$ is given by the *formula in definition above*.

^06d7a8

- [[Differential of a Smooth Map at Point]]
- [[Interior Multiplication]]

>[!info]
>The **exterior differentiation** defines the *differential* of $k$-form. 
>
>It is an **extension** of **differentiation** to **determinant function**.

- [[Antiderivation on Graded Algebra]]


## Explanation

>[!info]
>**Exterior derivative** generalize the concept of **curl operator** on vector fields in $\mathbb{R}^3$ to any *dimensions*.
>
>See **vector calculus**. 

>[!info]
>The **exterior derivatives** of a $k$-form is **a linear combination** of **$(k+1)$-forms**. 
>
>It component function is **the principal minior** of **Jacobian matrix** of component functions $$\left( \frac{ \partial \omega_{j} }{ \partial x^i }   \right).$$




## Property

>[!info]
>The exterior derivative **commutes with all pullbacks.**

>[!important] Proposition (Naturality of the Exterior Derivative)
>If $F: M \rightarrow N$ is a smooth map, then for each $k$ **the pullback map** $F^{*}: \Omega^k(N) \rightarrow \Omega^k(M)$ **commutes with** $d$: for all $\omega \in \Omega^{k}(N)$,
>$$
> \begin{align}
> F^{*}(d\omega) &= d\left(F^{*}\omega\right).  
> \end{align}
>$$ 

- [[Pullback of Covector Fields]]




## Invariant Formula for the Exterior Derivative

>[!info]
>We start with $1$-form.

>[!important] Proposition
>For any smooth $1$-form $\omega$ and smooth vector fields $X$ and $Y$,
>$$
> \begin{align}
> d\omega(X,Y) &= X(\omega(Y)) - Y(\omega(X)) - \omega([X, Y]).
> \end{align}
>$$ 
>where $[X, Y]$ is the **Lie bracket** of two vector fields. 


- [[Lie Bracket of Vector Fields]]

>[!info]
>Then extends to $k$-form.

>[!important] Proposition
>Let $M$ be a smooth manifold with or without boundary, and $\omega \in \Omega^k(M)$. 
>
>For any smooth vector fields $X_1,\ldots, X_{k+1}$ on $M$,
>$$
> \begin{align}
> d\omega \left(X_1,\ldots, X_{k+1}\right) &= \sum_{1\le i \le k+1}(-1)^{i}X_i\left(\omega \left(X_1,\ldots,  \widehat{X}_i  \ldots, X_{k+1}\right)\right)\nonumber\\
> &\, +   \sum_{1\le i < j \le k+1}(-1)^{i+j}\omega \left([X_i, X_j], X_1,\ldots,  \widehat{X}_i, \ldots,  \widehat{X}_j, \ldots, X_{k+1}\right),
> \end{align}
>$$ 
> where the hats indicate *omitted arguments.*

>[!info]
>This formula in similar to Laplace expansion for determinant of matrix.





-----------
##  Recommended Notes and References


- [[Coordinate Representation of k-Forms]]
- [[Differential k-Form on Manifold]]
- [[Differential as Covector Field]]
- [[Wedge Product]]

- [[Introduction to Smooth Manifolds by Lee]]