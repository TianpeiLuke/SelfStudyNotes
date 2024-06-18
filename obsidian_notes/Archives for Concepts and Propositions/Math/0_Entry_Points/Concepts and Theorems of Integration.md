---
tags:
  - entry_point
  - concept
  - math/real_analysis
  - math/differential_geometry
  - math/functional_analysis
  - math/stochastic_process
keywords: 
topics:
  - real_analysis
  - functional_analysis
  - differential_geometry
  - stochastic_process
name: Concepts and Theorems of Integration
date of note: 2024-06-06
---

## List of Concepts

### Riemann Integration on Closed Interval in Real Line

>[!info]
>$$
>\sup \left\{ \sum_{k=1}^{n}m_{k}\Delta_{k}: P(\Delta) \in \mathcal{P} \right\} \le \int_{a}^{b}f(x) dx \le \inf \left\{\sum_{k=1}^{n}M_{k}\Delta_{k} : P(\Delta)  \in \mathcal{P} \right\}
>$$

- [[Darboux Lower Sum and Darboux Upper Sum]]
- [[Riemann Integration]]
- [[Criterion of Riemann-Stieltjes Integrability]]

### Riemann-Stieltjes Integration with respect to Functions with Bounded Variation on Closed Interval in Real Line

>[!info]
>$$
>\sup \left\{ \sum_{k=1}^{n}m_{k}\Delta G_{k}: P(\Delta) \in \mathcal{P} \right\} \le \int_{a}^{b}f(x)\, dG(x) \le \inf \left\{\sum_{k=1}^{n}M_{k}\Delta G_{k} : P(\Delta)  \in \mathcal{P} \right\}
>$$

- [[Riemann–Stieltjes Integration]]


### Lebesgue Integration with respect to Lebesgue Measure on $\mathbb{R}^d$


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
- [[Integration by Parts]]

- [[Lebesgue Measure]]
- [[Expectation of Random Variable]]

>[!important] The Second Fundamental Theorem of Calculus (Absolutely Continuous)
>
>Let $F: [a, b] \rightarrow \mathbb{R}$ be **absolutely continuous**. 
>
>Then
>$$
> \begin{align*}
> \int_{[a, b]}F'(x) dx = F(b) - F(a).
> \end{align*}
>$$  

- [[Second Fundamental Theorem of Calculus Absolutely Continuous]]
- [[Development of Fundamental Theorem of Calculus by Lebesgue Theory]]

### Integration with respect to Lebesgue-Stieltjes Measure

>[!important] Theorem
>Let $F : \mathbb{R} \to \mathbb{R}$ be a **monotone non-decreasing** function, and define the left and right limits 
>$$F_{-}(x) := \sup_{y < x}\,F (y);\quad F_{+}(x) := \inf_{y > x}F (y),$$ thus one has 
>$$F_{-}(x) \le F (x) \le F_{+}(x)$$ 
>for all $x$. Let $\mathcal{B}[\mathbb{R}]$ be the *Borel $\sigma$-algebra* on $\mathbb{R}$. 
>
>Then there exists a **unique Borel measure**, called the **Lebesgue-Stieltjes measure** $\mu_{F} : \mathcal{B}[\mathbb{R}] \to [0, +\infty]$ such that
>- for all $− \infty < b < a < +\infty,$
>$$
>\begin{align*}
>\mu_{F}([a,b]) &= F_{+}(b) - F_{-}(a)\\
>\mu_{F}([a,b)) &= F_{-}(b) - F_{-}(a)\\
>\mu_{F}((a,b]) &= F_{+}(b) - F_{+}(a)\\
>\mu_{F}((a,b)) &= F_{-}(b) - F_{+}(a)
>\end{align*}
>$$ 
>- and 
>  $$\mu_{F} (\{a\}) = F+(a) − F−(a)$$ 
>  for all $a \in \mathbb{R}.$

