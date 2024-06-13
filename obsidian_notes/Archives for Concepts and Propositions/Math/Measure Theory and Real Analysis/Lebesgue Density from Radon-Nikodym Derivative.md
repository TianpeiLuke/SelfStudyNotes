---
tags:
  - concept
  - math/measure_theory
  - math/real_analysis
keywords:
  - lebesgue_density
topics:
  - measure_theory
name: Lebesgue Density from Radon-Nikodym Derivative
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Lebesgue Density from Radon-Nikodym Derivative

>[!important] Definition
>If $E$ is a *measureable set* in $\mathbb{R}^{d}$, $x\in \mathbb{R}^{d}$ is a **point of Lebesgue density** *of $E$* if
>$$
> \begin{align*}
> \lim\limits_{B \ni x,\; m(B)\rightarrow 0}\frac{m(B\cap E)}{m(B)} &= 1.
> \end{align*} 
>$$ 

- [[Lebesgue Measure]]
- [[Metric Topology and epsilon-ball]]

>[!important]
>Loosely speaking, it says that a small ball $B$ contains $x$ are *almost entirely covered by $E$*. 
>
>Then for any $\alpha<1$ close to $1$, and *every ball* $B$ of *sufficiently small radius* containing $x$, we have
>$$
> \begin{align*}
> m(E\cap B) &\ge \alpha\, m(B).
> \end{align*}
>$$


## Relation with Radon-Nikodym Derivative

>[!important] Theorem
>Let $\nu$ be a **regular signed measure** on $\mathbb{R}^{d}$, and let $$d\nu = d\lambda+ fdm$$ be its *Lebesgue-Radon-Nikodym decomposition*, where $\lambda \perp m$.  
>
>Then for *$m$-almost every* $x\in \mathbb{R}^{d}$,
>$$
> \begin{align*}
> \lim\limits_{r\rightarrow 0}\frac{\nu(E_{r})}{m(E_{r})} &= f(x),
> \end{align*}
>$$  
>where $E_{r}$ **shrinks regularly** to $x$.

- [[Lebesgue Measure]]
- [[Lebesgue-Radon-Nikodym Theorem]]
- [[Radon-Nikodym Derivative]]
- [[Pointwise Almost Everywhere Convergence]]
- [[Set Shrink Regularly and Bounded Eccentricity]]

>[!info]
>This theorem establish a one-to-one correspondence between the **Radon-Nikodym derivative** and the **Lebesgue density**.
>$$
> \frac{d\nu}{dm} = \lim_{ r \to 0 } \frac{\nu(E_{r})}{m(E_{r})}
>$$

- [[Radon-Nikodym Derivative]]


## Explanation

>[!info]
>The definition of **Vitali covering** is to make sure that the *Lebesgue density* is well defined.

- [[Vitali Covering]]


## Properties

>[!important] Proposition
>Suppose $E$ is a measureable set in $\mathbb{R}^{d}$. 
>
>Then
>
>- *Almost every* $x\in E$ is a point of **Lebesgue density** of $E$;
>- *Almost every* $x\not\in E$ is **not** a point of *Lebesgue density* of $E$.
>

^7e0527
- [[Lebesgue Set of Locally Integrable Function]]

>[!info]
>This proposition show that for *Lebesgue density* is **well defined** for *measurable sets*.





-----------
##  Recommended Notes and References


- [[Lebesgue-Radon-Nikodym Theorem]]
- [[Radon-Nikodym Derivative]]
- [[Pointwise Almost Everywhere Convergence]]
- [[Lebesgue Measure]]


- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]