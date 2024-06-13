---
tags:
  - entry_point
  - concept
  - math/topology
  - math/functional_analysis
  - math/convex_analysis
  - optimization/theory
keywords: 
topics:
  - topology
  - functional_analysis
  - convex_analysis
name: convex geometry
date of note: 2024-05-08
---

##  List of Concepts

- Topology
	- [[Convex Set]]
	- [[Urysohn Lemma]]
	- [[Tietze Extension Theorem]]


- Functional Analysis
	- [[Dual Normed Space and Dual Banach Space]]
	- [[Sublinear Functional]]


- Convex Analysis
	- [[Legendre Transform]]
	- [[Convex Conjugate Function]]
	- [[Support functional of Convex Set]]


- The Hahn-Banach Theorem
	- [[Hahn-Banach Theorem Extension Form]]
	- [[Hahn-Banach Theorem Geometric Form]]
		- [[Separation Theorem]]
	- [[Supporting Hyperplane of Convex Set]]
	- [[Dual Representation of Convex Set]]

- Convex Subset in Finite Dimensional Space
	- [[Carathéodory Theorem for Convex Hull]] 


## Highlights

>[!important] Eidelheit's Separation Theorem
>Let $K_1$ and $K_2$ be **convex sets** in $X$ such that $K_1$ has *interior points* and $K_2$ contains *no interior point of $K_1$.*
>
>Then there is a **closed hyperplane** $H$ **separating** $K_1$ and $K_2$; i.e., there exists $f \in X^{*}$ such that 
>$$
> \begin{align}
> \sup_{x \in K_1}f(x) &\le \inf_{x \in K_2}f(x) 
> \end{align}
>$$ 
>
>In other words, $K_1$ and $K_2$ lie in *opposite half-spaces* determined by $H$.


>[!important]
>The **support functional** of a *convex set* $K$ **completely specifies the set** (to within *closure*}
>$$
> \begin{align*}
> \overline{K} &= \bigcap_{f \in X^{*}}\set{x: f(x) \le h(f)}.
> \end{align*}
>$$ 



-----------
##  Recommended Notes and References

- [[Convex Analysis by Rockafellar]]
- [[Topology Book by Munkres]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Functional Analysis by Reed]]