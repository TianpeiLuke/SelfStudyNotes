---
tags:
  - concept
  - math/differential_geometry
keywords:
  - differential_coordinate
  - jacobian_matrix
topics:
  - differential_geometry
name: Coordinates Representation of Differential
date of note: 2024-05-17
---

## Concept Definition

>[!important]
>**Name**: Coordinates Representation of Differential at Point


### Coordinate Representation of Differential on Manifold

>[!important] Definition
>For a smooth map $F: M \rightarrow N$ between *smooth manifolds* with or without boundary, the *action* of **differential** $dF_{p}$ on a typical basis vector can be represented as
>$$
> \begin{align}
> dF_p\left(\frac{\partial}{\partial x^i}\Bigr|_{p}\right) &= \frac{\partial \widehat{F}^{i}}{\partial x^j}(\widehat{p})\;\frac{\partial}{\partial y^{i}}\Bigr|_{F(p)},
> \end{align}
>$$  
>where  
>- $$\widehat{F} = \psi \circ F \circ \varphi^{-1}: \;\; \varphi(U \cap F^{-1}(V)) \rightarrow \psi(V)$$ is the **coordinate representation** of $F$ under *smooth charts* $(U,\varphi)$ for $M$ and $(V, \psi)$ for $N$. 
>- Also $\widehat{p} = \varphi(p)$  is the **coordinate representation** of $p$. 
>- $(x^1,\ldots, x^n)$ is the *coordinates* of $U$ and $(y^1,\ldots, y^m)$ is the *coordinate* of $V$.  
>- The *matrix* for 
>$$
>\begin{align}
>  \left[\begin{array}{ccc}
> \dfrac{\partial\,\widehat{F}^{1}}{\partial\,x^{1}}(\widehat{p})& \ldots& \dfrac{\partial\,\widehat{F}^{1}}{\partial\,x^{n}}(\widehat{p})\\
> \vdots & \ddots & \vdots\\
> \dfrac{\partial\,\widehat{F}^{m}}{\partial\,x^{1}}(\widehat{p})& \ldots& \dfrac{\partial\,\widehat{F}^{m}}{\partial\,x^{n}}(\widehat{p})
> \end{array}\right]_{m \times n}
> \end{align}
>$$ 
>is the **Jacobian matrix**.
>
>That is $dF_{p}$ is represented in *coordinate bases* by the **Jacobian matrix** of (*the coordinate representative* of) $F$.

>[!info]
>Note that [[Einstein Summation Convention]]

- [[Coordinate Representation of Smooth Map]]
- [[Smooth Chart and Smooth Coordinate Map]]

>[!info]
>In fact, the *definition* of the **differential** was cooked up precisely to *give a* **coordinate-independent meaning** to the **Jacobian matrix**.

>[!info] Other Names
>In the differential geometry literature, the **differential** is sometimes called 
>- the **tangent map**, 
>- the **total derivative**, or 
>- simply **the derivative of $F$.** 
>-  **the (pointwise) pushforward**. 
>	- Because it "**pushes**" *tangent vectors* **forward** *from the domain manifold* to the *codomain*

>[!info]
>Different authors denote it by symbols such as
>$$
> \begin{align*}
> F'(p), \quad D\,F(p), \quad D\,F, \quad F^{*},\quad T\,F, \quad T_{p}F.
> \end{align*}
>$$ 



## Development of the Coordinate Representation of Differentials

![[differential_coordinate.png]]

### Coordinate Representation of Differential on Euclidean Space

>[!info]
>Next we explore how differentials look in coordinates. 
>
>- We begin by considering the special case of a smooth map $F: U \rightarrow V$, where $U \subseteq \mathbb{R}^n$ and $V \subseteq \mathbb{R}^m$ are *open subsets* of **Euclidean spaces.**  
>
>For any $p \in U$ , we will determine the **matrix** of $dF_p: T_{p}\mathbb{R}^n \rightarrow T_{F(p)}\mathbb{R}^m$ in terms of the *standard coordinate bases.*

- [[Differential of a Smooth Map at Point]]
- [[Linear Map]]
- [[Matrix]]
- [[Diffeomorphism]]

>[!info]
>
> Using $(x^1,\ldots, x^n)$ to denote the *coordinates in the domain* and $(y^1,\ldots, y^m)$ to denote those in the *codomain*, we use the **chain rule** to compute **the action of $dF_p$ on a typical basis vector** as follows:
>$$ 
> \begin{align*}
> dF_p\left(\frac{\partial}{\partial x^i}\Bigr|_{p}\right)(f) &= \frac{\partial}{\partial x^i}\Bigr|_{p} (f \circ F) \\
> &= \frac{\partial f}{\partial y^{j}}(F(p)) \frac{\partial F^{j}}{\partial x^i}(p) \\
> &= \left(\frac{\partial F^{j}}{\partial x^i}(p)\,\frac{\partial}{\partial y^{j}}(F(p))\right)(f) 
> \end{align*}
>$$ 

