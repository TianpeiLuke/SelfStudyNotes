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
>**Name**: Lebesgue Differentiation Theorem

### One-dimensional $\mathbb{R}$

>[!important] Lebesgue Differentiation Theorem (one dimensional, first formulation)
>Let $f: \mathbb{R} \rightarrow \mathbb{C}$ be an **absolutely integrable** function, and let $F: \mathbb{R} \rightarrow \mathbb{C}$ be the *definite integral* $$F(x) := \int_{[-\infty,x]} f(t) dt.$$ 
>
>Then $F$ is **continuous** and **almost everywhere differentiable**, and $$F'(x) = f(x)$$ for *almost every* $x \in \mathbb{R}$.



>[!important]  Lebesgue Differentiation Theorem (one dimensional, second formulation)
>Let $f: \mathbb{R} \rightarrow \mathbb{C}$ be an **absolutely integrable** function. 
>
>Then
>$$
> \begin{align}
>  \lim\limits_{h\rightarrow 0+}\frac{1}{h} \int_{[x,x+h]} f(t) dt = f(x)
> \end{align}
>$$  
>for *almost every* $x \in \mathbb{R}$, and
>$$
> \begin{align}
>  \lim\limits_{h\rightarrow 0+}\frac{1}{h} \int_{[x-h,x]} f(t) dt = f(x) 
> \end{align}
>$$
>for *almost every* $x \in \mathbb{R}$.

### $d$-dimensional $\mathbb{R}^d$

>[!important]  Lebesgue Differentiation Theorem ($\mathbb{R}^d$ case)
>Suppose $f: \mathbb{R}^{d} \rightarrow \mathbb{C}$ is **absolutly integrable**. 
>
>Then for *almost every* $x$, we have 
>$$
> \begin{align}
> &\lim\limits_{r\rightarrow 0}\frac{1}{m(B(x, r))}\int_{B(x, r)}\lvert f(z) - f(x) \rvert dz = 0 \\
>\end{align}
>$$
>and
>$$ 
>\begin{align}
> \lim\limits_{r\rightarrow 0}\frac{1}{m(B(x, r))}\int_{B(x, r)}f(z) dz = f(x), \nonumber
> \end{align}
>$$ 
> where $B(x, r) := \{ y \in \mathbb{R}^d : \lVert x - y \rVert < r\}$ is the **open ball** of radius $r$ *centered at* $x$.

- [[Pointwise Almost Everywhere Convergence]]
- [[Absolutely Convergent Integration]]




## Explanation





-----------
##  Recommended Notes and References

- [[Pointwise Almost Everywhere Convergence]]
- [[Absolutely Convergent Integration]]

- [[Density Argument for Asymptotic Analysis]]

- [[Introduction to Measure Theory by Tao]]