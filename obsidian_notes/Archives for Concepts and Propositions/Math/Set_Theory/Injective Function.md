---
tags:
  - concept
  - math/set_theory
keywords:
  - injective_function
topics:
  - set_theory
name: injective function
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Injective Function

>[!important] Definition
>A map $f: X\rightarrow Y$ is **injective**, or **one-to-one**, if for every $x_1 \neq x_2 \in X$, their map $$f(x_1) \neq f(x_2),$$ or, equivalently, $$f(x_1) = f(x_2)$$ **only if** $$x_1 = x_2.$$


## Explanation

>[!info]
>A function is injective, if there are **no two distinct inputs** that **share the same output**.

>[!info]
>If a function is injective, and **two output values** of function **are the same**, then the **input values must be the same.** 

>[!important]
>If $f: X \to Y$ is **injective**, then for any $U  \subseteq X$,
>$$
>\begin{align*}
>f^{-1}(f(U)) &= U
\end{align*}
>$$
>Thus $U$ can be **recovered** by its **image**.

>[!info]
>Injective functions are useful when we are trying to **recover or identify the inputs from outputs only**.


>[!info]
>A injective function may *not be able to* take *every possible values* in its **co-domain.** In other word, $f: X\to Y$ is injective, but no surjective, then for some $V \subset Y$,
>$$
>f^{-1}(V) = \emptyset
>$$


>[!important]
>Injective functions can be made **invertible** if we **restrict the co-domain** of $f$ to be its range. 

>[!important]
>If $f: X\to Y$ is **injective**, then the co-domain has at least as many element as the domain 
>$$
>\lvert Y \rvert \ge \lvert X \rvert.  
>$$

## Examples

>[!example]
>The [[Canonical Inclusion]] is a **injective map**.
>
>If  $X \subset Y$, then the **canonical inclusion map**  $\iota: X \to Y$ be defined by the equation
>$$
> \begin{align*}
> \iota(x) = x,
> \end{align*}
>$$ 
>for $x\in X.$
>
>We also called $\iota$ the **natural injections** and we used 
>$$
>\iota: X \xhookrightarrow{} Y
>$$

- [[Canonical Inclusion]]

## Properties

>[!important] Proposition
>The following statements for composite functions are true:
>
>- If $f, g$ are both **injective**, then $g \circ f$ is **injective**.
>- If $g \circ f$ is **injective**, then $f$ is **injective**.



>[!important] Proposition
> Every **injective** map $f: X \rightarrow Y$ can be writen as $$f = \iota \circ f_{R}$$ where $f_R: X \rightarrow f(X)$ is a **bijective** map and $\iota$ is the **inclusion map**.






-----------
##  Recommended Notes and References

- [[Function]]

- [[Topology Book by Munkres]]