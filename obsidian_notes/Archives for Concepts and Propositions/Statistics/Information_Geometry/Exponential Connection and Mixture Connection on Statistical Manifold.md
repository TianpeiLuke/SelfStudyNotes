---
tags:
  - concept
  - math/information_geometry
  - math/information_theory
  - machine_learning/theory
  - probabilistic_graphical_models/algorithm
keywords:
  - e_connection
  - m_connection
topics:
  - information_geometry
  - information_theory
  - probabilistic_graphical_model
  - machine_learning_theory
name: e-Connection and m-Connection on Statistical Manifold
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: e-Connection and m-Connection on Statistical Manifold

![[alpha-Connection on Statistical Manifold#^24ddaa]]

- [[alpha-Connection on Statistical Manifold]]

### Exponential Connection

>[!important] Definition
>Let $\mathcal{S}$ be a $n$-dimensional *statistical manifold* with *parameterization* $\theta\in \Theta$. 
>- Denote $\ell_{\theta} := \log p_{\theta}$ as the *log-likelihood function*.
>
>Denote $\nabla^{(\alpha)}: \mathfrak{X}(\mathcal{S}) \times \mathfrak{X}(\mathcal{S}) \rightarrow \mathfrak{X}(\mathcal{S})$ as the *$\alpha$-connection*.
>
>The **exponential connection** or **e-connection** is the $\alpha$-connection when $\alpha = 1$.  
>- It is denoted as $$\nabla^{(e)} \quad \text{ or } \quad \nabla^{(1)}$$
>- The **coefficient** or the **Christoffel symbol** of the **e-connection** under the *Fisher metric* is formulated as
>$$
> \begin{align}
> \Gamma_{i,j; k}^{(1)} := \Gamma_{i,j; k}^{(e)} &= \mathbb{E}_{\theta}\left[\left(\frac{\partial}{ \partial \theta^{i}} \frac{\partial}{ \partial \theta^{j}}\ell_{\theta} \right)\left( \frac{ \partial  }{ \partial \theta^{k} }\ell_{\theta}\right) \right], \quad i,j,k=1\,{,}\ldots{,}\,n
> \end{align}
>$$ 

^a34e99

- [[Exponential Family of Distributions]]

### Mixture Connection

>[!important] Definition
>Let $\mathcal{S}$ be a $n$-dimensional *statistical manifold* with *parameterization* $\theta\in \Theta$. 
>- Denote $\ell_{\theta} := \log p_{\theta}$ as the *log-likelihood function*.
>
>Denote $\nabla^{(\alpha)}: \mathfrak{X}(\mathcal{S}) \times \mathfrak{X}(\mathcal{S}) \rightarrow \mathfrak{X}(\mathcal{S})$ as the *$\alpha$-connection*.
>
>The **mixture connection** or **m-connection** is the $\alpha$-connection when $\alpha = -1$.  
>- It is denoted as $$\nabla^{(m)} \quad \text{ or } \quad \nabla^{(-1)}$$
>- The **coefficient** or the **Christoffel symbol** of the **m-connection** under the *Fisher metric* is formulated as
>$$
> \begin{align}
> \Gamma_{i,j; k}^{(-1)} := \Gamma_{i,j; k}^{(m)} &= \mathbb{E}_{\theta}\left[\left(\frac{\partial}{ \partial \theta^{i}} \frac{\partial}{ \partial \theta^{j}}\ell_{\theta} +  \frac{\partial}{ \partial \theta^{i} }\ell_{\theta}\,\frac{\partial}{ \partial \theta^{j} }\ell_{\theta} \right)\left( \frac{ \partial  }{ \partial \theta^{k} }\ell_{\theta}\right) \right], \quad i,j,k=1\,{,}\ldots{,}\,n
> \end{align}
>$$ 

^fb526f

- [[Gaussian Mixture Models]]


## Explanation



## Exponential Family is Flat under Exponential-Connection

![[Exponential Family of Distributions#^b32aa5]]

![[Log-Partition Function of Exponential Family#^8780a9]]

![[Fisher Information for Exponential Family#^713d66]]

- [[Log-Partition Function of Exponential Family]]
- [[Fisher Information for Exponential Family]]

>[!important] 
>Let $p(x; \theta)$ be a p.d.f. from an *exponential family*
>$$
> p(x; \theta) := \exp\left( \left\langle  \theta,\, T(x)   \right\rangle - A(\theta)\right)\,h(x)
>$$
>
>- The *log-likelihood function* $$\ell(\theta; x) :=  \left\langle  \theta,\, T(x)   \right\rangle - A(\theta) $$ 
>- The *score function*, i.e. the basis of tangent space $T_{p}\mathcal{S}$ is given by $$\begin{align*}\frac{ \partial \ell }{ \partial \theta^{i} } &= T_{i}(x) - \frac{ \partial  }{ \partial \theta^{i} }A(\theta) \\[5pt] &=  T_{i}(x) - \mathbb{E}_{ \theta }\left[  T_{i}(X) \right] \end{align*}$$
>- The *second derivative* is given by the **Fisher metric** $$\frac{ \partial^2 \ell }{ \partial \theta^{i} \partial \theta^{j}} = - \text{Cov}(T_{i}, T_{j}) = - I(\theta)_{i,j} = - g_{i,j}(\theta)$$
>- The **Chrstoffel symbol** for **e-connection** of $p(x;\theta)$ from exponential family is given by 
>$$
> \begin{align}
> \Gamma_{i,j; k}^{(1)} := \Gamma_{i,j; k}^{(e)} &= \mathbb{E}_{\theta}\left[\left(\frac{\partial}{ \partial \theta^{i}} \frac{\partial}{ \partial \theta^{j}}\ell_{\theta} \right)\left( \frac{ \partial  }{ \partial \theta^{k} }\ell_{\theta}\right) \right], \quad i,j,k=1\,{,}\ldots{,}\,n \\[8pt]
>&= \mathbb{E}_{\theta}\left[\left(- I(\theta)_{i,j} \right)\left( T_{k}(X) - \mathbb{E}_{ \theta }\left[  T_{k}(X) \right]\right) \right] \\[5pt] 
>&= - I(\theta)_{i,j}\;\mathbb{E}_{\theta}\left[ T_{k}(X) - \mathbb{E}_{ \theta }\left[  T_{k}(X) \right] \right]\\[5pt]  
>&= 0
> \end{align}
>$$ 

- [[Fisher Metric or Information Metric of Statistical Manifold]]

>[!important] Theorem
>An **exponential family** in the form of $$p(x; \theta) := \exp\left( \left\langle  \theta,\, T(x)   \right\rangle - A(\theta) \right)\,h(x)$$ is **e-fiat** i.e. $$\Gamma_{i,j:k}^{(e)} = 0$$ and its **natural parameters** $$\theta := (\theta^1 \,{,}\ldots{,}\,\theta^{n})$$ form an **e-affine coordinate system**.

- [[Exponential Family as Affine Subspace in Statistical Manifold]]

## Mixture Distribution is Flat under Mixture-Connection

>[!important] 
>Let $p(x; \theta)$ be a p.d.f. from a **mixture family**
>$$
> p(x; \theta) := \left\langle  \theta\,,\,T(x)    \right\rangle + h(x) = \sum_{i}\theta^{i}T_{i}(x) + h(x)
>$$
>- For instance $$\begin{align} p(x; \theta)&= \sum_{i=1}^{n}\theta^{i}p_{i}(x) + \left(1- \sum_{i=1}^{n}\theta^{i}\right)\,p_{0}(x) \\[5pt] &= p_{0}(x) + \sum_{i=1}^{n}\theta^{i}\left(p_{i}(x) - p_{0}(x)\right) \end{align}$$
>- The *score function*, i.e. the basis of tangent space $T_{p}\mathcal{S}$ is given by $$\begin{align*}\frac{ \partial \ell }{ \partial \theta^{i} } &= \frac{1}{p(x; \theta)} T_{i}(x) \end{align*}$$
>- The *second derivative* is given by  $$\frac{ \partial^2 \ell }{ \partial \theta^{i} \partial \theta^{j}} = - \frac{T_{i}(x) T_{j}(x)}{p^2(x; \theta)}$$
>- The **Chrstoffel symbol** for **m-connection** of $p(x;\theta)$ from mixture family is given by 
>$$
> \begin{align}
> \Gamma_{i,j; k}^{(-1)} := \Gamma_{i,j; k}^{(m)} &= \mathbb{E}_{\theta}\left[\left(\frac{\partial}{ \partial \theta^{i}} \frac{\partial}{ \partial \theta^{j}}\ell_{\theta} +  \frac{\partial}{ \partial \theta^{i} }\ell_{\theta}\,\frac{\partial}{ \partial \theta^{j} }\ell_{\theta} \right)\left( \frac{ \partial  }{ \partial \theta^{k} }\ell_{\theta}\right) \right], \quad i,j,k=1\,{,}\ldots{,}\,n \\[8pt]
>&= \mathbb{E}_{\theta}\left[\left( - \frac{T_{i}(X) T_{j}(X)}{p^2(X; \theta)} +  \frac{1}{p(X; \theta)} T_{i}(X) \frac{1}{p(X; \theta)} T_{j}(X)  \right)\left( \frac{1}{p(X; \theta)} T_{i}(X) \right) \right] \\[5pt] 
>&= 0
> \end{align}
>$$ 


>[!important] Theorem
>A **mixture family** in the form of $$p(x; \theta) = \left\langle  \theta\,,\,T(x)    \right\rangle + h(x)$$ is **m-fiat** i.e. $$\Gamma_{i,j:k}^{(m)} = 0$$ and its **mixture parameters** $$\theta := (\theta^1 \,{,}\ldots{,}\,\theta^{n})$$ form an **m-affine coordinate system**.


## Information Projection and Moment Projection

![[Information Projection and Moment Projection#^0fc945]]

![[Information Projection and Moment Projection#^2f1ad5]]

- [[Information Projection and Moment Projection]]


-----------
##  Recommended Notes and References


- [[Information Projection and Moment Projection]]

- [[Duality of Connections on Riemannian Manifold]]

- [[Riemannian Metric and Riemannian Manifold]]

- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Concepts related to Tangent Space and Tangent Bundle]]

- [[Connection in Vector Bundle and Covariant Derivative]]
- [[Affine Connection on Tangent Bundle]]


- [[Metric Connection for Riemannian Manifold]]




- [[Methods of Information Geometry by Amari]] pp 33 - 34
- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]
