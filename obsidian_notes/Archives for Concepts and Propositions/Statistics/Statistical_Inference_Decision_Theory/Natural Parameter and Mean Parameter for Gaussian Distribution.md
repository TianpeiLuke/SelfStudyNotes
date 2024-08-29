---
tags:
  - concept
  - probabilistic_graphical_models/models
  - math/probability
  - statistics/estimation
keywords:
  - natural_parameterization
  - mean_parameterization
topics:
  - probability
  - probabilistic_graphical_model
  - statistics/estimation
name: Natural Parameter and Mean Parameter for Gaussian Distribution
date of note: 2024-08-28
---

## Concept Definition

>[!important]
>**Name**: Natural Parameter and Mean Parameter for Gaussian Distribution

![[Gaussian Random Vector#^a97326]]

![[Gaussian Graphical Model#^162c43]]

### Natural Parameters

>[!important] Definition
>The *multivariate Gaussian distribution* $\mathcal{N}(\mu, \Sigma)$ has the **natural paramterization**
>$$
>p(x; \theta, \Theta) := \exp \left(\left\langle  \theta\,,\, x  \right\rangle + \left\langle  \Theta\,x\,,\, x \right\rangle - A(\theta, \Theta) \right)
>$$
>where the **natural parameters** $(\theta, \Theta) = \omega(\mu, \Sigma)$ 
>$$
>\begin{align*}
> \theta &= \Sigma^{-1}\mu\\[5pt]
> \Theta &= -\frac{1}{2} \Sigma^{-1}
>\end{align*}
>$$
>- The **log-partition function** parameterized by $(\mu, \Sigma)$ is $$A(\mu, \Sigma) = \frac{1}{2}\left\{n \log(2\pi) + \left\langle  \Sigma\mu\,,\, \mu \right\rangle + \log \det \left\lvert  \Sigma \right\rvert \right\}$$
>- The **log-partition function** parameterized by $(\theta, \Theta)$ is  $$A(\theta, \Theta) = \frac{1}{2}\left\{n \log(2\pi) - \frac{1}{2}\left\langle  \Theta^{-1}\theta\,,\, \theta \right\rangle -\log \left[  (-2)^{n} \det \left\lvert  \Theta \right\rvert\right] \right\}$$
>
>- The **sufficient statistics** for $\Theta$ and $\theta$ are 
>  $$
> \begin{align*}
> X & \leftrightarrow \theta  \\[5pt]
> XX^{T} & \leftrightarrow \Theta
>\end{align*}
> $$ 
>- Denote the **sufficient statistic vector** $$T = \left[\begin{array}{c}(X_{i}) \\[5pt] (X_{i}^2) \\[5pt] (2X_{i}X_{j})_{i<j} \end{array} \right] := \left[\begin{array}{c}(T_{i}) \\[5pt] (T_{i,i}) \\[5pt] (T_{i,j})_{i<j} \end{array} \right]$$ 
>
>- The **inverse** of mapping, $\omega^{-1}$, is defined as
>$$
>\begin{align*}
> \mu &= -\frac{1}{2} \Theta^{-1}\theta\\[5pt]
> \Sigma &= -\frac{1}{2} \Theta^{-1}
>\end{align*}
>$$

- [[Gaussian Random Vector]]
- [[Gaussian Graphical Model]]
- [[Canonical Form of Gaussian Graphical Model]]
- [[Exponential Family of Distributions]]

### Mean Parameters

>[!important] Definition
>The **mean parameters** for $\mathcal{N}(\mu, \Sigma)$ can be obtained as $(\eta, E) = \chi(\mu, \Sigma)$
>$$
>\begin{align*}
> \eta &= \mathbb{E}_{ p }\left[  X \right] = \mu \\[5pt]
> E &= \mathbb{E}_{ p }\left[  X\,X^{T} \right] = \Sigma + \mu\,\mu^{T}
>\end{align*}
>$$
>- The *inverse mapping* is defined as 
>$$
>\begin{align*}
> \mu &= \eta \\[5pt]
> \Sigma  &= E - \eta\,\eta^{T}
>\end{align*}
>$$  
>- The **negative entropy** parameterized by $(\eta, E)$ is  $$-H(\eta, E) = -\frac{n}{2}\left\{ \log(2\pi) + 1 \right\} - \frac{1}{2} \log \det \left\lvert E - \eta\,\eta^{T}  \right\rvert $$
>- The **mean parameterization** of the p.d.f. of Gaussian distribution is 
>  $$
>  p(x; \eta, E) := \exp \left(-\frac{1}{2} \left\langle \left(E - \eta\,\eta^{T}\right)^{-1}\,\left(x - \eta\right) \,,\, \left(x - \eta\right)   \right\rangle - H(\eta, E) + \frac{n}{2} \right)
> $$

- [[Log-Partition Function of Exponential Family]]

### Fisher Information

![[Fisher Information#^03df64]]

- [[Fisher Information]]

>[!important] Definition
>The **Fisher information** of parameters $(\mu, \Sigma)$ for Gaussian distribution $\mathcal{N}(\mu, \Sigma)$ is
>$$
>\begin{align*}
> I_{\mu, \Sigma}(\mu, \Sigma) = \left[ \begin{array}{cc}\Sigma^{-1} & 0 \\0 & \alpha_{klmn} \end{array} \right] 
>\end{align*}
>$$

>[!important] Definition
>The **Fisher information** of *natural parameters* $(\theta, \Theta)$ is the **Hessian** of *log-partition function*
>$$
>I_{\theta, \Sigma}(\theta, \Theta) = \nabla^2\,A(\theta, \Theta)
>$$
>and
>$$
>\begin{align*}
> I_{\theta, \Sigma}(\theta, \Theta)  = \frac{1}{2} \left[ \begin{array}{cc} - \Theta^{-1} & \Lambda_{kl}\,\theta \\[5pt] \theta^{T}\,\Lambda_{mn} & \lambda_{klmn} - \theta^{T}\,\Lambda_{klmn}\,\theta \end{array} \right] 
>\end{align*}
>$$
>where 
>- $$\Lambda_{kl} = \left\{ \begin{array}{ll}\left[\Theta^{-1}\right]_{\cdot,k}\,\left[\Theta^{-1}\right]_{k,\cdot} & \text{ if }k=l \\[5pt] \left[\Theta^{-1}\right]_{\cdot,k}\,\left[\Theta^{-1}\right]_{l,\cdot} + \left[\Theta^{-1}\right]_{\cdot,l}\,\left[\Theta^{-1}\right]_{k,\cdot} & \text{ if }k\neq l   \end{array} \right.$$
>- $$\Lambda_{klmn} = \left\{ \begin{array}{ll}\left[\Lambda_{kk} \right]_{\cdot,m}\,\left[\Theta^{-1}\right]_{n,\cdot} & \text{ if }k=l \\[5pt] \left[\Lambda_{kl}\right]_{\cdot,m}\,\left[\Theta^{-1}\right]_{n,\cdot} + \left[\Lambda_{kl}\right]_{\cdot,n}\,\left[\Theta^{-1}\right]_{m,\cdot} & \text{ if }k\neq l   \end{array} \right.$$
>- $$\lambda_{klmn} = \left\{ \begin{array}{ll}\left[\Theta^{-1} \right]_{k,k}\,\left[\Theta^{-1}\right]_{k,k} & \text{ if }k=l=m=n \\[5pt] \left[\Theta^{-1}\right]_{k,m}\,\left[\Theta^{-1}\right]_{l,n} + \left[\Theta^{-1}\right]_{l,m}\,\left[\Theta^{-1}\right]_{k,n} & \text{ if }k = l \, \veebar\, m = n \\[5pt] 2\left(\left[\Theta^{-1}\right]_{k,m}\,\left[\Theta^{-1}\right]_{l,n} + \left[\Theta^{-1}\right]_{l,m}\,\left[\Theta^{-1}\right]_{k,n}\right) & \text{ otherwise }  \end{array} \right.$$
>
>Moreover, we have $$I(\theta) = \text{Cov}(T_{i}, T_{j})$$

- [[Log-Partition Function of Exponential Family]]
- [[Exponential Family and Convex Duality]]
- Malagò, L., & Pistone, G. (2015, January). Information geometry of the Gaussian distribution in view of stochastic optimization. In _Proceedings of the 2015 ACM Conference on Foundations of Genetic Algorithms XIII_ (pp. 150-162).


## Explanation





-----------
##  Recommended Notes and References


- [[Canonical Form of Gaussian Graphical Model]]
- [[Gaussian Random Vector]]
- [[Gaussian Graphical Model]]
- [[Gaussian Process]]
- [[Inverse Covariance Estimation]]



- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- Malagò, L., & Pistone, G. (2015, January). Information geometry of the Gaussian distribution in view of stochastic optimization. In _Proceedings of the 2015 ACM Conference on Foundations of Genetic Algorithms XIII_ (pp. 150-162).