>[!important] Thoerem
>Let $F : \mathbb{R} \to \mathbb{R}$ be a **monotone non-decreasing** and **absolutely continuous** function. Let $\mathcal{B}[\mathbb{R}]$ be the *Borel $\sigma$-algebra* on $\mathbb{R}$.
>
>Then 
>- for any $E\in \mathcal{B}[\mathbb{R}]$, the **Lebesgue-Stieltjes measure** of $E$ can be represented in the following form $$\mu_{F}(E) = \int_{E} F'(x)\,dx,$$ where $F'(x)$ is the *first-order derivative* of $F$ and the RHS is with respect to **Lebesgue measure**.
>- For any **unsigned Borel measurable** function $f: \mathbb{R} \to \mathbb{R}$, we have $$\int_{\mathbb{R}} f\,d\mu_{F} = \int_{\mathbb{R}} f\,F'\,dx.$$

>[!important] Definition
>From above proposition, we define the **Lebesgue-Stieltjes Integral** of $f$ *with respect to* $F$ as
>$$
>\int_{\mathbb{R}} f\,dF := \int_{\mathbb{R}} f\,d\mu_{F}
>$$

- [[Lebesgue-Stieltjes Measure]]
- [[Lebesgue-Stieltjes Integration]]

### Itô Stochastic Integration with respect to Brownian Motion

>[!important] Definition
>Let $(X_{t}, t \in [0,T])$ be a *step process* and $(W_{t}, t \in [0,T])$ be *Wiener process*.
>
>Define the **Itô stochastic Integration** of $(X_{t})$ on $[0,T]$ as 
>$$
>\begin{align}
>\int_{0}^{T} X_{t}\;dW := \sum_{i=0}^{n-1}\,X_{i}\left(W_{t_{i+1}} - W_{t_{i}}\right)
>\end{align}
>$$

>[!important] Definition
>Let $(X_{t}, t\in [0,T]) \in \mathbb{L}^2([0,T])$ be *progressive measurable stochastic process* such that 
>$$
>\mathbb{E}_{\mathcal{P}}\left[  \int_{T}X^2_{t}dt \right] < \infty.
>$$
>
>The **Itô stochastic integral** of $(X_{t})$ on domain $[0,T]$ is defined as the limit of a sequence of integral of bounded step processes $(X_{t}^n) \in \mathbb{L}^2([0,T])$
>$$
>\int_{0}^T X_{t}\,dW := \lim_{ n \to \infty } \int_{0}^{T}X_{t}^n\,dW
>$$
>in $L^2(\Omega, \mathcal{P})$ topology.

- [[Brownian Motion Wiener Process]]
- [[Progressively Measurable Stochastic Process]]
- [[Step Process]]
- [[Itô Stochastic Integration of Step Process]]
- [[Itô Stochastic Integration]]
- [[Stochastic Differential]]
- [[Itô Chain Rule and Itô Formula]]
- [[Stochastic Integral of Brownian Motion]]
- [[Stochastic Integral with Hermite Polynomial]]
- [[Itô Product Rule and Stochastic Integration by Parts]]
- [[Stochastic Differential of Product of Brownian Motions]]


### White Noise Integration

- [[Wiener Measure as Random Finitely Additive Measures]]
- [[Integration with respect to Wiener Measure]]
- [[Representation of Gaussian Process via White Noise Integral]]

### Stochastic Differential Equation

- [[Stochastic Differential Equations]]
- [[Langevin Equation]]
- [[Ornstein–Uhlenbeck Process]]

### Integration with respect to Radon Measure as Linear Functional 

>[!important] Theorem
>Let $X$ be a *locally compact Hausdorff (LCH)* space,  $\mathcal{M}(X)$ be the space of **signed Radon measure** on $X$ and $\mathcal{C}_{0}(X)$ be the space of all continuous functions that *vanishes at infinity.* 
>
>For every signed Radon measure $\mu$, define a bounded linear functional on $\mathcal{C}_{0}(X)$, $I_{\mu}: \mathcal{C}_{0}(X) \to \mathbb{R}$ as
> $$
> \begin{align*}
> I_{\mu}(f) &= \int f d\mu. 
> \end{align*}
> $$
>
>Then the map 
>$$
>\mu \rightarrow I_{\mu}
>$$ 
>is an **isometric isomorphism** from $\mathcal{M}(X)$ to $(\mathcal{C}_{0}(X))^{*}$, i.e.
>$$\mathcal{M}(X) \simeq (\mathcal{C}_{0}(X))^{*} $$

