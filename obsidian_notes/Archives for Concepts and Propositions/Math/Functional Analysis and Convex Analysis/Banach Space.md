---
tags:
  - concept
  - math/functional_analysis
keywords:
  - banach_space
topics:
  - functional_analysis
name: Banach space
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Banach Space


>[!important] Definition
>A **complete** **normed** *linear space* is called a **Banach space**.


## Explanation




## Example

>[!example]
>A **finite-dimensional normed vector space** with **any norm** $(V, \lVert \cdot \rVert)$ is a  *Banach space*. 

- [[Norm and Normed Space]]

>[!example]
>All **Hilbert spaces** are Banach space with norm $$\lVert f \rVert_{\mathcal{H}} := \left(\left\langle  f\,,\,f    \right\rangle_{\mathcal{H}}\right)^{1 / 2}.$$

- [[Hilbert Space]]

>[!example]
>For $0 <p < \infty$, the space of **$p$-summable sequence** $$\ell^{p} := \left\{ (a_{0}, a_{1} \,{,}\ldots{,}\,): a_{i} \in \mathbb{C},\; \sum_{n=0}^{\infty}|a_{n}|^{p} < \infty \right\} $$
>is a *Banach space* with respect to norm $$\lVert a \rVert_{\ell^p} := \lVert a \rVert_{p} := \left(\sum_{n=0}^{\infty}|a_{n}|^{p}\right)^{1 / p}.$$

