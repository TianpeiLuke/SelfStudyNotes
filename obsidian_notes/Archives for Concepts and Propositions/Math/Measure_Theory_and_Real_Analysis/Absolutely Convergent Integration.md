---
tags:
  - concept
  - math/real_analysis
  - math/measure_theory
keywords:
  - absolutely_convergenct_integration
topics:
  - real_analysis
  - measure_theory
name: Absolutely Convergent Integration
date of note: 2024-05-13
---

## Concept Definition

>[!important]
>**Name**:  Absolutely Convergent Integration

>[!important] Definition
>Let $(X, \mathscr{F}, \mu)$ be a measure space. A *measurable function* $f : X \rightarrow \mathbb{C}$ is said to be **absolutely integrable** if the *unsigned integral* 
>$$
> \begin{align*}
>  \lVert f \rVert_{L^{1}(X)} &:= \int_{X}\;\lvert f \rvert \;d\mu 
> \end{align*}
>$$ 
> is **finite**. 

- [[Unsigned Integral of Functions]]

>[!important] Definition
> We refer to this quantity $\lVert f \rVert_{L^{1}(X)}$ as **the $L^1(X)$ norm** of $f$.
> 
> We use $L^1(X)$ or $L^1(X, \mathscr{F}, \mu)$ or $L^1(\mu)$ to denote **the space of absolutely integrable functions.** 

- [[Lp Space]]
- [[Norm and Normed Space]]
- [[Banach Space]]

>[!info]
> Sometimes $$\int_{X}f d\mu$$ is also denoted as $$\int_{X}f(x)\mu(dx)$$ or $$\int_{X}f(x) d\mu(x),$$ 
> where $X\subseteq \mathbb{R}^{d}$ and $\mu(E) = \int_{E}\mu dx$.

## Integration of Absolutely Integrable Function

>[!important] Definition
> If $f$ is *real-valued* and *absolutely integrable*, we define **the Lebesgue integral**  by the formula
>$$ 
> \begin{align*}
> \int_{X}f d\mu &= \int_{X}f_{+}d\mu - \int_{X}f_{-}d\mu
> \end{align*}
>$$ 
> where $f_{+} = \max\set{f, 0}$ and $f_{-} = \max\set{-f, 0}$ are the *magnitudes* of the **positive** and **negative components** of $f$. 

>[!info]
>Note that the two unsigned integrals on the right-hand side are finite, as $f_+, f_{-}$ are **pointwise dominated** by $|f|$. 


>[!important] Definition
>If $f$ is *complex-valued* and *absolutely integrable*, we define **the Lebesgue integral**  by the formula
>$$
> \begin{align*}
> \int_{X}f d\mu &= \int_{X}\Re( f ) d\mu  + i\,\int_{X}\Im(f) d\mu,
> \end{align*}
>$$ 
> where the two integrals on the right are interpreted as *real-valued absolutely integrable Lebesgue integrals*.



## Explanation




## Property

