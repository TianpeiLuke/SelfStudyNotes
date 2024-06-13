---
tags:
  - concept
  - math/set_theory
keywords:
  - surjective_function
topics:
  - set_theory
name: surjective function
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Surjective Function

>[!important] Definition
>A map $f: X\rightarrow Y$ is **surjective**, or, **onto**, if for *every* $y \in Y$, there *exists* a $x \in X$ such that $y = f(x)$.

>[!important]
>By definition, $f: X \to Y$ is *surjective*, then the **range** of $f$ is a superset of its **image/co-domain,** i.e. 
>$$
>Y \subseteq f(X)
>$$ 

## Explanation

>[!info]
>If a function is surjective, then *every value* in the **co-domain** is the *output* of $f$. 


>[!important]
>If $f:X\to Y$ is **surjective**, then 
>$$
>f^{-1}(Y) \subseteq X 
>$$

>[!info]
>This means that for any subset $U$ of $Y$, $f^{-1}(U) \neq \emptyset.$

>[!important]
>If $f: X \to Y$ is **surjective**, then for any $U  \subseteq Y$,
>
>$$
>\begin{align*}
>f(f^{-1}(U)) &= U
\end{align*}
>$$
>That is, $U$ can be **recovered** from its *preimage*. 


>[!info]
>The surjective map is used when we want to map a group of elements in domain $X$ into one element in co-domain $Y$. 
>
>- A typical example is **the quotient map** that maps an equivalence class of elements into one point.
>- Another example is **the canonical projects** from product space to its coordinates.

- [[Canonical Projection]]


>[!important]
>If $f: X\to Y$ is **surject**, then the domain has at least as many element as the co-domain 
>$$
>\lvert X \rvert \ge \lvert Y \rvert.  
>$$

## Properties

>[!important] Proposition
>The following statements for composite functions are true:
>
>- If $f, g$ are both **surjective**, then $g \circ f$ is **surjective**. 
>- If $g \circ f$ is **surjective**, then $g$ is **surjective**.


>[!important] Proposition
>Every **surjective** map $f: X \rightarrow Y$ can be writen as $$f =  f_{p} \circ \pi$$ where $\pi: X\rightarrow (X/\sim)$ is a **quotient map**, i.e. projection $$x \mapsto [x]$$ for the equivalent relation $$x \sim y \Leftrightarrow f(x) = f(y)$$ and  $f_p: (X/\sim) \rightarrow Y$ is defined as $f_p([x]) = f(x)$ **constant** in each coset $[x]$.

- [[Quotient Map]]
- [[Equivalence Relation]]
- [[Equivalence Relation]]



## Example

>[!example]
>The [[Canonical Projection]] is a **surjective map**.
>
>Let $\pi_{i} : \prod_{i=1}^n X_{i} \rightarrow X_{i}$ be defined by the equation
>$$
> \begin{align*}
> \pi_i (x_{1} \,{,}\ldots{,}\, x_{n}) = x_{i};
> \end{align*}
>$$
>$\pi_{i}$ is the **canonical projection onto $i$-th coordinate**.

>[!example] 
>The [[Quotient Map]] is a **continuous surjective map**.
>
>In particular, for a set $X$ and $\sim$ is an equivalence relation on $X$. The projection from $X$ to its [[Quotient Set]], is a *surjective map*, i.e. $\pi : X \to X / \sim$ defined by
>$$
>\pi: x \to [x], \quad x\in X
>$$ 
>
>For every equivalence class $[x]$, $x \in [x]$.  






-----------
##  Recommended Notes and References

- [[Function]]

- [[Topology Book by Munkres]]