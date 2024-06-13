---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_immersion
topics:
  - differential_geometry
name: Smooth Immersion
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Smooth Immersion

>[!important] Definition
>A smooth map $F: M \rightarrow N$ is called a **smooth immersion** if its *differential* is *injective* *at each point*. 
>
>or *equivalently*, if $$\text{rank }F = \text{dim }M.$$


- [[Rank of Smooth Map]]
- [[Differential of a Smooth Map at Point]]
- [[Injective Function]]
- [[Canonical Inclusion]]

## Explanation

>[!info]
>A map $F: M \rightarrow N$ is 
>- **injective**: $a \neq b$ then $F(a) \neq F(b)$ 
>- **immersion**:  $v\neq w \in T_{p}M$, then $dF_{p}(v) \neq dF_{p}(w) \in T_{F(p)}N.$


>[!info]
>The following proposition states that smooth immersion is a local property.

>[!important] Proposition
>Suppose $F: M \rightarrow N$ is a smooth map and $p \in M$ . 
>
>If $dF_p$ is **injective**, then $p$ has a *neighborhood* $U$ such that $F|_{U}$ is an **immersion**.


>[!important] 
>The concept
>- **submersion/immersion**: about a **local property** of $F$ 
>- **surjective/injective**:  about a **global property** of $F$.  
>  
>Local property can *be determined by* the global property but not vice versa. 
>
>Thus a map 
>- can be **submersion** but *may not be surjective*.  
>- can be **immerison** but may *not be injective*. 

>[!info]
>By Global Rank Theorem [[Rank Theorem]], the converse is true for $F$ of **constant rank**.
>- $F$ surjective, then it is smooth submersion.
>- $F$ injective, then it is smooth immersion.


## Examples

>[!example]
>If $\gamma: J \rightarrow M$ is a **smooth curve** in a *smooth manifold* $M$ with or without boundary, then $\gamma$ is a **smooth immersion** *if and only if* $$\gamma'(t) \neq 0$$ for all $t \in J$.

>[!example]
> The smooth map $X: \mathbb{R}^2 \rightarrow \mathbb{R}^3$ given by
>$$ 
> \begin{align*}
> X(u,v) =  ((2+ \cos(2\pi u))\cos(2\pi v)\;,\; (2+\cos(2\pi u))\sin(2\pi v)\;,\;\sin(2\pi u))
> \end{align*}
>$$  
>is a **smooth immersion** of $\mathbb{R}^2$ into $\mathbb{R}^3$ whose *image* is the **doughnut-shaped surface** obtained by *revolving the circle* $$(y -2)^2 + z^2 = 1$$ in the $(y,z)$-plane about the $z$-axis .

## Canonical Representation of Immersion

 >[!important]
 >According to [[Rank Theorem]], the **canonical representation** for a **smooth immersion** in
 >$$
 >\widehat{F}(x^1,\ldots, x^m) =  (x^1,\ldots, x^m, 0,\ldots, 0).
 >$$
 >is called the **canonical injection** or **the inclusion map**, denoted as $\iota$.





-----------
##  Recommended Notes and References

- [[Rank of Smooth Map]]
- [[Differential of a Smooth Map at Point]]
- [[Injective Function]]


- [[Introduction to Smooth Manifolds by Lee]]