>[!important] Proposition
>Suppose $f, g\in L^1(X, \mu)$ and $\alpha, \beta\in \mathbb{R}$.
>
>Then 
>- **Linearity**: $$\int_{X} (\alpha\,f + \beta\,g)\,d\mu = \alpha\,\int_{X} f\,d\mu + \beta \int_{X} g\,d\mu $$
>- **Monotonicity**: if $f \le g$ on $X$, then $$\int_{X} f\,d\mu \le \int_{X} g\,d\mu.$$
>- **Finite Partition on Integral Region**: if $f\in L^1(X, \mu)$ on $[a,b]$, and $$X = \bigcup_{i=1}^{n}X_{i}$$ where $X_{i} \cap X_{j} = \emptyset$, then $f\in L^1(X_{i}, \mu)$ for $i=1 \,{,}\ldots{,}\,n$. And $$\int_{X} f\,d\mu  = \sum_{i=1}^{n}\int_{X_{i}} f\,d\mu.$$
>- **Linearity in Measure**: if $f\in L^1(X, \mu_{1})$ and $f\in L^1(X, \mu_{2})$, then $f\in L^1(X, \alpha\mu_{1} + \beta\mu_{2})$ and $$\int_{X} f d\left( \alpha\mu_{1} + \beta\mu_{2} \right) = \alpha\,\int_{X} f\,d\mu_{1} + \beta \int_{X} f\,d\mu_{2} $$
>- **Norm**: $|f| \in L^1(X, \mu)$ and $$\left|\int_{X} f\,d\mu\right| \le \int_{X} |f|\,d\mu.$$
>- **Almost Everywhere Equivalence Class**: If $$f(x) = g(x), \text{ $\mu$-almost every }x\in X,$$ then $$\int_{X}f d\mu = \int_{X} g d\mu.$$
>- **Vanishing**: if $f \in L^1(X, \mathscr{F}, \mu)$, then $$\lVert f \rVert_{L^1} = 0 \quad \iff \quad f=0, \;\;\mu\text{-almost everywhere}.$$
>- **Vertical Truncation**: $$\lim_{ n \to \infty } \int_{X} \min\{f, n\}\,d\mu = \int_{X} f\,d\mu$$
>- **Horizontal Truncation**: Let $$E_{1} \subseteq E_{2} \,{\subseteq}\ldots{\subseteq}\, $$ be a *monotone sequence* of $\mathscr{F}$-measurable sets, then $$\lim_{ n \to \infty } \int_{X}f\, \mathbb{1}_{E_{n}}\,d\mu = \int_{X} f\,d\mu.$$
>- **Refinement**: If $(X, \mathscr{F}', \mu')$ is a **refinement** of $(X, \mathscr{F}, \mu)$, i.e. $\mathscr{F}' \subseteq \mathscr{F}$ and $\mu' = \mu|_{\mathscr{F}'},$ and $f\in L^1(X, \mathscr{F}, \mu)$, then $$f\in L^1(X, \mathscr{F}', \mu').$$ 
>- **Restriction on Measurable Set**: Suppose $A \in \mathscr{F}$ and $A \subset B$, and $f\in L^1(X, \mathscr{F}, \mu)$, then $$\int_{A} f|_{A}\; d\mu|_{A} = \int_{X} f\, \mathbb{1}_{A}\; d\mu.$$ We would write $\int_{A} f\; d\mu := \int_{A} f|_{A}\; d\mu|_{A}.$

- [[Monotone Sequence of Nested Sets]]
- [[Restriction of Measure on Subset]]

## Change of Variable

>[!important] Proposition
>Let $f \in L^1(\mathbb{R}^n, m)$ be absolutely integrable with respect to *Lebesgue measure*, and let $T: \mathbb{R}^n \to \mathbb{R}^n$ be an **invertible linear transformation**. 
>
>Then
>$$
>\begin{align*}
>\int_{\mathbb{R}^n}f\left( T^{-1}(x) \right)\,dx = \lvert \det(T) \rvert \int_{\mathbb{R}^n} f(x)\,dx 
>\end{align*}
>$$
>or, equivalently,
>$$
>\begin{align*}
>\int_{\mathbb{R}^n}f\left( T(x) \right)\,dx = \lvert \det(T) \rvert^{-1} \int_{\mathbb{R}^n} f(x)\,dx 
>\end{align*}
>$$


>[!important]
>The change of variable corresponds to the **pushforward measure**
>$$
>\int_{\mathbb{R}^n} (f\circ T)\, d\mu = \int_{\mathbb{R}^n} f \,d(T_{*}\mu)
>$$
>The *pushforward* of *Lebesgue measure* $m$ by $T$ can be obtained as
>$$
>T_{*}m = \frac{1}{|\det(T)|}m
>$$

- [[Push-forward Measure and Push-forward Operator]]


## Compatibility with Riemann Integration

>[!important] Proposition
>Let $f: [a,b]\to \mathbb{R}$ be **Riemann integrable**. Let $F: \mathbb{R} \to \mathbb{R}$ be *extension* of $f$ such that 
>$$
>F(x) = f(x), \; x\in [a,b], \quad \text{otherwise } F(x) = 0.
>$$
>
>Then $F\in L^1(\mathbb{R}, m)$ is **Lebesgue integrable** and
>$$
>\int_{\mathbb{R}}F(x)\,dx = \int_{a}^{b}f(x)\,dx.
>$$

- [[Riemann Integration]]

## Markov Inequality

- [[Markov Inequality]]


## Integral by Parts

- [[Integration by Parts]]





-----------
##  Recommended Notes and References

- [[sigma Algebra Generated by Sets]]
- [[Measure Space and Countably Additive Measure]]
- [[Measurable Function]]
- [[Pointwise Almost Everywhere Convergence]]
- [[Lebesgue-Stieltjes Integration]]

- [[Real Analysis by Royden]]
- [[Introduction to Measure Theory by Tao]]