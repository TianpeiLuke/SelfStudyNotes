---
tags:
  - concept
  - math/real_analysis
keywords: 
topics:
  - real_analysis
name: Lebesgue Differentiation Theorem
date of note: 2024-05-28
---

## Theorem

>[!important]
>**Name**: Lebesgue Differentiation Theorem for Locally Integrable Function

>[!important]  Lebesgue Differentiation Theorem (Locally Integrable Function)
>Suppose $f$ is **locally integrable** on $\mathbb{R}^{d}$. For every $x$ in the *Lebesgue set* of $f$, i.e. for *almost every* $x$, we have 
>$$
> \begin{align*}
> \lim\limits_{U_{\alpha} \ni x,\; m(U_{\alpha})\rightarrow 0}\frac{1}{m(U_{\alpha})}\int_{U_{\alpha}}\lvert f(z) - f(x) \rvert dz = 0
> \end{align*} 
>$$
>and
>$$
> \begin{align*} 
>\lim\limits_{U_{\alpha} \ni x,\; m(U_{\alpha})\rightarrow 0}\frac{1}{m(U_{\alpha})}\int_{U_{\alpha}}f(z) dz = f(x),
> \end{align*}
>$$ 
> for *every family* $\set{U_{\alpha}}$ that **shrinks regularly** to $x$.

- [[Locally Integrable Function]]
- [[Lebesgue Set of Locally Integrable Function]]
- [[Pointwise Almost Everywhere Convergence]]
- [[Set Shrink Regularly and Bounded Eccentricity]]

## Explanation

>[!info]
>This theorem is also called **the First Fundamental Theorem of Calculus.**

- [[Second Fundamental Theorem of Calculus Absolutely Continuous]]

## Proof

- [[Hardy-Littlewood Maximal Theorem]]



-----------
##  Recommended Notes and References

- [[Lebesgue Differentiation Theorem for Absolutely Integrable Function]]
- [[Lebesgue Density from Radon-Nikodym Derivative]]

- [[Locally Integrable Function]]
- [[Lebesgue Set of Locally Integrable Function]]
- [[Pointwise Almost Everywhere Convergence]]
- [[Set Shrink Regularly and Bounded Eccentricity]]

- [[Density Argument for Asymptotic Analysis]]

- [[Introduction to Measure Theory by Tao]]