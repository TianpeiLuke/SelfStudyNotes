---
tags:
  - concept
  - math/information_geometry
  - math/differential_geometry
keywords:
  - statistical_manifold
topics:
  - information_geometry
  - differential_geometry
name: Statistical Manifold of Parametric Family
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Statistical Manifold of Parametric Family

![[Topological Manifold#^90f99f]]

- [[Topological Manifold]]

![[Coordinate Chart#^1c8d37]]

- [[Coordinate Chart]]
- [[Smooth Chart and Smooth Coordinate Map]]
- [[Smooth Atlas]]
- [[Transition Map and Smoothly Compatible]]

![[Smooth Manifold#^dcce28]]

- [[Smooth Manifold]]

![[Parametric Models#^408b6c]]


>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a *$\sigma$-finite measure* space.  
>
>Consider $\mathcal{P}(\mathcal{X})$ as the *space of all probability density functions* on $\mathcal{X}$ with respect to base measure $\mu$
>$$
> \begin{align*}
> \mathcal{P}(\mathcal{X}) := \left\{ p := \frac{dP}{d\mu} : \mathcal{X} \rightarrow \mathbb{R}\;|\; \forall P \ll \mu   \right\} 
> \end{align*}
>$$  
>where 
>- the p.d.f. $$p = \frac{dP}{d\mu} \in \mathscr{F} / \mathcal{B}(\mathbb{R})$$ is  the *Radon-Nikodym derivative* of a probability measure $P$ with respect to $\mu$, which is *random variable*   
>- and $P \ll \mu$ is any *probability measure* that is dominated by $\mu$.
>- Assume that the *support* of $p$ *covers* $\mathcal{X}$, i.e. $$p(x) >0, \quad \forall x \in \mathcal{X}.$$
>  
>  
>A subset of $\mathcal{P}(\mathcal{X})$ $$\mathcal{S} \subset\mathcal{P}(\mathcal{X})$$ is called a **$n$-dimensional statistical manifold** if $\mathcal{S}$ is equipped with a *maximum smooth atlas* $\mathcal{A}$, i.e.
>- there exists a *collection* $\mathcal{A}$ of *smooth coordinate charts* $(U_{p},\, \varphi_{p})$ such that
>	- for each $p$, $U_{p}$ is *open*, and $\mathcal{S} \subset \bigcup_{p\in \mathcal{S}}U_{p}$
>	- $\varphi_{p}: U_{p} \to \hat{U}_{p} \subset \mathbb{R}^{n}$ is a smooth map to some open subset $\hat{U}_{p}$ in $\mathbb{R}^{n}$
>	- And any two charts $(U, \varphi)$ and $(V, \psi)$ in $\mathcal{A}$ must satisfy the following condition:
>		- either $U \cap V = \emptyset$ 
>		- or the *transition map* $\psi \circ \varphi^{-1}: \varphi(U \cap V ) \rightarrow \psi(U \cap V)$ is a *diffeomorphism*. 
>- In other word, for each $p \in \mathcal{S}$, there exists a *parameterization* $\theta :=\varphi(p)$, that is, $p$ is indexed by $\theta$ as  $$p\in \mathcal{S} \implies p := p_{\theta} := p(x; \theta)$$
>
>A **$n$-dimensional statistical manifold** is a **parameteric family** of distributions, or a **parametric model**. $$\mathcal{S} := \left\{ p_{\theta}: \theta \in \Theta \subseteq \mathbb{R}^{n} \right\} $$
>

^646891

- [[Measure Space and Countably Additive Measure]]
- [[Probability Space]]
- [[Probability Density Function of Random Variable]]
- [[Random Element and Random Variable]]
- [[Parametric Models]]



## Explanation

### Space of Measures with Bounded Total Variations

![[Space of Bounded Signed Measures#^d5ec0e]]

![[Space of Bounded Signed Measures#^73c68c]]

- [[Space of Bounded Signed Measures]]

### Wasserstein Space

![[Wasserstein Space#^998943]]

- [[Wasserstein Space]]






-----------
##  Recommended Notes and References

- [[Fisher Information]]

- [[Riemannian Metric and Riemannian Manifold]]
- [[Inner Product Space]]

- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Concepts related to Tangent Space and Tangent Bundle]]

- [[Embedded Submanifold]]
- [[Radon-Nikodym Derivative]]
- [[Absolute Continuity for Measures]]

- [[Diffeomorphism]]

- [[Lp Space]]
- [[Hilbert Space]]



- [[Methods of Information Geometry by Amari]] pp 25 - 27
- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]
