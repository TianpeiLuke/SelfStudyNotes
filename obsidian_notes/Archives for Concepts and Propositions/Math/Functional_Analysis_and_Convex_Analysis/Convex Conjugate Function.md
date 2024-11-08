---
tags:
  - concept
  - math/functional_analysis
  - optimization/theory
  - math/convex_analysis
keywords:
  - legendre_fenchel_transform
  - convex_conjugate
  - fenchel_conjugate
topics:
  - functional_analysis
  - convex_analysis
name: convex conjugate; Legendre-Fenchel Transformation; Fenchel conjugate
date of note: 2024-05-08
---

## Concept Definition

>[!important]
>**Name**:  Convex Conjugate or **Fenchel Conjugate** or **Legendre–Fenchel transformation**


>[!important] Definition
>Let $X$ be a real *topological vector space*, and $X'$ be the **dual space** of $X$. Denoted by
>$$
>\begin{align*}
>\left\langle \cdot , \cdot \right\rangle &: X' \times X \rightarrow \mathbb{R},
>\end{align*}
>$$ 
>the *canonical dual pairing*, such that $\left\langle x^{*} , x \right\rangle \mapsto x^{*}(x).$
>
>For a function $f: X \to \mathbb{R} \cup \left\{ -\infty, +\infty \right\}$ taking values on extended real-number line, its **convex conjugate** is the function
>$$
>f^{*}: X^{*} \to \mathbb{R} \cup \left\{ -\infty, +\infty \right\}
>$$ 
>whose value at $x^{*} \in X^{*}$ is defined as the supremum 
> $$
>\begin{align*}
>f^{*}(x^{*}) &:= \sup_{x \in X}\left\{ \left\langle x^{*},x\right\rangle - f(x) \right\}. 
> \end{align*}
>$$
>or, equivalently, in terms of infimum
> $$
> \begin{align*}
>f^{*}(x^{*}) &:= - \inf_{x \in X}\left\{f(x) - \left\langle x^{*},x\right\rangle  \right\}. 
> \end{align*}
> $$

^2763c0

- [[Convex Function]]
- [[Topological Vector Space]]
- [[Bounded Linear Functional]]'
- [[Canonical Dual Pairing]]


## Explanation

>[!info]
>Note *the dual pairing* is *not an inner product*, but for *Hilbert space*, the dual pairing can be transformed into an inner product since the dual vector and the original vector both in the same space.


>[!info]
>Unlike [[Legendre Transform]], the original function *need not to be a convex function*. The domain $X$ need *not to be convex*.

## Properties

>[!info]
>$f^{*}$ is a convex function, i.e. the domain of $f^{*}$, $X^{*}$ is a convex set.

>[!info]
>The [[Carathéodory Theorem for Convex Hull]] suggests that the convex conjugate function [[Convex Conjugate Function]]
>$$
>f^{*}(x^{*}) := \sup_{x \in X}\left\{ \left\langle x^{*},x\right\rangle - f(x) \right\}
>$$
>is **finite everywhere** if $X$ is **closed, bounded** in $\mathbb{R}^n$, and $f$ is **continuous** with $f(x) = +\infty$ if $x\not\in X$.



## Examples

>[!example]
>Let $$f(\boldsymbol{x}) := \sum_{i=1}^{n}x_{i} \log(x_{i}) = - h(\boldsymbol{x})$$ is the *negative entropy function* for probability mass function $\boldsymbol{x}$.
>
>The convex conjugate of $f$ is **the log-sup-exp function**
>$$
>f^{*}(\boldsymbol{x}^{*}) = \log \left(\sum_{i=1}^{n} \exp \left(x^{*}_{i}\right)\right).
>$$

- [[Shannon Entropy]]
- [[Softmax Function and Log-Sum-Exp Function]]


## Applications

### Calculus of Variations

- [[Lagrangian Function in Mechanics and Variational Calculus]]
- [[Hamiltonian Function in Mechanic and Variational Calculus]]
- [[First Variation of Functional]]

### $f$-Divergence

- [[f-Divergence]]
- [[Variational Formula for f-Divergence]]

### Bregman Divergence

- [[Bregman Divergence]]


### Lagrangian Multipliers and Convex Optimizations

- [[Methods of Lagrangian Multipliers]]
- [[Lagrangian Dual Function]]
- [[Convex Optimization Problem]]

### Concentration Inequality

- [[Cramér–Chernoff Method]]
- [[Moment Generating Function]]



-----------
##  Recommended Notes and References

- [[Legendre Transform]]


- [[Convex Optimization by Boyd]]
- [[Convex Analysis by Rockafellar]]
- [[Optimization by Vector Space Methods by Luenberger]] pp 195


- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)