- [[Duality of Measure and Functional of Continuous Functions]]
	- [[Borel Measure]]
	- [[Inner Regularity]]
	- [[Outer Regularity]]
	- [[Radon Measure]]
	- [[Summary of Spaces of Continuous Functions]]
	- [[Riesz-Markov Representation Theorem]]


### Integration with respect to Project-Valued Spectral Measure

>[!important] Definition
>For each $\psi \in \mathcal{H}$, the induced *Radon measure* $\mu_{\psi} \in \mathcal{M}_{+}(\sigma(A))$ defined in
>$$
>\left\langle f(A)\psi\,,\,\psi  \right\rangle_{\mathcal{H}}  = \int_{\sigma(A)} f\; d\mu_{\psi},\quad \forall f \in \mathcal{C}(\sigma(A))
>$$
> is called the **spectral measure** *associated with* the vector $\psi \in \mathcal{H}$. 

>[!important] Definition
>We denote this operator via the **integration** with respect to *the projection-valued measure*
>$$
> \begin{align*}
> B &:= \int_{\mathbb{R}}  f(\lambda)\; dP_{S}(\lambda).
> \end{align*}
>$$ 
>It is equivalent to the following *spectral integration* with respect to positive measure $\left\langle  \psi\, , \,P_{S}\psi \right\rangle$
>$$
> \begin{align*}
>  \left\langle \int  f(\lambda)\; dP_{S}(\lambda)\psi \,,\,  \psi\right\rangle &=  \int f(\lambda) \;d \left\langle P_{S}\psi, \psi \right\rangle
>\end{align*} 
>$$
>where $\psi \in \mathcal{H}$ is some vector.

- [[Hilbert Space]]
- [[Self-Adjoint Operator in Hilbert Space]]
- [[Resolvent Set and Spectrum of Linear Operator]]
- [[Eigenvalue Point Residual Spectrum of Linear Operator]]
- [[Spectrum of Self-Adjoint Linear Operator]]
- [[Continuous Functional Calculus]]
- [[Positive Linear Functional]]
- [[Spectral Measure induced by Positive Linear Functional]]
- [[Spectral Theorem in Functional Calculus Form]]
- [[Spectral Projection]]
- [[Projection-Valued Measure]]
- [[Integration with respect to Project-Valued Measure]]
- [[Spectral Theorem in Projection-Valued Measure Form]]



### Integration with respect to Different Forms on Smooth Manifold

- [[Calculus on Manifolds]]

>[!important]
>$$
>\int_{\mathcal{M}} \omega = \int_{\mathbb{R}^d} \sum_{(i_{1} \,{,}\ldots{,}\,i_{d})} \omega_{i_{1} \,{,}\ldots{,}\,i_{d}} \; dx^{i_{1}} \,{\wedge}\ldots{\wedge}\,dx^{i_{d}}
>$$


- [[Orientations of Manifold determined by k-Form]]
- [[Differential k-Form on Manifold]]
- [[Differential k-Form as Infinitesimal Volume]]
- [[Riemannian Volume Form]]
- [[Integration of Differential k-Form]]
- [[Integration on Riemannian Manifold]]


>[!important] Stokes' Theorem
>Let $\omega$ be a **smooth $(n-1)$-form** with **compact support** on an **oriented**, $n$-dimensional manifold with boundary $M$, where $\partial M$ is given the **induced orientation**.
>
>Then
>$$
>\begin{align*}
>\int_{\partial M} \omega = \int_{M} d\omega
\end{align*}
>$$
>where $d\omega$ is the **exterior derivative** of $\omega.$ 

- [[Exterior Derivatives of Differential Form]]
- [[Stokes Theorem]]
- [[Divergence Theorem on Riemannian Manifold]]
- [[Divergence Operator of Vector Field on Riemannian Manifold]]

## Explanation





-----------
##  Recommended Notes and References

