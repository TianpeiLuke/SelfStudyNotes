---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - canonical_form
  - sum_product
  - PGM
  - probabilistic_graphical_models
keywords:
  - gaussian_graphical_model
  - probabilistic_graphical_model
  - sum_product
  - canonical_form
topics:
  - probabilistic_graphical_model
name: Canonical Form of Gaussian Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Canonical Form of Gaussian Graphical Model

>[!quote]
>the key difference between inference in the continuous and the discrete case is that the factors can no longer be represented as tables. Naively, we might think that we can represent **factors as Gaussians**, but this is *not the case*. The reason is that **linear Gaussian CPDs are generally not Gaussians**, but are rather a conditional distribution. Thus, we need to find a more *general representation* for factors, that accommodates both Gaussian distributions and linear Gaussian models, as well as any combination of these models that might arise during the course of inference.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 609

### Canonical Form

>[!important] Definition
>A **canonical form** $C(x; K, h, g)$ is a *logarithmic-concave function* on $\mathbb{R}^{d}$ defined as 
>$$
>C(x; K,h, g) = \exp \left( - \frac{1}{2}\left\langle Kx , x \right\rangle + \left\langle h , x \right\rangle  + g\right),
>$$
>where $K\in \mathbb{R}^{d\times d}$, $h\in \mathbb{R}^{d}$, and $g\in \mathbb{R}$ are parameters.

- [[Log-Concave and Log-Convex Function]]

>[!info]
>We can represent a multivariate Gaussian p.d.f. as a canonical form
>$$
>\begin{align*}
> \mathcal{N}(x; \mu, \Sigma) &= \frac{1}{\sqrt{(2\pi)^{n}|\det(\Sigma)| }}\exp \left(-\frac{1}{2}\left(x - \mu\right)^T\,\Sigma^{-1}\,(x - \mu)\right) \\
> &= \exp \left( -\frac{1}{2} \left\langle \Sigma^{-1}x , x \right\rangle + \left\langle \Sigma^{-1}\mu , x \right\rangle - \frac{1}{2}\left\langle \Sigma^{-1}\mu , \mu \right\rangle - \log \left( (2\pi)^{n / 2}\, |\det(\Sigma)|^{1 / 2}\right) \right) \\
> &:= C(x; K, h, g)
>\end{align*}
>$$
>where 
>$$
>\begin{align*}
> K &= \Sigma^{-1}\\
> h &= \Sigma^{-1}\mu\\
> g &= - \frac{1}{2}\left\langle \Sigma^{-1}\mu , \mu \right\rangle - \log \left( (2\pi)^{n / 2}\, |\det(\Sigma)|^{1 / 2}\right)
>\end{align*}
>$$
>- $K$ is **precision matrix** (**inverse covariance matrix**) of Gaussian distribution.
>- $(K, h)$ forms **canonical parameters** for Gaussian distribution for *sufficient statistics* $X, XX^T.$
>- $g$ is the *log-partition function.*
>

- [[Gaussian Random Vector]]
- [[Exponential Family of Distributions]]

>[!info]
>Note that in general, $K$ is *not necessarily invertible*.

### Operation on Canonical Forms

>[!important] Definition
>The **product** of two *canonical forms* over the same scope $x$ is 
>$$
>C(x; K_{1}, h_{1}, g_{1}) \cdot C(x; K_{2}, h_{2}, g_{2}) = C(x; K_{1} + K_{2}, h_{1} + h_{2}, g_{2} + g_{2})   
>$$
>
>If two canonical forms are of different scopes, we can extend their scopes and padding zeros in parameters.

>[!important] Definition
>The **division** of two *canonical forms* over the same scope $x$ is 
>$$
>\frac{C(x; K_{1}, h_{1}, g_{1})}{C(x; K_{2}, h_{2}, g_{2})} = C(x; K_{1} - K_{2}, h_{1} - h_{2}, g_{2} - g_{2})   
>$$
>
>If two canonical forms are of different scopes, we can extend their scopes and padding zeros in parameters.

>[!important] Definition
>The **vacuous canonical forms** is defined as
>$$
>1 \equiv C(x; 0, 0, 0)
>$$

