---
tags:
  - entry_point
  - concept
  - math/real_analysis
keywords: 
topics:
  - real_analysis
name: Development of Integrations
date of note: 2024-05-13
---

## Concept Definition

### Riemann Integration

>[!important] Definition
>Let $f: [a,b] \to \mathbb{R}$ be a *bounded function*, i.e. there exists some $M >0$ such that $$|f(x)| \le M$$ for all $x\in [a, b].$
>
>Given a partition $P = \left\{ x_{0}, x_{1} \,{,}\ldots{,}\, x_{n} \right\}$ of $[a,b]$, the **Darboux lower sum** of $f$ *with respect to* $P$ is defined as
>$$
>\begin{align*}
>L(f, P) := \sum_{k=1}^{n}m_{k}\left( x_{k} - x_{k-1} \right)
>\end{align*}
>$$
>where 
>$$
>m_{k} = \inf\left\{ f(x): x \in [x_{k-1}, x_{k}] \right\}.
>$$
>
>Similarly, the **Darboux upper sum** of $f$ *with respect to* $P$  is defined as
>$$
>\begin{align*}
>U(f, P) := \sum_{k=1}^{n}M_{k}\left( x_{k} - x_{k-1} \right)
>\end{align*}
>$$
>where
>$$
>M_{k} = \sup\left\{ f(x): x \in [x_{k-1}, x_{k}] \right\}.
>$$

>[!important]
>The **Riemann lower integral** of $f$ is defined as
>$$
>\begin{align*}
>L(f) := \sup\left\{L(f, P): P\in \mathcal{P}  \right\}
>\end{align*}
>$$
>where $L(f, P)$ is the *Darboux lower sum* with respect to a partition $P\in \mathcal{P}$.
>
>Similarly, the **Riemann upper integral** of $f$ is defined as
>$$
>\begin{align*}
>U(f) = \sup\left\{ U(f, P): P\in \mathcal{P} \right\}
>\end{align*}
>$$
>where $U(f, P)$ is the *Darboux upper sum* with respect to a partition $P\in \mathcal{P}$.


>[!important] Definition 
>We say that $f$ is **Riemann-integrable** if $$L(f) = U(f).$$ We denote it as
>$$
>\int_{a}^{b}f(x)\,dx = U(f) = L(f)
>$$


- [[Darboux Lower Sum and Darboux Upper Sum]]
- [[Riemann Integration]]
- [[Criterion of Riemann-Stieltjes Integrability]]

### Riemann–Stieltjes Integration

- [[Riemann–Stieltjes Integration]]

### Lebesgue Integration

>[!important]
>- **Unsigned Simple Function**:
>  $$
>  f = \sum_{i=k}^{m}c_k \mathbb{1}_{E_k}
> $$
> 
>-  **Unsigned Measurable Function**
> $$
>  \set{f_n} \rightarrow f \text{ pointwise} 
>$$
>where $\set{f_n}$ is a sequence of **unsigned simple functions.**
>- **Abusolute Integrable Function**
>  $$
>  \lVert f \rVert_{L^1(\mathbb{R}^d)}  < \infty 
>  $$
> where $|f|$ is **unsigned measurable function.**


>[!important]
>- **Simple Integration** of **Unsigned Simple Function**:
>$$
>\text{simp }\int_{\mathbb{R}^d} f(x) dx = \sum_{i=k}^{m}c_k \mu(E_k)
>$$
> 
>-  Integration of the **Unsigned Measurable Function**
> $$
> \begin{align*}
>\int_{\mathbb{R}^{d}}f(x)dx &:=  \underline{\int_{\mathbb{R}^{d}}}f(x)dx \\
>&= \sup\limits_{0\le g\le f,\; g\text{ simple}} \text{simp}\int_{\mathbb{R}^{d}}g(x) dx
\end{align*}
>$$
>
>- Integration of the **Abusolute Integrable Function**
> $$
> \int_{\mathbb{R}^{d}}f(x)dx = \int_{\mathbb{R}^{d}}f_{+}(x)dx - \int_{\mathbb{R}^{d}}f_{-}(x)dx.
>$$

- [[Simple Integral of Simple Functions]]
- [[Unsigned Integral of Functions]]
- [[Absolutely Convergent Integration]]
- [[Criteria for Measurability]]

### Lebesgue-Stieltjes Integration

- [[Lebesgue-Stieltjes Measure]]
- [[Lebesgue-Stieltjes Integration]]


## Comparison 

|                                       | **Unsigned Simple Function** | **Unsigned Measurable Function**     | **Abusolute Integrable Function** |
| ------------------------------------- | ---------------------------- | ------------------------------------ | --------------------------------- |
| **Compatibility**                     |                              | $\checkmark$                         | $\checkmark$                      |
| **Compatibility to Riemann Integral** | $\checkmark$                 | $\checkmark$                         | $\checkmark$                      |
| **Linearity**                         | Unsigned $\checkmark$        | $\checkmark$                         | $\checkmark$                      |
| **Equivalence**                       | $\checkmark$                 | $\checkmark$                         | $\checkmark$                      |
| **Vanishing**                         | $\checkmark$                 | $\checkmark$                         | $\checkmark$                      |
| **Monotonicity**                      | $\checkmark$                 | $\checkmark$                         | $\checkmark$                      |
| **Superadditivity**                   |                              | lower Lebesgue integral $\checkmark$ |                                   |
| **Reflection**                        |                              | lower Lebesgue integral $\checkmark$ |                                   |
| **Divisibility**                      |                              | lower Lebesgue integral $\checkmark$ |                                   |
| **Finite additivity**                 | $\checkmark$                 | $\checkmark$                         | $\checkmark$                      |
| **Horizontal truncation**             |                              | $\checkmark$                         | $\checkmark$                      |
| **Vertical truncation**               |                              | $\checkmark$                         | $\checkmark$                      |
| **Translation Invariance**            |                              | $\checkmark$                         | $\checkmark$                      |

## Important Convergence Theorem

- [[Monotone Convergence Theorem]]
- [[Fatou Lemma]]
- [[Dominated Convergence Theorem]]

- [[Uniform Integrable Family of Functions]]
- [[Vitali Convergence Theorem for Uniformly Integrable Tight Functions]]
- [[Vitali Lp Convergence Theorem]]

## Mode of Convergence

- [[Summary of Modes of Convergence]]
- [[Modes of Convergence]]

## Littlewood's Three Principles

>[!important] Littlewood's Three Principles in $\mathbb{R}^n$
>1. Every (**measurable**) set is **nearly** a **finite sum** of **intervals**;
>2. Every (**absolutely integrable**) function is **nearly** **continuous**;
>3. Every (**pointwise**) **convergent** sequence of functions is **nearly** **uniformly convergent**
>

- [[Littlewood Principles]]
	- [[Lebesgue Measure#Criteria for Measurability]]
	- [[Simple Approximation Theorem of Lp Function]]
	- [[Lusin Theorem]]
	- [[Egorov Theorem]]





-----------
##  Recommended Notes and References



- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Real Analysis by Royden]]
- [[Probability and Measure by Billingsley]]
- [[Principles of Mathematical Analysis by Rudin]] pp 321