- [[Coordinate Representation of Tangent Vector]]

>[!important] Definition
>The *action* of **differential** of $F: U \rightarrow V$ , where $U \subseteq \mathbb{R}^n$ and $V \subseteq \mathbb{R}^m$ **on a typical basis vector** can be represented as
>$$
> \begin{align}
> dF_p\left(\frac{\partial}{\partial x^i}\Bigr|_{p}\right) &= \frac{\partial F^{j}}{\partial x^i}(p)\; \frac{\partial}{\partial y^{j}}\Bigr|_{F(p)},
> \end{align} 
>$$ 
>where $(x^1,\ldots, x^n)$ is the *coordinates* of $U$ and $(y^1,\ldots, y^m)$ is the *coordinate* of $V$.

>[!important]
>In other words, the **matrix** of $dF_p$ in terms of the *coordinate bases* is 
>$$
> \begin{align}
>  \left[\begin{array}{ccc}
> \dfrac{\partial\,F^{1}}{\partial\,x^{1}}(p)& \ldots& \dfrac{\partial\,F^{1}}{\partial\,x^{n}}(p)\\
> \vdots & \ddots & \vdots\\
> \dfrac{\partial\,F^{m}}{\partial\,x^{1}}(p)& \ldots& \dfrac{\partial\,F^{m}}{\partial\,x^{n}}(p)
> \end{array}\right]_{m \times n}
> \end{align}
>$$  
>This matrix is none other than **the Jacobian matrix** of $F$ at $p$, which is the **matrix representation** of the **total derivative** $DF_{p}: \mathbb{R}^n \rightarrow \mathbb{R}^m$. 

>[!info]
> Therefore, in this case, $dF_p: T_{p}\mathbb{R}^n \rightarrow T_{F(p)}\mathbb{R}^m$ corresponds to **the total derivative** $DF_{p}: \mathbb{R}^n \rightarrow \mathbb{R}^m$, under our *usual identification of Euclidean spaces* with *their tangent spaces.* 
> 
> The same calculation applies if $U$ is an open subset of half-spaces $\mathbb{H}^n$ and $V$ is an open subset of $\mathbb{H}^m$.


### Coordinate Representation of Differential on Manifold

>[!info]
>- Now consider the more general case of a smooth map $F: M \rightarrow N$ between smooth manifolds with or without boundary.   
> 
> Choosing *smooth coordinate charts* $(U,\varphi)$ for $M$ containing $p$ and $(V, \psi)$  for $N$ containing $F(p)$, we obtain the **coordinate representation** $$\widehat{F} = \psi \circ F \circ \varphi^{-1}: \varphi(U \cap F^{-1}(V)) \rightarrow \psi(V).$$ 
> 
> Let $\widehat{p} = \varphi(p)$ be **coordinate representation** of $p$.

- [[Smooth Chart and Smooth Coordinate Map]]
- [[Coordinate Representation of Smooth Map]]

>[!info]
> By the computation above, $d\widehat{F}_{\widehat{p}}$ is represented with respect to the standard coordinate bases by *the Jacobian matrix* of $\widehat{F}$ at $\widehat{p}$. 
> 
> Using the fact that $\psi^{-1} \circ \widehat{F} =  F \circ \varphi^{-1}$, we compute
>$$
> \begin{align*}
> dF_p\left(\frac{\partial}{\partial x^i}\Bigr|_{p}\right) &= dF_{p}\left(d (\varphi^{-1})_{\widehat{p}}\left(\frac{\partial}{\partial x^i}\Bigr|_{\widehat{p}}\right)\right) \\
> &= d(\psi^{-1})_{\widehat{F}(\widehat{p})}\left(d\widehat{F}_{\widehat{p}}\left(\frac{\partial}{\partial x^i}\Bigr|_{\widehat{p}}\right)\right)\\
> &= d(\psi^{-1})_{\widehat{F}(\widehat{p})}\left( \frac{\partial \widehat{F}^{j}}{\partial x^{i}}(\widehat{p})\, \frac{\partial}{\partial y^{j}}\Bigr|_{\widehat{F}(\widehat{p})}\right)\\
> &= \frac{\partial \widehat{F}^{j}}{\partial x^{i}}(\widehat{p})\,\left(d(\psi^{-1})_{\widehat{F}(\widehat{p})}\frac{\partial}{\partial y^{j}} \Bigr|_{\widehat{F}(\widehat{p})}\right)\\
> &= \frac{\partial \widehat{F}^{j}}{\partial x^{i}}(\widehat{p})\,\frac{\partial}{\partial y^{j}}\Bigr|_{p}
> \end{align*}
>$$ 


























-----------
##  Recommended Notes and References

- [[Differential of a Smooth Map at Point]]
- [[Coordinate Representation of Tangent Vector]]

- [[Smooth Manifold]]
- [[Basis of Vector Space]]


