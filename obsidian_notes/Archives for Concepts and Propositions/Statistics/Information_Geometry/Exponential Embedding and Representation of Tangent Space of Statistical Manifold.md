---
tags:
  - concept
  - math/information_geometry
keywords:
  - exponential_connection
  - e_connection
  - statistical_manifold
  - exponential_representation_measure
topics:
  - information_geometry
name: Exponential Embedding and  Representation of Tangent Space of Statistical Manifold
date of note: 2024-11-03
---

## Concept Definition

>[!important]
>**Name**: Exponential Embedding and Representation of Tangent Space of Statistical Manifold

![[Statistical Manifold as Parametric Family#^646891]]

![[Smooth Immersion#^fcddc4]]

![[Smooth Embedding#^2f0f85]]

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
>Define an *injective map* $\sigma: \mathcal{P}(\mathcal{X}) \to \mathbb{R}^{\mathcal{X}}$ where  $$\sigma: p \mapsto \log(p)$$
>- The image of $\sigma$ is $$\sigma(\mathcal{P}) := \left\{ \log p:\; p\in \mathcal{P}(\mathcal{X}) \right\} $$
>- Now consider restriction of $\sigma$ on the *statistical manifold* $\mathcal{S}$ and assumes that $$\nabla \log p_{\theta} := \left[ \partial_{1} \log p_{\theta} \,{,}\ldots{,}\, \partial_{n} \log p_{\theta} \right] $$ are *linearly indenpendent.*
>
>The restriction of $\sigma$ from $\mathcal{S}$ onto its image $$\sigma: \mathcal{S} \to \left\{ \log p_{\theta}\in \mathbb{R}^{\mathcal{X}}:\; p_{\theta}\in \mathcal{S} \right\}$$ is a *smooth embedding*, called **exponential embedding** or **logarithmic embedding** of *statistical manifold* $\mathcal{S}$ in $\mathbb{R}^{\mathcal{X}}$
>
> Consider the *differential* of *exponential embedding* as $$d\sigma: T_{p}\mathcal{S} \to T_{\sigma(p)}\mathbb{R}^{\mathcal{X}} \simeq \mathbb{R}^{\mathcal{X}}$$ 
>- We call $X_{p}^{(e)} := d\sigma(X_{p})$ as the **exponential representation** or **e-representation** or **logarithmic representation** of a *tangent vector* $X_{p} \in T_{p}\mathcal{S}$, i.e. $$d\sigma: X_{p} \in T_{p}\mathcal{S} \to X_{p}^{(e)}$$ 
>- Denote the **space** of $X_{p}^{(e)}$ for all $p\in \mathcal{S}$ as $$T_{p}^{(e)}\mathcal{S} := \left\{ X^{(e)} = d\sigma(X_{p}) \;:\; X_{p} \in T_{p}\mathcal{S} \right\} $$
>	- The **basis vector** in $T_{p}^{(e)}\mathcal{S}$ is given by the *log-likelihood score function* $$\frac{ \partial  }{ \partial \theta^{i} }\log p_{\theta} := \partial_{i}\,\ell_{\theta}$$ i.e. $$X_{p}^{(e)}  = X^{i}\partial_{i}\ell_{\theta}$$ under Einstein summation convention.
>	- We can show that the **tangent space** of $\mathcal{S}$ under **exponential representation** $T_{p}^{(e)}\mathcal{S}$ is identified with $$T_{p}^{(e)}\mathcal{S} = \left\{ f \in L^1(\mathcal{X}, p)\;:\; \mathbb{E}_{ p }\left[  f \right] = 0 \right\} $$
>	  
>Finally, we can use *exponential embedding* to embed $T_{p}\mathcal{S}$ into a Hilbert space $$T_{p}^{(e)}\mathcal{S}  \xhookrightarrow{} L^2(\mathcal{X}, p)$$
>- For any $X_{p}$ and $Y_{p}$ in $T_{p}\mathcal{S}$, the *inner product* of *tangent vector* is identified as the **cross-correlation** between their **exponential representations**, i.e. $$\left\langle  X_{p}\,,\,  Y_{p}  \right\rangle_{g} := \mathbb{E}_{ p }\left[  X_{p}^{(e)}\,Y_{p}^{(e)} \right] :=  \left\langle  X_{p}^{(e)}\,,\,  Y_{p}^{(e)}  \right\rangle_{L^{2}(\mathcal{X}, p)}$$
>- In other word, the **Fisher metric** is represented as $$g_{i,j} := \left\langle  \partial_{i}|_{p}\,,\,\partial_{j}|_{p}  \right\rangle = \mathbb{E}_{ p }\left[  \partial_{i}\ell_{\theta}\; \partial_{j}\ell_{\theta} \right]$$



- [[Affine Space]]
- [[Statistical Manifold as Parametric Family]]
- [[Smooth Embedding]]
- [[Differential of a Smooth Map at Point]]
- [[Likelihood Function]]
- [[Hilbert Space]]
- [[Lp Space]]
- [[Fisher Metric or Information Metric of Statistical Manifold]]

### Exponential Connection and Parallel Transport

>[!important] Proposition
>Let $$P_{p,q}^{(e)}: T_{p}\mathcal{S} \to T_{q}\mathcal{S}$$ be the **parallel transport** along the smooth curve $\gamma$ on $\mathcal{S}$ with $$\gamma(0) = p, \; \gamma(t) = q$$ induced by the **exponential connection** $\nabla^{(e)}$.
>
>Then the **exponential representation** of vector field *parallel transported* by $P_{p,q}^{(e)}$ is given by  
>$$
>P_{p,q}^{(e)}(X_{p}) = Y_{q} \quad \iff \quad Y_{q}^{(e)} = X_{p}^{(e)} - \mathbb{E}_{q}\left[  X_{p}^{(e)} \right]
>$$
>- The shift $$f  \mapsto f - \mathbb{E}_{ q }\left[  f \right]$$ establishes a **linear isomorphism** from $T_{p}^{(e)}\mathcal{S}$ to $T_{q}^{(e)}\mathcal{S}$

- [[Parallel Transport Algebraic Definitions]]
- [[Parallel Transport of Tensor Field along Curve]]
- [[Exponential Connection and Mixture Connection on Statistical Manifold]]
- [[Linear Isomorphism]]


## Explanation

>[!info]
>The restriction of $\sigma$ from $\mathcal{S}$ onto its image $$\sigma: \mathcal{S} \to \left\{ \log p_{\theta}\in \mathbb{R}^{\mathcal{X}}:\; p_{\theta}\in \mathcal{S} \right\}$$ is a *smooth embedding*  of *statistical manifold* $\mathcal{S}$ in $\mathbb{R}^{\mathcal{X}}$
>
>To show that, we see that 
>- $\log(\cdot)$ is bijective, and smooth with smooth inverse for all $p >0$, and all basis scores are independent.
>- Also assumes that $$\nabla \log p_{\theta} := \left[ \partial_{1} \log p_{\theta} \,{,}\ldots{,}\, \partial_{n} \log p_{\theta} \right] $$ are *linearly indenpendent.*
>- Thus $$d\sigma_{p}: \partial_{i}|_{p} \to \partial_{i}\log p$$ has full rank

- [[Smooth Embedding]]

>[!info]
>To show that $$T_{p}^{(e)}\mathcal{S} = \left\{ f \in L^1(\mathcal{X}, p)\;:\; \mathbb{E}_{ p }\left[  f \right] = 0 \right\} $$, 
>We note that $$\sigma(p) = \log(p)$$ and $$\int p d\mu = 1,$$ 
>we have for $i=1\,{,}\ldots{,}\,n$ 
>$$
>\begin{align*} 
>\mathbb{E}_{ p }\left[  \partial_{i}\ell_{\theta} \right] 
>&=\int \partial_{i} \log(p_{\theta}) p_{\theta} \,d\mu \\[5pt] 
>&= \int \frac{1}{p_{\theta}} (\partial_{i} \log(p_{\theta})) p_{\theta} d\mu \\[5pt] 
>&= \int \partial_{i} \log(p_{\theta}) d\mu \\[5pt] 
>&= \partial_{i}  \int p d\mu  = \partial_{i}  1 = 0
>\end{align*}
>$$ 
>
>Since $$X_{p}^{(e)}  = X^{i}\partial_{i}\ell_{\theta}$$ under Einstein summation convention, we have
>$$
>\mathbb{E}_{ p }\left[ X_{p}^{(e)}\right] = \mathbb{E}_{ p }\left[  X^{i}\partial_{i}\ell_{\theta} \right] = X^{i}\mathbb{E}_{ p }\left[  \partial_{i}\ell_{\theta} \right] = 0
>$$





-----------
##  Recommended Notes and References


- [[Mixture Embedding and Representation of Tangent Space of Statistical Manifold]]


- [[Smooth Immersion]]
- [[Injective Function]]
- [[Bijective Function and Inverse Function]]
- [[Einstein Summation Convention]]

- [[Methods of Information Geometry by Amari]] pp 40 - 41