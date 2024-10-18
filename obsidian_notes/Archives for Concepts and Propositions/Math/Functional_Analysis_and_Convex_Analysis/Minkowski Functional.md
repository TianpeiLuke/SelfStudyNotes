---
tags:
  - concept
  - math/functional_analysis
  - math/convex_analysis
  - optimization/theory
  - optimization/convex_optimization
keywords:
  - Minkowski_functional
  - gauge_function
topics:
  - functional_analysis
  - convex_analysis
name: Minkowski functional
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**:   Minkowski Functional or **Gauge function**

>[!important] Definition
>Let $K$ be a subset in a *real (or complex)  vector space* $X$. 
>
>Define the **gauge** *of* $K$ or the **Minkowski functional** associated with or *induced by* $K$ as a function $\rho_{K}: X \to [0, +\infty]$, valued in *extended* real numbers, defined by
>$$
> \begin{align*}
> \rho_{K}(x) &:= \inf\{ \lambda \ge 0 : x \in \lambda K  \}
> \end{align*}
>$$  
>defined on $X^{*}$ is called **the support functional** of $K$. 

^72ea74

>[!info]
>For any $x \in X$, $\rho_{K}(x) < + \infty$ if and only if 
>$$
>\{ \lambda: x\in \lambda K \; \} \neq \emptyset
>$$

## Explanation

>[!info]
>Minkowski functional is the function that recovers a *notion of distance* on a linear space.


## Example

>[!example]
>For normed vector space $X$,  let $K = \{x \in X: \lVert x \rVert \le 1  \}$ is *the unit ball*, then 
>$$
>\rho_{K}(x) := \lVert x \rVert 
>$$
>
>The *gauge function* of unit ball is just the *norm* itself.

- [[Norm and Normed Space]]

>[!example]
>Let $X$ be a vector space over field $F$. Let $f: X \to F$ be any *linear functional* (not necessarily bounded) on $X$.
>
>For fixed $t>0$, let $K$ be
>$$
>K := \{ x\in X: |f(x)| \le t \}.
>$$
>
>The *Minkowski functional* induced by $K$ is 
>$$
>\rho_{K}(x) = \frac{1}{t} |f(x)|, \quad x \in X.
>$$
>
>Note that this function fits the conditions 
>- **homogeneity**: $\rho_{K}(\gamma x) = |\gamma| \rho_{K}(x)$;
>- **the triangle inequality**: $\rho_K(x + y)\le \rho_{K}(x)+ \rho_{K}(y)$.
>- **non-negativity**: $\rho_{K}(x) \ge 0$.
>  
>Thus the *Minkowski functional* induced by $K$ is a **semi-norm**. So $(X, \rho_{K})$ is endowed with induced topology. 
>
>Note that $(X, \rho_{K})$  is not *necessarily Hausdorff* thus not necessarily a *locally convex space*.


- [[Locally Convex Space]]
- [[Vector Space over a Field]]

## Construct Semi-Norm from Minkowski Functional

>[!important] Theorem
>Let $X$ be a vector space.  If $K \subset X$ is a **balanced**, **convex** and **absorbing set** (i.e. an **absorbing disk**). 
>
>Then the **Minkowski functional** induced by $K$, which is a map $\rho_{K}: X \to [0, +\infty]$, defined by
>$$
>\rho_{K}(x) := \inf\{ \lambda \ge 0 : x \in \lambda K  \}
>$$
>is a **semi-norm** and is a **sub-linear functional**.
>
>Moreover, 
>$$
>\rho_{K}(x) = \frac{1}{\sup\{ \lambda \ge 0 : \lambda x \in K \}}.
>$$

- [[Disked Set]]
	- [[Convex Set]]
	- [[Balanced Set]]
- [[Absorbing Set]]

- [[Sublinear Functional]]

>[!info]
>We can show that 
>$$
>\{ x: \rho_{K}(x) < 1 \} \subset K \subset \{ x: \rho_{K}(x) \le 1 \}
>$$

>[!info]
>The Minkowski functional is used in combination with the Hahn-Banach Theorem to prove for extension of linear functional, since it provides a **sub-linear functional.**
>
>It is the key in proving the [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]]

- [[Hahn-Banach Theorem Extension Form]]
- [[Sublinear Functional]]

-----------
##  Recommended Notes and References

- [[Convex Set]]
- [[Support functional of Convex Set]]
- [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]]

- [[Convex Analysis by Rockafellar]]
- [[Convex Optimization by Boyd]]

- Wikipedia [Minkowski_functional](https://en.wikipedia.org/wiki/Minkowski_functional)

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)