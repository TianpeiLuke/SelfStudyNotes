---
tags:
  - concept
  - math/set_theory
keywords:
  - preimage_function
  - range_function
topics:
  - set_theory
name: preimage and range of function
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: *Preimage* and *Range* of Function

>[!important] Definition
>Let $f: X\rightarrow Y$ be a function. The set $X$ is the **domain** of $f$, and the set $Y$ is the **co-domain**, or **image** of $f$.
>
>- The **range** of $f$ is the set of all possible assignments for all $x \in X$
>$$f(X) := \{y: y = f(x), x\in X \}$$  
>- The **preimage** of $f$ under set $U \subset Y$ is the set of all possible $x$ such that $f(x) \in U$, i.e.
>$$
>f^{-1}(U) := \{ x\in X: f(x) \in U  \}.
>$$  



## Explanation

>[!info]
>The range is within the image
>$$
>f(X) \subset Y
>$$
>and the preimage is within the domain
>$$
>f^{-1}(V) \subset X
>$$


>[!important]
>By definition, for any function $f: X \to Y$ and $V \subseteq X$,
>$$
>V \subseteq  f^{-1}(f(V))
>$$
>
>For **surjective** function, the subset is strict.



-----------
##  Recommended Notes and References

- [[Function]]

- [[Topology Book by Munkres]]