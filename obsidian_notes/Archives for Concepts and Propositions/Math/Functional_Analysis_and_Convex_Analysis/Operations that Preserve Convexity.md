---
tags:
  - concept
  - math/convex_analysis
keywords:
  - convex_operation
topics:
  - convex_analysis
name: Operations that Preserve Convexity
date of note: 2024-05-16
---

## Concept Definition

>[!important]
>**Name**: Operations that Preserve Convexity

### Non-negative Sum

>[!important] Proposition
>Let $\left\{ f_{k}: \mathcal{X} \to \mathbb{R}, k=1,2,\,{}\ldots{}\,n \right\}$ be a set of **convex functions**. And suppose that $\left\{ w_{k}, k=1,2,\,{}\ldots{}\,n \right\}$ is a set of **non-negative scalars**.
>
>Then $$\sum_{k=1}^{n}w_{k}\,f_{k}(\cdot)$$ is a **convex function**.
>
>In general, if $f: \mathcal{X} \times \mathcal{Y} \to \mathbb{R}$ is **convex** in its *first argument*, and $w: \mathcal{Y} \to [0, \infty)$ is a *non-negative function*, such that
>$$
> \int_{\mathcal{X}}\int_{\mathcal{Y}}|w(y)\,f(x, y)|\,dy\,dx < \infty,
>$$
>then 
>$$
>g(x) :=  \int_{\mathcal{Y}}w(y)\,f(x, y)\,dy
>$$
>is **convex** in $x\in \mathcal{X}$

^96448c

### Composition with Affine Mapping

>[!important] Proposition
>Suppose $f: \mathbb{R}^n \to \mathbb{R}$, and $A \in \mathbb{R}^{n \times m}$, $b\in \mathbb{R}^{n}$.
>
>Define $g: \mathbb{R}^{m} \to \mathbb{R}$ by $$g(x) = f\left(Ax + b\right),$$ with domain $$\text{dom}(g) = \left\{ x: \; Ax + b \in \text{dom}(f) \right\}.$$
>
>If $f$ is **convex**, then $g$ is **convex**; if $f$ is **concave**, then $g$ is **concave**.

^273433

### Pointwise Maximum or Supremum

>[!important] Proposition
>If $f, g$ are **convex functions**, then the **pointwise maximum** defined by
>$$
>h(x) = \max\{ f(x), g(x) \},
>$$
>with $\text{dom}(h) = \text{dom}(f) \,\cap\,\text{dom}(g),$ is also **convex**.
>
>Similarly for any **finite number** of **convex functions** $f_{1} \,{,}\ldots{,}\,f_{n}$, their **pointwise maximum** $$g(x) := \max\left\{ f_{1}(x) \,{,}\ldots{,}\,f_{n}(x) \right\}$$ is also **convex**.

^59d4d8

>[!important] Danskin's Theorem
>If for every $y$ in **compact set** $\mathcal{Y} \subset \mathbb{R}^{m}$, $f(\cdot, y)$ is **convex functions**, then the **supremum** 
>$$
>g(x) = \sup_{y \in \mathcal{Y}}f(x, y)
>$$
> is also **convex** and the **domain** of $g$ is $$\text{dom}(g) = \{ x: (x, y) \in \text{dom}(f), \; \forall y\in \mathcal{Y},\;  \sup_{y \in \mathcal{Y}}f(x, y) < \infty \}. $$
> 
> The **epigraph** of $g$ is the *intersection of epigraphs*
>$$
>\text{epi}(g) = \bigcap_{y \in \mathcal{Y}}\text{epi}(f(\cdot, y)).
>$$

^8828bd

