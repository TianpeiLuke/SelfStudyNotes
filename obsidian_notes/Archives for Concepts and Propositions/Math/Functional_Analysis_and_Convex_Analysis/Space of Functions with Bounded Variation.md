---
tags:
  - concept
  - math/real_analysis
keywords:
  - bouded_variation_function
topics:
  - real_analysis
name: Function of Bounded Variation
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Function of Bounded Variation

### One Dimensional Case


![[Total Variation of Function#^a2e91f]]


>[!important] Definition
>We say that $F: \mathbb{R}\to \mathbb{R}$ has **bounded variation** (on $\mathbb{R}$) if $$\lVert F \rVert_{TV(\mathbb{R})} < \infty.$$
>
>Denote **the space** of functions **with bounded variation** on $\mathbb{R}$ as $$BV(\mathbb{R}) := \left\{ f: \mathbb{R}\to \mathbb{R} :  \lVert f \rVert_{TV(\mathbb{R})} < \infty\right\} $$

- [[Total Variation of Function]]

>[!info]
>In this case, $\lVert F \rVert_{TV(\mathbb{R})}$ is often written as $\lVert F \rVert_{BV(\mathbb{R})}$ or just $\lVert F \rVert_{BV}$.


### Multi-dimensional Case

>[!important] Definition
>The space of **functions with bounded variations** on open subset $\Omega \subset \mathbb{R}^{n}$  is defined as
>$$
> BV(\Omega, \mathbb{R}) := \left\{f: \in L^1(\Omega):  V(f, \Omega)  < \infty \right\} 
>$$
>with **total variation** of $f$ in $\Omega$ is defined as 
>$$
>\begin{align*}
> V(f, \Omega)  := \sup\left\{ \int_{\Omega}f \;\text{div}(\phi)\, dx: \;\; \phi \in \mathcal{C}_{c}(\Omega, \mathbb{R}^n), \; \lVert \phi \rVert_{L^{\infty}(\Omega)} \le 1  \right\} 
\end{align*}
>$$
>where $\text{div}$ is the **divergence operator**, $\mathcal{C}_{c}(\Omega, \mathbb{R}^d)$ is the continuous function from $X \to \mathbb{R}^d$ with *compact support*, $\lVert  \rVert_{\infty}$ is the **essential supremum norm**.

- [[Total Variation of Function#Generalization]]

## Explanation

>[!important] Proposition
>A function $F : \mathbb{R} \rightarrow \mathbb{R}$ is of **bounded variation** *if and only if* it is the **difference** of *two* **bounded monotone** functions.

## Connection to Riemann-Stieltjes Integration

- [[Riemann–Stieltjes Integration]]


## Banach Space

>[!important] 
>$BV(\Omega, \mathbb{R})$ is a *Banach space* with respect to the norm
>$$
>\lVert f \rVert_{BV(\Omega)} := \lVert f \rVert_{L^1} + V(f, \Omega) 
>$$

- [[Banach Space]]

## Sobolev Space

>[!important] 
>The **Sobolev space** $W^{1,1}(\Omega)$ is a subspace of $BV(\Omega, \mathbb{R})$.
>
>For each $f\in W^{1,1}(\Omega)$, there exists a **measure** $$d\mu = Df\;dx$$ such that 
>$$
>\int f\;\text{div}(\phi)dx = - \int \phi\,d\mu = - \int \phi\,Df\,dx
>$$
>where $Df$ is the **weak derivative** of $f$.

- [[Sobolev Space]]
- [[Kantorovitch Representation Theorem for Dual of L-infinity]]

## Dual Space of $C_{c}(\Omega)$ space, Radon Measure and Weak Derivatives

>[!info]
>Note that
>$$
>\begin{align*}
> \left\lvert \int_{\Omega}\,f\; \text{div}(\phi)\; dx  \right\rvert \le V(f, \Omega) \;\lVert \phi \rVert_{L^{\infty}(\Omega)}
>\end{align*}
>$$
>
>Thus the map
>$$
>\phi \to \int_{\Omega}\,f\; \text{div}(\phi)\; dx
>$$
>is a **continuous linear functional** on $\mathcal{C}_{c}(\Omega, \mathbb{R}^n).$
>
>By [[Hahn-Banach Theorem Extension Form]], we can extend this linear functional to $\mathcal{C}_{0}(\Omega, \mathbb{R}^{n})$.
>
>By [[Riesz-Markov Representation Theorem]], we can find a Radon measure corresponding to it.
>$$d\mu = Df\;dx$$ 
>where $Df$ is the **weak derivative** of $f$.

- [[Space of Bounded Signed Measures]]
- [[Riesz-Markov Representation Theorem]]
- [[Continuous Functions with Compact Support]]
- [[Continuous Functions that Vanish At Infinity]]

>[!important] Theorem
>If $f\in BV(\Omega, \mathbb{R})$ with **bounded total variation**, then there exists a **finite vector Radon measure** $Df$ on $\mathscr{F}$ such that the following **equality** holds
>$$
>\begin{align*}
> \int_{\Omega}\,f\,\text{div}(\phi)\,dx = - \int_{\Omega}\,\left\langle \phi ,  Df\right\rangle
>\end{align*}
>$$
>for all $\phi \in \mathcal{C}_{c}(\Omega, \mathbb{R}^n).$
>
>In other word, $$f \mapsto \int_{\Omega}\,f\,\text{div}(\phi)\,dx $$ defines a **linear functional** on $\mathcal{C}_{c}(\Omega, \mathbb{R}^n)$ and $Df$ is the **weak derivative** of $f$.

- [[Space of Bounded Signed Measures]]
- [[Radon Measure]]
- [[Weak Derivative via Tempered Distribution]]



-----------
##  Recommended Notes and References

- [[Jordan Decomposition Theorem and total variation measure]]
- [[Total Variation of Function]]

- [[Banach Space]]

- [[Introduction to Measure Theory by Tao]]

- Wikipedia [Bounded_variation](https://en.wikipedia.org/wiki/Bounded_variation)