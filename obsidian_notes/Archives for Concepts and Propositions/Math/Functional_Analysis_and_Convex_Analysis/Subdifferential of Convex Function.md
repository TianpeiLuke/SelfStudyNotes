---
tags:
  - concept
  - math/convex_analysis
keywords:
  - subdifferential
  - subgradient
topics:
  - convex_analysis
name: Subdifferential of Convex Function
date of note: 2024-05-17
---

## Concept Definition

>[!important]
>**Name**: Subdifferential of Convex Function

>[!important] Definition
>A vector $x^{*}$ is said to be a **subgradient** of a convex function $f: X \to \mathbb{R}$ at a point $x$ if for any point $z \in X$,
>$$
>f(z) \ge f(x) + \left\langle  x^{*}\,,\, z - x   \right\rangle
>$$
>
>This condition is referred to as **the subgradient inequality**.

- [[Convex Function]]
- [[Gradient of Smooth Map]]


>[!important] Definition
>The *set of all subgradients* of $f$ at $x$ is called the **subdifferential** of $f$ **at** $x$.
>
>The *subdifferential* of $f$ at $x$ is denoted as $\partial f(x).$ That is,
>$$
>\partial f(x) = \{ v:  f(z) \ge f(x) + \left\langle v\,,\, z - x   \right\rangle\; \forall z \in X \}
>$$

- [[Differential of a Smooth Map at Point]]


>[!important] Definition
>The multivalued mapping $$\partial f: x \mapsto \partial f(x)$$ is called the **subdifferential of $f$.**


## Explanation

>[!info]
>When $f$ is finite at $x$, then the subgradient has a **geometric interpretation**:
>
>the graph of the affine function $$h(z) := f(x) + \left\langle  x^{*}\,,\, z - x   \right\rangle$$ is a **non-vertical supporting hyperplane** to *the convex epigraph* $\text{epi}(f)$ at point $x$. 

- [[Epigraph or Supergraph of Function]]
- [[Supporting Hyperplane of Convex Set]]
- [[Support functional of Convex Set]]

>[!important]
>By definition, $\partial f(x)$ is always a **closed convex set**.

## Properties

>[!important] Proposition 
>For any **proper convex** function $f$ and any vector $x$,   the following four conditions on a vector $x^{*}$ are **equivalent** to each other:
>- $$x^{*} \in \partial f(x);$$
>- $$\left\langle x^{*}\,,\,z \right\rangle - f(z)$$ achieves its **supremum** in $z$ at $z = x$;
>- $$f(x) + f^{*}(x^{*}) \le \left\langle  x^{*}\,,\,x \right\rangle;$$
>- $$f(x) + f^{*}(x^{*}) = \left\langle  x^{*}\,,\,x \right\rangle.$$
>
>If $\bar{f}(x) = f(x)$, three **more conditions** can be added to this list
>- $$x \in \partial f^{*}(x^{*})$$
>- $$\left\langle z^{*}\,,\,x \right\rangle - f^{*}(z^{*})$$ achieves its **supremum** in $z^{*}$ at $z^{*}= x^{*}.$
>- $$x^{*} \in \partial  \bar{f}(x).$$
>
>Note that $f^{*}$ is the Legendre transform of $f$,.
 
- [[Legendre Transform]]



## Relation with Gradient

>[!info]
>If $f$ is **differentiable**, then the **subgradient** is **unique** and it is equal to the **gradient** itself.
>
>$$
>\partial f(x) = \{ \nabla f(x) \}
>$$

- [[Relationship Subgradient to Gradient]]

## Generalization to Locally Convex Space

>[!important] Definition
>Let $X$ be a *locally convex space* and $V \subset X$ is a *convex* subset. Let $f: V \to \mathbb{R}$ be a real-valued *convex function* on $V$. 
>
>A linear *functional* $f^{*} \in X^{*}$ in the dual space is called the **subgradient of** $f$ **at** $x\in V$ if for all $z \in V$, 
>$$
>f(z) \ge f(x) + \left\langle  f^{*}\,,\, z - x   \right\rangle,
>$$
>where $\left\langle  \,,\,    \right\rangle: X^{*} \times X \to \mathbb{R}$ is the [[Canonical Dual Pairing]].

- [[Locally Convex Space]]




-----------
##  Recommended Notes and References

- [[Convex Function]]
- [[Epigraph or Supergraph of Function]]
- [[Supporting Hyperplane of Convex Set]]
- [[Differential of a Smooth Map at Point]]
- [[Gradient of Smooth Map]]


- [[Convex Analysis by Rockafellar]]