- [[Epigraph or Supergraph of Function]]
- Wikipedia [Danskin%27s_theorem](https://en.wikipedia.org/wiki/Danskin%27s_theorem)
- [[Nonlinear Programming by Bertsekas]]



### Convex Conjugate 

>[!important]
>If $f: \mathbb{R}^n \to \mathbb{R}$ is convex, with $\text{dom}(f) = \mathbb{R}^n$, then 
>$$
>f(x) = \sup\left\{ g(x):\; g \text{ is affine, } g(z) \le f(z),\; \forall z\right\} 
>$$


![[Legendre Transform#^fff1cb]]

- [[Convex Conjugate Function]]
- [[Legendre Transform]]


### Composition 

>[!important] Proposition
>Suppose that both $f$ and $g$ are **twice differentiable functions**.
>- If $f$ is **convex** and **non-decreasing**, and $g$ is **convex**, then  $f \circ g$ is **convex**.
>- If $f$ is **convex** and **non-increasing**, and $g$ is **convex**, then  $f \circ g$ is **concave**.
>- If $f$ is **concave** and **non-decreasing**, and $g$ is **concave**, then  $f \circ g$ is **concave**.
>- If $f$ is **concave** and **non-increasing**, and $g$ is **concave**, then  $f \circ g$ is **convex**.

- [[Exp-Concave Function]]

>[!important] Proposition
>For a **convex function** $f$, define the **extended-value extension**
>$$
>\bar{f}(x) = \left\{
>\begin{array}{cc}
> f(x) & x \in \text{dom}(f) \\
> +\infty &  x \not\in \text{dom}(f)
>\end{array}
>\right.
>$$
>Similarly, for a **concave function** $g$, define the **extended-value extension**
>$$
>\bar{g}(x) = \left\{
>\begin{array}{cc}
> g(x) & x \in \text{dom}(g) \\
> -\infty &  x \not\in \text{dom}(g)
>\end{array}
>\right.
>$$
>
>
>- If $f$ is **convex**, and $\bar{f}$ is **non-decreasing**, and $g$ is **convex** , then  $f \circ g$ is **convex**.
>- If $f$ is **convex**, and $\bar{f}$ is **non-increasing**, and $g$ is **convex**, then  $f \circ g$ is **concave**.
>- If $f$ is **concave**, and $\bar{f}$ is **non-decreasing**, and $g$ is **concave**, then  $f \circ g$ is **concave**.
>- If $f$ is **concave**, and $\bar{f}$ is **non-increasing**, and $g$ is **concave**, then  $f \circ g$ is **convex**.

>[!info]
>- If $f$ is **convex**, then $\exp(f)$ is **convex**.
>- If $f$ is **concave** and **positive**, then $\log(f)$ is **concave**.
>- If $f$ is **concave** and **positive**, then $1 / f$ is **convex**.

### Minimization of Jointly Convex Function Over Convex Set

>[!important] Proposition
>Let $C \subset \mathbb{R}^{d}$ be a **convex set**, and $f: \mathbb{R}^{d} \times  \mathbb{R}^{d} \to \mathbb{R}$ be a **proper jointly convex function**.
>
>Then 
>$$
>g(x) := \inf_{y \in C}f(x, y)
>$$
>is **convex** in $x$ given that $$g(x) > - \infty, \;\;\text{ for some }x.$$ The domain of $g$ is
>$$
>\text{dom}(g) := \left\{ x: (x,y)\in \text{dom}(f), \;\; \text{ for some }y \right\} 
>$$

^316418

>[!important] Proposition
>Suppose $h: \mathbb{R}^{m} \to \mathbb{R}$ is **convex**. Then the function $g: \mathbb{R}^{n}\to \mathbb{R}$ defined by
>$$
>g(x) = \inf\left\{ h(y): \; Ay = x \right\} 
>$$
>where $A\in \mathbb{R}^{n\times m}$, is **convex**.




### Perspective Function

![[Perspective Function#^4c8078]]

![[Perspective Function#^7f2372]]

- [[Perspective Function]]







## Explanation





-----------
##  Recommended Notes and References

- [[Convex Function]]

- [[Convex Optimization by Boyd]] pp 79 - 90