---
tags:
  - concept
  - math/functional_analysis
  - math/stochastic_process
keywords:
  - dual_pairing
topics:
  - functional_analysis
  - probability
name: Canonical Dual Pairing
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Canonical Dual Pairing

>[!important] Definition
>Let $X$ be a *topological vector space* and $X^{*}$ be its *continuous dual space*. Denoted by
>$$
>\begin{align*}
>\left\langle \cdot , \cdot \right\rangle &: X^{*} \times X \rightarrow \mathbb{R},
>\end{align*}
>$$ 
>the **canonical dual pairing**, such that $$\left\langle x^{*} , x \right\rangle \mapsto x^{*}(x).$$

- [[Topological Vector Space]]
- [[Dual Normed Space and Dual Banach Space]]

## Explanation

>[!important]
>A dual pairing is a **bilinear form.** That is, for linear functional $f, g\in X^{*}$ and any  $x, y \in X$, any $\alpha, \beta \in \mathbb{R}$
>- $\left\langle  \,,\,    \right\rangle$ is linear in its first argument
>  $$
>  \left\langle \alpha f + \beta  g\,,\,  x  \right\rangle = \alpha  \left\langle f\,,\,  x  \right\rangle + \beta   \left\langle g\,,\,  x  \right\rangle
> $$ 
>-  $\left\langle  \,,\,    \right\rangle$ is linear in its second argument
>$$
> \left\langle  f\,,\, \alpha x + \beta y   \right\rangle = \alpha \left\langle  f\,,\,  x   \right\rangle + \beta \left\langle  f\,,\,   y   \right\rangle
>$$ 

>[!info]
>In canonical dual pairing, the bilinear form is an *evaluation map* $\iota: (f, x) \mapsto f(x).$



-----------
##  Recommended Notes and References

- Wikipedia [Dual system](https://en.wikipedia.org/wiki/Dual_system)
- 