- [[lp Sequence Space]]
- Wikipedia [Sequence_space](https://en.wikipedia.org/wiki/Sequence_space)

>[!example]
>For $p = \infty$, the space of all **bounded sequence** $$\ell^{\infty} := \left\{ (a_{0}, a_{1} \,{,}\ldots{,}\,): a_{i} \in \mathbb{C},\; \sup_{n}|a_{n}| < \infty \right\} $$
>is a *Banach space* with respect to norm $$\lVert a \rVert_{\infty} := \sup_{n}|a_{n}|.$$

- [[lp Sequence Space]]

>[!example]
>Let $\mathbb{C}^{\omega}$ be the **$\omega$-tuple** of $\mathbb{C}$.
>
>- The space of **convergent sequences** $c \subset \mathbb{C}^{\omega}$ is defined as $$c := \left\{ (x_{0}, x_{1} \,{,}\ldots{,}\,): \lim_{ n \to \infty } x_{n}\text{ exists}  \right\}$$
>- The space of **null sequences** (or **vanishing sequences**) $c_{0} \subset \mathbb{C}^{\omega}$ is defined as $$c_{0} := \left\{ (x_{0}, x_{1} \,{,}\ldots{,}\,): \lim_{ n \to \infty } x_{n} = 0  \right\}$$
>
>We have 
>$$
>c_{0} \subset c \subset \ell^{\infty}
>$$
>and $c_{0}$ is a **closed subspace** of $c$ and $c$ is a **closed subspace** of $\ell^{\infty}$
>
>Both $c_{0}$ and $c$ are **Banach space** under norm $$\lVert x \rVert_{\infty} := \sup_{n}|x_{n}|.$$

- [[Convergent Sequence Space]]


>[!example] 
>For $1 \le p < \infty$,  **$L^p(\mathcal{X}, \mu)$ space** is a *Banach space* with respect to norm $$\lVert f \rVert_{L^p} := \left(\int_{\mathcal{X}}\lvert f \rvert^p\,d\mu\right)^{1 / p}.$$

- [[Lp Space]]
- [[Riesz-Fisher Theorem and Completeness of Lp Space]]


>[!example]
>For $p=\infty$, $$L^{\infty}(X, \mu) := \left\{ f: X \to \mathbb{C} \text{ $\mu$-measurable}: \text{ess }\sup_{X}|f| < \infty \right\} $$ is the space of **essentially bounded functions** 

- [[L-infinite Space]]
- [[Essential Supremum and Essential Infimum]]



>[!example]
>The space of *all bounded linear operator* from one normed space $X$ to another normed space $Y$, $\mathcal{L}(X, Y)$, is a Banach space under operator norm.

- [[Space of Bounded Linear Operators]]


>[!example]
>The space of **functions with bounded variations** on open subset $\Omega \subset \mathbb{R}^{n}$  is defined as
>$$
> BV(\Omega, \mathbb{R}) := \left\{f: \in L^1(\Omega):  V(f, \Omega)  < \infty \right\} 
>$$
>with the **norm** defined as
>$$
>\lVert f \rVert_{BV(\Omega)} := \lVert f \rVert_{L^1} + V(f, \Omega) 
>$$
>
>Here, $V(f, \Omega)$ is  **total variation** of $f$ in $\Omega$ is defined as 
>$$
>\begin{align*}
>  V(f, \Omega)   := \sup\left\{ \int_{\Omega}f \;\text{div}(\phi)\, dx: \;\; \phi \in \mathcal{C}_{c}(\Omega, \mathbb{R}^n), \; \lVert \phi \rVert_{L^{\infty}(\Omega)} \le 1  \right\} 
\end{align*}
>$$
>where $\text{div}$ is the **divergence operator**, $\mathcal{C}_{c}(\Omega, \mathbb{R}^d)$ is the continuous function from $X \to \mathbb{R}^d$ with *compact support*, $\lVert  \rVert_{\infty}$ is the **essential supremum norm**.

- [[Space of Functions with Bounded Variation]]
- [[Total Variation of Function]]



>[!example] 
>Let $X$ be  a **compact Hausdorff** space. Denote $\mathcal{C}(X, \mathbb{C})$ as the space of *all continuous* (complex-valued) functions on $X$, endowed with the norm
>$$
>\lVert f \rVert_{\infty} := \sup_{x \in X}\lvert f(x) \rvert.  
>$$ 
>
>Let $\mathcal{C}(X, \mathbb{R})$ be the space of all real-valued continuous functions on $X$.
>
>Then $\mathcal{C}(X, \mathbb{C})$ is a complex **Banach space** and $\mathcal{C}(X, \mathbb{R})$ is a real **Banach space**. Also $$\mathcal{C}(X, \mathbb{C}) \subset L^{\infty}(X, \mu)$$ is a **closed subspace**.

- [[Compact Hausdorff Space]]
- [[Uniform Topology on Metric Spaces]]
- [[Space of all Continuous Functions]]
- [[Summary of Spaces of Continuous Functions]]





>[!example] 
>**The Orlicz space** $L_{\psi} = L_{\psi}(X, \mathscr{F}, \mu)$ consists of all measurable functions $f$ on the measure space $(X, \mathscr{F}, \mu)$ with **finite Orlicz norm**, i.e.
>$$
> \begin{align*}
> L_{\psi} := \set{f \in \mathscr{F}/\mathcal{B}_{\mathbb{R}}: \lVert f \rVert_{\psi}  < \infty}.
> \end{align*}
>$$ 
>where **the Orlicz norm** is defined as
>$$
> \begin{align*}
> \lVert f \rVert_{\psi} := \inf\left\{t>0: \int_{X} \psi \left( \frac{\lvert f \rvert }{t}\right) d\mu  \le 1 \right\}.
> \end{align*}
>$$ 
>and $\psi$ is **convex**, **increasing**, and satisfies:
>$$
> \begin{align*}
> \psi(0) = 0, \quad \psi(x) \to \infty, \;\text{ as }x\to \infty.
> \end{align*}
>$$ 
>
>**The Orlicz space** is a *Banach space*

- [[Orlicz Space]]


>[!example]
>Let $1 \le p < +\infty$,  the **Sobolev space** $W^{k, p}(\Omega)$ is the space of all functions $f\in L^p(\Omega)$ such that 
>- $f$ and 
>- all of its *weak derivatives* $D^{\alpha}f$ for all $|\alpha| \le k$
>
>has *finite $L^p$ norm*. That is,
>$$
>W^{k, p}(\Omega) = \left\{ f\in L^p(\Omega): \lVert D^{\alpha}\,f \rVert_{L^p(\Omega)} < \infty, \;\; \forall |\alpha| \le k  \right\}. 
>$$
>
>The **Sobolev space** is a *Banach space* with a natural **norm**
>$$
>\begin{align*}
>\lVert f \rVert_{W^{k, p}} := \left( \sum_{|\alpha| \le k} \left\lVert D^{\alpha}f \right\rVert_{L^p(\Omega)}^{p}    \right)^{1 / p} = \left( \sum_{|\alpha| \le k} \int_{\Omega}  \left\lvert D^{\alpha}f(x) \right\rvert^{p}  dx   \right)^{1 / p} < \infty.
>\end{align*}
>$$

- [[Sobolev Space]]


>[!example]
>Given measurable space $(\mathcal{X}, \mathscr{F})$, the space of all **regular signed Borel measures (Radon measures)** with **bounded variation** on $\mathcal{X}$, $$\mathcal{M}(\mathcal{X}) := \left\{ \mu: \mathscr{F} \to \mathbb{R}: \mu \text{ is a Radon measure }, |\mu|(\mathcal{X}) < \infty  \right\} $$ is a *Banach space* with bounded **total variation norm** $$\lVert \mu \rVert := |\mu|(\mathcal{X})$$ where $$\lvert \mu \rvert = \mu_{+} + \mu_{-} $$ where $\mu_{+}$ and $\mu_{-}$ are two positive measures such that $\mu = \mu_{+} - \mu_{-}$ and $\mu_{+} \perp \mu_{-}.$

- [[Radon Measure]]
- [[Jordan Decomposition Theorem and total variation measure]]
- [[Measure Space and Countably Additive Measure]]

>[!example]
>Let $(\mathcal{X}, \mathscr{F})$ be a *measurable space*.
>
>- The space of all **bounded finitely additive signed measures** $\nu$ is called the **BA space**, and is denoted as  $\mathcal{BA}(\mathcal{X}, \mathscr{F})$, i.e.$$\mathcal{BA}(\mathcal{X}, \mathscr{F}) := \left\{ \nu \in {\mathbb{R}}^{\mathscr{F}}: \nu \text{ finitely additive and } \lvert \nu \rvert (\mathcal{X}) < \infty\right\}.$$ 
>
>- The space of all **bounded countably additive signed measures** $\mu$ is called the **CA space** and is denoted as  $\mathcal{CA}(\mathcal{X}, \mathscr{F})$, i.e. $$\mathcal{CA}(\mathcal{X}, \mathscr{F}) := \left\{ \mu \in {\mathbb{R}}^{\mathscr{F}}: \mu \text{ countably additive and } \lvert \mu \rvert (\mathcal{X}) < \infty \right\}$$ 
>
>- The space of all **bounded Radon (regular Borel) signed measures** $\mu$ is called the **RCA space** and is denoted as  $\mathcal{RCA}(\mathcal{X}, \mathscr{F})$, i.e. $$\mathcal{RCA}(\mathcal{X}, \mathscr{F}) := \left\{ \mu \in {\mathbb{R}}^{\mathscr{F}}: \mu \text{ is Radon measure and } \lvert \mu \rvert (\mathcal{X}) < \infty \right\}.$$ 
>
>With respect to the **total variation norm** $$\lVert \nu \rVert := |\nu|(\mathcal{X}),$$ 
>- The BA space $\mathcal{BA}(\mathcal{X}, \mathscr{F})$ is a **Banach space** with respect to the **total variation norm** $$\lVert \nu \rVert := |\nu|(\mathcal{X}).$$
>- The CA space $\mathcal{BA}(\mathcal{X}, \mathscr{F})$ is a **Banach space** and it is a **closed subspace** of BA space
>- The RCA space $\mathcal{RCA}(\mathcal{X}, \mathscr{F}) \equiv \mathcal{M}(\mathcal{X})$ is a **Banach space** and it is a **closed subspace** of CA space
>
>
>We have $$\mathcal{RBA}(\mathcal{X}) \subset \mathcal{CA}(\mathcal{X}) \subset \mathcal{BA}(\mathcal{X})$$

- [[Space of Bounded Signed Measures]]






-----------
##  Recommended Notes and References

- [[Norm and Normed Space]]
- [[Complete Metric Space]]
- [[Metric Space]]
- [[Hilbert Space]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)