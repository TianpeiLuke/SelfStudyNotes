---
tags:
  - concept
  - statistics/concentration_inequality
  - math/information_theory
keywords:
  - log_sobolev_inequality
topics:
  - concentration_inequality
  - information_theory
name: Logarithmic Sobolev Inequality for Gaussian Random Variables
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Logarithmic Sobolev Inequality for Gaussian Random Variables

>[!important] Theorem (Logarithmic Sobolev Inequality for Independent Gaussian Random Variables)
>Let $f: \mathbb{R}^n \to \mathbb{R}$ be a **continuous differentiable** function and let $$Z = (Z_1 \,{,}\ldots{,}\, Z_n)$$ be a vector of $n$ **independent** **standard Gaussian random variables**. 
>
>Then
>$$
> \begin{align}
> \text{Ent}(f^2(Z)) &\le 2  \mathbb{E}_{}\left[\lVert \nabla f(Z) \rVert_{2}^2   \right].  
> \end{align}
>$$ 

^928b56

- [[Entropy Functional]]

>[!important] Theorem (Measure-Theoretical Version)
>Let $f \in L^2(\mathbb{R}^n, \mathcal{N})$ be a real-valued functions on $\mathbb{R}^n$ such that
>$$
>\lVert f \rVert_{L^2(\mathcal{N})} := \int_{\mathbb{R}^n} \lvert f \rvert^2\; d\mathcal{N} < +\infty
>$$
>where $\mathcal{N}$ is the **standard Gaussian measure** on $\mathbb{R}^n$, i.e.
>$$
>d\mathcal{N} = \left(\frac{1}{2\pi}\right)^{n/2}\exp \left( -\frac{ \lVert x \rVert_{2}^{2}}{2} \right)dx.
>$$
>
>Then the following inequality holds
>$$
>\begin{align*}
> \int_{\mathbb{R}^n} \lvert f \rvert^2\, \log\left( \lvert f \rvert^2 \right) \; d\mathcal{N} - \left( \int_{\mathbb{R}^n} \lvert f \rvert^2\,d\mathcal{N} \right) \;\log \left( \int_{\mathbb{R}^n} \lvert f \rvert^2\, d\mathcal{N} \right) &\le 2\,\int_{\mathbb{R}^n} \lvert \nabla f \rvert^2 \,d\mathcal{N}  \\
> \implies  \int_{\mathbb{R}^n} f^2 \log \left( \frac{f^2}{\int_{\mathbb{R}^n} f^2\, d\mathcal{N} } \right) d\mathcal{N} &\le  2\,\int_{\mathbb{R}^n} \lvert \nabla f \rvert^2 \,d\mathcal{N} 
\end{align*}
>$$
>or, in simpler form
>$$
>\text{Ent}_{\mathcal{N}}(f^2) \le 2\,\int_{\mathbb{R}^n} \lvert \nabla f \rvert^2 \,d\mathcal{N}  
>$$

- [[Gaussian Measure]]




## Explanation


>[!important] 
>The **Gaussian logarithmic Sobolev inequality** has a *constant* $C = 2$ that is **independent of dimension** $n$:
>$$
>\text{Ent}_{\mathcal{N}}(f^2) \le C\,\int_{\mathbb{R}^n} \lvert \nabla f \rvert^2 \,d\mathcal{N}  
>$$
>
>This **dimension-free property** is related to the **concentration of Gaussian measure** $\mathcal{N}.$
>
>As a consequence, this inequality can be extended to **functions** of *Gaussian measure* on **infinite dimensional space**, such as Gibbs measure, *Gaussian process* etc.

- [[Gaussian Measure]]
- [[Gaussian Random Function]]




## Talagrand's Gaussian Transportation Inequality


>[!important]
>Talagrand's **Gaussian transportation inequality** implies the **Tsirelson-Ibragimov-Sudakov inequality** (i.e. the *dimension-free concentration* of *Lipschitz function* of Gaussian vectors), which we proved based on the **Gaussian logarithmic Sobolev inequality** and **Herbst's argument**.


- [[Talagrand Gaussian Transportation Inequality]]





-----------
##  Recommended Notes and References

- [[Entropy Functional]]
- [[Sobolev Space]]
- [[Talagrand Gaussian Transportation Inequality]]

- [[Concentration Inequalities by Boucheron]]