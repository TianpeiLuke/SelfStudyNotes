---
tags:
  - concept
  - math/differential_geometry
keywords:
  - lie_bracket
topics:
  - differential_geometry
name: Lie Bracket of Vector Fields
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Lie Bracket of Vector Fields


>[!important] Definition
>Let $X$ and $Y$ be smooth vector fields on a smooth manifold $M$ and $f \in \mathcal{C}^{\infty}(M)$ is *smooth function*  on $M$. 
>
>Define an **operator** $[X,Y] : \mathcal{C}^{\infty}(M) \rightarrow \mathcal{C}^{\infty}(M)$, called **the Lie bracket** of $X$ *and* $Y$, defined by
>$$
> \begin{align}
> [X,Y]\,f &= XYf - YXf. 
> \end{align}
>$$ 

- [[Vector Fields as Total Derivation of Smooth Maps]]
- [[Smooth Maps on Space of Vector Fields]]
- [[Smooth Vector Field on Manifold]]


## Explanation

>[!important]
>A vector field maps a *smooth function* on $M$ to *another smooth function* on $M$. Thus it is valid to define $XYf = Xg$ where $g= Yf$ is the **derivation of $f$ under $Y$.** 
>
>$[X, Y]_{p}f$ is a **second-order (mixed directional) derivatives** of $f$ at $p$ **along two directions** $Y_p$ and $X_p$.


>[!important]
>Note that $XY$ itself is **not a vector field** since it does *not necessarily satisfy the Leibnitz rule.* 
>
>For example, $X = \frac{\partial }{ \partial x}$ and $Y = x \frac{\partial }{ \partial y}$. Let $f(x, y) = x$ and $g(x, y) = y$. Then direct computation shows that $$XY(fg) = 2x,$$ while $$f XYg + g XYf  = x,$$ so $XY$ is not a derivation of $\mathcal{C}^{\infty}(\mathbb{R}^2)$.


## Coordinate Representation

- [[Coordinate Formula for Lie Bracket of Vector Fields]]


## Geometric Intepretation

>[!important] Theorem
>If $M$ is a **smooth manifold** and $V, W \in \mathfrak{X}(M)$, then $$\mathscr{L}_{V}\,W = [V, W].$$

- [[Lie Derivative of Vector Field]]

>[!important]
>This thoerem also gives us a **geometric interpretation** of the **Lie bracket** of *two vector fields*: 
>- it is the **directional derivative** of **the second vector field** along *the __flow__ of the __first__*. 

>[!info]
>Compare to the covariant derivative defined by connections. 

- [[Connection in Vector Bundle]]



-----------
##  Recommended Notes and References


- [[Differential of a Smooth Map at Point]]
- [[Smooth Map]]
  
  
- [[Space of all Smooth Vector Fields on a Manifold]]
- [[Smooth Vector Field on Manifold]]
- [[Vector Field on Manifold]]


- [[Vector Space over a Field]]


- [[Introduction to Smooth Manifolds by Lee]]