>[!important] Definition
>Let  $C(x,y; K, h, g)$ be a *canonical form* over $(x,y)$ where 
>$$
>\begin{align*}
> K &= \left[\begin{array}{cc}
>K_{x x} & K_{x y} \\
>K_{y x} & K_{y y}
>\end{array}\right] \\[5pt]
> h&= \left[\begin{array}{c}
>h_{x}  \\
>h_{y} 
>\end{array}\right].
>\end{align*}
>$$
>The **marginalization** of *canonical forms* $C((x,y); K, h, g)$ is also a *canonical form*
>$$
>\begin{align*}
>  \int C(x,y; K, h, g) dy &= C(x; K', h', g')
\end{align*}
>$$
>where 
>$$
>\begin{align*}
> K' &= K_{x x} - K_{x y}K_{y y}^{-1}K_{y x} = K / K_{y y} \\[5pt]
> h' &= h_{x} - K_{x y}K_{y y}^{-1}h_{y}\\[5pt]
> g' &= g + \frac{1}{2}\left( \log \,\lvert 2\pi \, K_{y y}^{-1} \rvert\,  + \left\langle K_{y y}^{-1}h_{y} \,,\, h_{y} \right\rangle \right)
>\end{align*}
>$$
>
> Note that $K' = K / K_{y y}$ is the **Schur complement** of $K_{y y}$.

- [[Schur Complement and Inversion of Block Matrix]]

>[!important] Definition
>Let  $C(x,y; K, h, g)$ be a *canonical form* over $(x,y)$ where 
>$$
>\begin{align*}
> K &= \left[\begin{array}{cc}
>K_{x x} & K_{x y} \\
>K_{y x} & K_{y y}
>\end{array}\right] \\[5pt]
> h&= \left[\begin{array}{c}
>h_{x}  \\
>h_{y} 
>\end{array}\right].
>\end{align*}
>$$
>
>Given a  a context representing *evidence* $Y= y$, the **reduced canonical form** is also a *canonical form* $$C(X, Y=y; K, h, g) = C(X; K', h', g')$$ where
>$$
>\begin{align*}
> K' &= K_{x x}  \\[5pt]
> h' &= h_{x} - K_{x y}\,y\\[5pt]
> g' &= g + \left\langle h_{y} , y \right\rangle - \frac{1}{2}\left\langle K_{y y}\,y \,,\, y \right\rangle 
>\end{align*}
>$$

- [[Marginal and Conditional Distribution of Gaussian]]

## Explanation

>[!info]
>The operation of canonical form corresponding to different Gaussian distribution
>
>Suppose that $$C((x,y); K, h, g) = \mathcal{N}((x,y); \mu, \Theta) = C(x; \Theta, \Theta\mu, g)$$ where $\Theta = \Sigma^{-1}$ is the **inverse covariance matrix** or **precision matrix** of joint random variable $(X,Y)$
>
>- the **marginalization** of $C$ corresponds to the *marginal distribution* of $X$ $$C(x; K', h', g') = \mathcal{N}(x; \mu_{x}, \Sigma_{xx})$$ where $h' =  \Sigma_{xx}^{-1}\mu_{x}$ and $K' = \Sigma_{x x}^{-1}$
>- the **reduction** of of $C$ corresponds to the *conditional distribution* of $X$ given $Y=y$, $$C(x; K', h', g') = \mathcal{N}(x; \mu_{x|Y=y}, \Theta_{xx})$$


![[Marginal and Conditional Distribution of Gaussian#^4a335a]]

- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]
- [matrix inversion identity](https://en.wikipedia.org/w/index.php?title=Invertible_matrix&action=edit&section=18)

![[Marginal and Conditional Distribution of Gaussian#^fca789]]


![[Marginal and Conditional Distribution of Gaussian#^0d8021]]

- [[Marginal and Conditional Distribution of Gaussian]]




-----------
##  Recommended Notes and References

- [[Gaussian Belief Propagation]]
- [[Gaussian Graphical Model]]

- [[Inverse Covariance Estimation]]
- [[Gaussian Process]]
- [[Gaussian Measure]]
- [[Gaussian Random Function]]
- [[Gaussian Random Vector]]




- [[Probabilistic Graphical Models by Koller]] pp 608
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]