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
>**Name**: Coordinate Formula for Lie Bracket of Vector Fields


>[!info] Definition
>Let $X$ and $Y$ be smooth vector fields on a smooth manifold $M$ and $f \in \mathcal{C}^{\infty}(M)$ is *smooth function*  on $M$. 
>
>Define an **operator** $[X,Y] : \mathcal{C}^{\infty}(M) \rightarrow \mathcal{C}^{\infty}(M)$, called **the Lie bracket** of $X$ *and* $Y$, defined by
>$$
> \begin{align}
> [X,Y]\,f &= XYf - YXf. 
> \end{align}
>$$ 

- [[Lie Bracket of Vector Fields]]

>[!important] Proposition
>Let $X, Y$ be smooth vector fields on a smooth manifold $M$ with or without boundary, and let $X = X^i\, \frac{\partial}{\partial x^{i}}$ and $Y = Y^j\frac{\partial}{\partial x^{j}}$ be the **coordinate expressions** for $X$ and $Y$ in terms of some *smooth local coordinates* $(x^i)$ for $M$. 
>
>Then $[X, Y]$ has the following **coordinate expression**:
>$$
> \begin{align}
> [X, Y]&= \left(X^{i} \frac{\partial Y^{j}}{\partial x^{i}} - Y^{i}\frac{\partial X^{j}}{\partial x^{i}}  \right) \frac{\partial}{ \partial x^{j}},  
> \end{align} 
>$$ 
> or more concisely,
>$$ 
> \begin{align}
> [X, Y]&= \left(XY^{j}  - YX^{j}\right) \frac{\partial}{\partial x^{j}}.  
> \end{align}
>$$ 

- [[Coordinate Representation of Vector Field on Manifold]]
- [[Einstein Summation Convention]]


## Explanation

>[!example]
>One trivial application of above formula is to compute **the Lie brackets of the coordinate
vector fields** $\frac{\partial}{\partial x^{i}}$  in *any smooth chart*: 
> 
>because *the component functions* of the coordinate vector fields are all *constants*, it follows that
>$$ 
> \begin{align}
>  \left[\frac{\partial}{\partial x^{i}},  \frac{\partial}{\partial x^{j}}\right] &\equiv 0, \quad \forall\, i,j.  
> \end{align} 
>$$ 















-----------
##  Recommended Notes and References


- [[Differential of a Smooth Map at Point]]
- [[Smooth Map between Euclidean Spaces]]
  
  
- [[Space of all Smooth Vector Fields on a Manifold]]
- [[Smooth Vector Field on Manifold]]
- [[Vector Field on Manifold]]


- [[Vector Space over a Field]]


- [[Introduction to Smooth Manifolds by Lee]]