---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
keywords:
  - alpha_divergence
  - alpha_connection
topics:
  - information_geometry
  - information_theory
name: alpha-Divergence
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: $\alpha$-Divergence

![[f-Divergence#^e7fa76]]

>[!important] Definition
>Define a real-valued function $f^{(\alpha)}: \mathbb{R} \to \mathbb{R}$ for $\alpha\in [-1,1]$ as follows
>$$
>f^{(\alpha)}(x) = \left\{\begin{array}{cl} \dfrac{4}{1- \alpha^2}\left[ 1 - x^{(1+\alpha)/2} \right] & \alpha \not\in \{ -1, 1 \} \\[5pt] x \log x & \alpha = 1 \\[5pt] -\log x & \alpha = -1  \end{array}  \right. 
>$$ 
>
>Let $P$ and $Q$ be *probability measures* on a measurable space $(\Omega, \mathscr{F})$, and $P$ is *absolutely continuous* with respect to $Q$, 
>$$P \ll Q.$$
>
>The **$\alpha$-divergence** from $Q$ to $P$ is defined as
>$$
>\begin{align*}
>\mathbb{D}^{(\alpha)}\left(P\left\|\right.Q\right) &= \frac{4}{1- \alpha^2} \int \left[ 1 - \left(\frac{dP}{dQ}\right)^{(1+\alpha)/2} \right] dQ \\[10pt] 
>&= \frac{4}{1- \alpha^2} \left\{ 1 - \int_{\Omega} P(dx)^{(1- \alpha)/2}\;Q(dx)^{(1 + \alpha)/2} \right\} \\[5pt] 
>&=  \frac{4}{1- \alpha^2} \left\{ 1 - \int_{\Omega} p(x)^{(1- \alpha)/2}\;q(x)^{(1 + \alpha)/2}\,d\mu(x) \right\}.
>\end{align*}
>$$
>where 
>- $$\frac{dP}{dQ} \in Q$$ is the *Radon-Nikodym derivative* which is $Q$-measurable random variable.
>- And $p(x)$, $q(x)$ are *p.d.f*. of $P$ and $Q$ with respect to a common $\sigma$-finite measure $\mu$ on $(\Omega, \mathscr{F}).$
>- The **$\alpha$-divergence** is a *special case* of the *$f$-divergence* where $f = f^{(\alpha)}$ $$\mathbb{D}^{(\alpha)}\left(P\left\|\right.Q\right) := \mathbb{D}_{f^{(\alpha)}}\left(P\left\|\right.Q\right)$$


- [[f-Divergence]]
- [[Absolute Continuity for Measures]]
- [[Radon-Nikodym Derivative]]


## Explanation


## Example

>[!example]
>$$f^{(1)}(x) := x\log(x),$$ we have the [[Kullback-Leibler Divergence]].
>$$
>\mathbb{D}^{(1)}\left(P\left\|\right.Q\right) = \int \frac{dP}{dQ} \log\left( \frac{dP}{dQ} \right) dQ = \int  \log\left( \frac{dP}{dQ} \right) dP = \mathbb{KL}\left( P \left\|\right. Q \right) .
>$$

>[!example]
>$$f^{(-1)}(x) := -\log(x),$$ we have the **reversed** [[Kullback-Leibler Divergence]].
>$$
>\mathbb{D}^{(-1)}\left(P\left\|\right.Q\right) = \int - \log\left( \frac{dP}{dQ} \right) dQ = \int  \log\left( \frac{dQ}{dP} \right) dQ = \mathbb{KL}\left( Q \left\|\right. P \right) .
>$$

- [[Exponential Connection and Mixture Connection on Statistical Manifold]]

>[!example]
>$$f^{(0)}(x) := 4(1 - \sqrt{ x }),$$ we have 
>$$
>\mathbb{D}^{(0)}\left(P\left\|\right.Q\right) = 2 \int_{\Omega}\,\left(\sqrt{ p(x)} - \sqrt{q(x)} \right)^2\,d\mu(x).
>$$
>where the square root of it is the **Hellinger distance**
>$$
>\frac{1}{2} \sqrt{\mathbb{D}^{(0)}\left(P\left\|\right.Q\right)} = \left\{ \frac{1}{2} \int_{\Omega}\,\left(\sqrt{ p(x)} - \sqrt{q(x)} \right)^2\,d\mu(x) \right\}^{1/2} 
>$$

- Wikipedia [Hellinger_distance](https://en.wikipedia.org/wiki/Hellinger_distance)


## $\alpha$-Connection

- [[alpha-Connection on Statistical Manifold]]




-----------
##  Recommended Notes and References



- [[alpha-Connection on Statistical Manifold]]
- [[Dual of alpha-Connection]]
- [[Divergence Function on Manifold]]


- [[Riemannian Metric and Riemannian Manifold]]

- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Concepts related to Tangent Space and Tangent Bundle]]


- [[f-Divergence]]
- [[Kullback-Leibler Divergence]]
- [[Phi Entropy Functional]]



- [[Methods of Information Geometry by Amari]] pp 57
- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]
