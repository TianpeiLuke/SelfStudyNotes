---
tags:
  - concept
  - math/information_geometry
keywords:
  - mixture_connection
  - m_connection
  - statistical_manifold
  - mixture_representation_measure
topics:
  - information_geometry
name: Mixture Embedding and Representation of Tangent Space of Statistical Manifold
date of note: 2024-11-03
---

## Concept Definition

>[!important]
>**Name**: Mixture Embedding and Representation of Tangent Space of Statistical Manifold

![[Statistical Manifold as Parametric Family#^646891]]

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a *$\sigma$-finite measure* space.  
>
>Consider $\mathcal{P}(\mathcal{X})$ as the *space of all probability density functions* on $\mathcal{X}$ with respect to base measure $\mu$
>$$
> \begin{align*}
> \mathcal{P}(\mathcal{X}) := \left\{ p := \frac{dP}{d\mu} : \mathcal{X} \rightarrow \mathbb{R}\;|\; \forall P \ll \mu   \right\} 
> \end{align*}
>$$  
>- Assume that the *support* of $p$ *covers* $\mathcal{X}$, i.e. $$p(x) >0, \quad \forall x \in \mathcal{X}.$$
>- The *statistical manifold* $\mathcal{S}$ parameterized by $\theta\in \Theta$ is a subset of $\mathcal{P}$. $$\mathcal{S} \subset \mathcal{P}(\mathcal{X})$$
>  
>Note that 
>- the space of p.d.f. on $\mu$ is a subspace in *$\mu$-measurable function space* on $\mathcal{X}$, $\mathbb{R}^{\mathcal{X}}$
>- More precisely, $\mathcal{P}(\mathcal{X})$ is an *affine subspace* of $L^1$ $$\mathcal{P}(\mathcal{X})  \subset \left\{ f\in L^1(\mathcal{X},\mu) \;:\; \int_{\mathcal{X}}f d\mu = 1 \right\} $$
>- Since $\mathcal{P}(\mathcal{X}) \subset \mathbb{R}^{\mathcal{X}}$, its tangent space is the subspace of tangent space of $\mathbb{R}^{\mathcal{X}}$. 
>
>Define an *injective map* $\sigma: \mathcal{P}(\mathcal{X}) \to \mathbb{R}^{\mathcal{X}}$ where  $$\sigma: p \mapsto \sqrt{p}$$
>- The image of $\sigma$ is $$\sigma(\mathcal{P}) := \left\{ \sqrt{p}:\; p\in \mathcal{P}(\mathcal{X}) \right\} $$
>- Now consider restriction of $\sigma$ on the *statistical manifold* $\mathcal{S}$ and assumes that $$\nabla  \sqrt{p_{\theta}} := \frac{1}{2} \left[ \partial_{1} p_{\theta} \,{,}\ldots{,}\, \partial_{n} p_{\theta} \right] $$ are *linearly indenpendent.*
>
>The restriction of $\sigma$ from $\mathcal{S}$ onto its image $$\sigma: \mathcal{S} \to \left\{ \sqrt{p_{\theta}}\in \mathbb{R}^{\mathcal{X}}:\; p_{\theta}\in \mathcal{S} \right\}$$ is a *smooth embedding*, called **mixture embedding** or **natural embedding** of *statistical manifold* $\mathcal{S}$ in $\mathbb{R}^{\mathcal{X}}$
>
> Consider the *differential* of *exponential embedding* as $$d\sigma: T_{p}\mathcal{S} \to T_{\sigma(p)}\mathbb{R}^{\mathcal{X}} \simeq \mathbb{R}^{\mathcal{X}}$$ 
>- We call $X_{p}^{(m)} := d\sigma(X_{p})$ as the **mixture representation** or **m-representation** of a *tangent vector* $X_{p} \in T_{p}\mathcal{S}$, i.e. $$d\sigma: X_{p} \in T_{p}\mathcal{S} \to X_{p}^{(m)}$$ 
>- Denote the **space** of $X_{p}^{(m)}$ for all $p\in \mathcal{S}$ as $$T_{p}^{(m)}\mathcal{S} := \left\{ X^{(m)} = d\sigma(X_{p}) \;:\; X_{p} \in T_{p}\mathcal{S} \right\} $$
>	- The **basis vector** in $T_{p}^{(m)}\mathcal{S}$ is given by the *gradient of p.d.f.* $$\frac{ \partial  }{ \partial \theta^{i} } p_{\theta} := \partial_{i}\,p_{\theta} $$ i.e. $$X_{p}^{(m)}  = X^{i}\,\partial_{i}\,p_{\theta}$$ under Einstein summation convention.
>	- We can show that the **tangent space** of $\mathcal{S}$ under **mixture representation** $T_{p}^{(m)}\mathcal{S}$ is identified with a *linear subspace* $$T_{p}^{(m)}\mathcal{S} = \left\{ f \in L^1(\mathcal{X}, \mu)\;:\; \int_{\mathcal{X}}f d\mu = 0 \right\} $$
>	  
>Finally, we can use *mixture embedding* to embed $T_{p}\mathcal{S}$ into a Hilbert space $$T_{p}^{(m)}\mathcal{S}  \xhookrightarrow{} L^2(\mathcal{X}, \mu)$$
>- For any $X_{p}$ and $Y_{p}$ in $T_{p}\mathcal{S}$, the *inner product* of *tangent vector* is identified as the **cross-correlation** between their **exponential representations**, i.e. $$\left\langle  X_{p}\,,\,  Y_{p}  \right\rangle_{g} := 4 \left\langle  X_{p}^{(m)}\,,\,  Y_{p}^{(m)}  \right\rangle_{L^{2}(\mathcal{X}, \mu)}$$
>- In other word, the **Fisher metric** is represented as $$g_{i,j} := \left\langle  \partial_{i}|_{p}\,,\,\partial_{j}|_{p}  \right\rangle = 4\int_{\mathcal{X}} (\partial_{i}\sqrt{ p_{\theta} })\; (\partial_{j}\sqrt{ p_{\theta} })\;d\mu$$

- [[Statistical Manifold as Parametric Family]]
- [[Hilbert Space]]
- [[Affine Space]]
- [[Linear Subspace]]
- [[Smooth Embedding]]
- [[Likelihood Function]]
- [[Lp Space]]

### Mixture Connection and Parallel Transport

>[!important] Proposition
>Let $$P_{p,q}^{(m)}: T_{p}\mathcal{S} \to T_{q}\mathcal{S}$$ be the **parallel transport** along the smooth curve $\gamma$ on $\mathcal{S}$ with $$\gamma(0) = p, \; \gamma(t) = q$$ induced by the **mixture connection** $\nabla^{(m)}$.
>
>Then the **mixture representation** of vector field *parallel transported* by $P_{p,q}^{(e)}$ is given by  
>$$
>P_{p,q}^{(m)}(X_{p}) = Y_{q} \quad \iff \quad Y_{q}^{(m)} = X_{p}^{(m)}
>$$
>- In other word, **mixture connection** is just the *natural connection* induced from the **affine structure** of $$\left\{ f\in L^1(\mathcal{X},\mu) \;:\; \int_{\mathcal{X}}f d\mu = 1 \right\} $$


- [[Parallel Transport Algebraic Definitions]]
- [[Parallel Transport of Tensor Field along Curve]]
- [[Exponential Connection and Mixture Connection on Statistical Manifold]]
- [[Affine Space]]


## Explanation





-----------
##  Recommended Notes and References


- [[Exponential Embedding and Representation of Tangent Space of Statistical Manifold]]
- [[Exponential Connection and Mixture Connection on Statistical Manifold]]
- [[Smooth Embedding]]
- [[Mixture Family of Distributions]]

- [[Methods of Information Geometry by Amari]] pp 40 - 41