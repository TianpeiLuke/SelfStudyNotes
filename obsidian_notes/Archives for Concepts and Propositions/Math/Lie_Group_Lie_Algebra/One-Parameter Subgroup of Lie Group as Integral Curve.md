---
tags:
  - concept
  - math/lie_group_algebra
  - math/differential_geometry
keywords:
  - one_parameter_group
topics:
  - differential_geometry
  - lie_group_lie_algebra
name: One-Parameter Subgroup of Lie Group and Flow
date of note: 2024-10-27
---

## Concept Definition

>[!important]
>**Name**: One-Parameter Subgroup of Lie Group and Flow

![[Global Flow on Smooth Manifold#^532ef7]]

>[!important] Definition
>Let $G$ be the *Lie group*.
>
>A **one-parameter subgroup** of $G$ is defined as a *Lie group homomorphism* $$\gamma: \mathbb{R} \to G,$$ with $\mathbb{R}$ considered as a *Lie group* under addition. 

- [[Lie Group]]
- [[Homomorphism between Groups]]

### Integral Curve

>[!important] Theorem (Characterization of One-parameter Subgoup)
>Let $G$ be a **Lie group**. 
>
>A map  $$\gamma: \mathbb{R} \to G$$  is an **one-parameter subgroups** $\gamma$ of $G$ *if and only if*  it is a **maximal integral curve** of **left-invariant** vector fields *starting at the identity*.

- [[Maximal Integral Curve of Vector Field]]
- [[Integral Curve of Vector Field]]


### One-parameter Subgroup Generated by Lie Algebra

![[Matrix Exponential as Global Flow in General Linear Group#^926b51]]

>[!important] Definition
>Let $G$ be the *Lie group* with *Lie algebra* $\mathfrak{g}$.
>
>For every $X\in \mathfrak{g}$,  a map $$\gamma: \mathbb{R} \to G$$ is called a **one-parameter subgroup** of $G$ **generated by** $X$ if
>- $\gamma$ is *smooth*; and $$\gamma(0) = I$$
>- the *velocity* of $\gamma$ at any point is given by $X$ at that point as $$\gamma'(t_{0}) := d\gamma(t)\left(\frac{d}{dt}\Big|_{t=t_{0}}\right) = X_{\gamma(t_{0})}, \quad \forall t_{0}\in \mathbb{R}$$
>	- Equivalently, $\gamma(t)$ is the *integral curve* of $X$.
>- for all $s,t \in \mathbb{R}$, $$\gamma(t+s) = \gamma(t)\,\gamma(s),$$ where the multiplication on right hand side is *the Lie group multiplication*.

^477259

- [[Continuous Function]]
- [[Lie Algebra as Vector Space with Lie Bracket]]
- [[Matrix Exponential as Global Flow in General Linear Group]]
- [[Derivation of Smooth Map at point and Tangent Vector]]
- [[Differential of a Smooth Map at Point]]



## Explanation

>[!important]
>We can define  a map $$\theta: \mathbb{R} \times  G \to G$$ from  **one-parameter subgroup** $\gamma$  by $$\theta(t, p)= \gamma(t)\,p$$
>
>We show that $\theta$ is a **global flow** in $G$ since the following conditions are satisfied:
>- $\theta$ is *smooth*
>- $$\theta(0, p) = \gamma(0)\,p = p$$
>- for any $p\in G$, any $s,t\in \mathbb{R}$ $$\begin{align*} \theta(t, \theta(s, p)) & = \gamma(t)\theta(s, p) \\[5pt] &= \gamma(t)\gamma(s)p \\[5pt] &= \gamma(t+s)p \\[5pt] &= \theta(t+s, p)\end{align*}$$

- [[Topological Group Action]]
- [[Global Flow on Smooth Manifold]]

## Exponential Map on Lie Group

![[Exponential Map of Lie Group and Matrix Lie Group#^c127f2]]

- [[Exponential Map of Lie Group and Matrix Lie Group]]
- [[Matrix Exponential]]


-----------
##  Recommended Notes and References









- [[Introduction to Smooth Manifolds by Lee]] pp 516 - 518
- [[Lie Groups Lie Algebra and Representations by Hall]] pp 41