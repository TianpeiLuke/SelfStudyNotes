---
tags:
  - concept
  - math/probability
  - machine_learning_models
  - math/information_geometry
  - math/differential_geometry
keywords:
  - affine_space
  - exponential_family
  - e_connection
topics:
  - information_geometry
  - statistics/estimation
  - probability
name: Exponential Family as Affine Subspace in Statistical Manifold
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Exponential Family as Affine Subspace in Statistical Manifold

![[Exponential Family of Distributions#^b32aa5]]

![[Log-Partition Function of Exponential Family#^8780a9]]

![[Fisher Information for Exponential Family#^713d66]]

- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- [[Fisher Information for Exponential Family]]

![[Exponential Connection and Mixture Connection on Statistical Manifold#^a34e99]]

>[!important] Theorem
>An **exponential family** is **e-fiat** i.e. $$\Gamma_{i,j:k}^{(e)} = 0$$ and its **natural parameters** $$\theta := (\theta^1 \,{,}\ldots{,}\,\theta^{n})$$ form an **e-affine coordinate system**.

- [[Exponential Connection and Mixture Connection on Statistical Manifold]]
- [[Affine Space]]
- [[Coordinate Chart]]
- [[Smooth Atlas]]

### Proof

>[!info] Proof 
>Let $p(x; \theta)$ be a p.d.f. from an *exponential family*
>$$
> p(x; \theta) := \exp\left( \left\langle  \theta,\, T(x)   \right\rangle - A(\theta) \right)
>$$
>
>- The *log-likelihood function* $$\ell(\theta; x) :=  \left\langle  \theta,\, T(x)   \right\rangle - A(\theta) $$ 
>- The *score function*, i.e. the basis of tangent space $T_{p}\mathcal{S}$ is given by $$\begin{align*}\frac{ \partial \ell }{ \partial \theta^{i} } &= T^{i}(x) - \frac{ \partial  }{ \partial \theta^{i} }A(\theta) \\[5pt] &=  T^{i}(x) - \mathbb{E}_{ \theta }\left[  T^{i}(X) \right] \end{align*}$$
>- The *second derivative* is given by the **Fisher metric** $$\frac{ \partial^2 \ell }{ \partial \theta^{i} \partial \theta^{j}} = - \text{Cov}(T^{i}, T^{j}) = - I(\theta)_{i,j} = - g_{i,j}(\theta)$$
>- The **Chrstoffel symbol** for **e-connection** of $p(x;\theta)$ from exponential family is given by 
>$$
> \begin{align}
> \Gamma_{i,j; k}^{(1)} := \Gamma_{i,j; k}^{(e)} &= \mathbb{E}_{\theta}\left[\left(\frac{\partial}{ \partial \theta^{i}} \frac{\partial}{ \partial \theta^{j}}\ell_{\theta} \right)\left( \frac{ \partial  }{ \partial \theta^{k} }\ell_{\theta}\right) \right], \quad i,j,k=1\,{,}\ldots{,}\,n \\[8pt]
>&= \mathbb{E}_{\theta}\left[\left(- I(\theta)_{i,j} \right)\left( T^{k}(X) - \mathbb{E}_{ \theta }\left[  T^{k}(X) \right]\right) \right] \\[5pt] 
>&= - I(\theta)_{i,j}\;\mathbb{E}_{\theta}\left[ T^{k}(X) - \mathbb{E}_{ \theta }\left[  T^{k}(X) \right] \right]\\[5pt]  
>&= 0
> \end{align}
>$$ 


>[!important] Theorem
>If  $\mathcal{S}$ is **fiat**, then a **necessary** and **sufficient** *condition* for a submanifold $\mathcal{M}$ to be **autoparallel** is that *$\mathcal{M}$* is expressed as an **affine subspace** (or an open subset of an affine subspace) of $\mathcal{S}$ with respect to an **affine coordinate system**. 
>
>In particular, **geodesics** may be expressed using **linear equations** (as a *line or a segment*) with respect to **affine coordinate systems**. 
>
>In addition, if $\mathcal{M}$ is **autoparallel**, then it is also **flat**.



## Explanation





-----------
##  Recommended Notes and References


- [[Statistical Manifold as Parametric Family]]
- [[Concepts related to Tangent Space and Tangent Bundle]]

- [[Log-Likelihood Score Function and Fisher Score]]
- [[Fisher Metric or Information Metric of Statistical Manifold]]


- [[Exponential Family of Distributions]]
- [[Riemannian Metric and Riemannian Manifold]]
- [[Statistical Manifold as Parametric Family]]


- [[Methods of Information Geometry by Amari]]
- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]
