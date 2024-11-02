---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - deep_learning/representation_learning
keywords:
  - autoencoder
  - representation_learning
  - contractive_autoencoder
topics:
  - representation_learning
name: Contractive Auto-Encoder
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Contractive Auto-Encoder

![[Auto-Encoder and Stochastic Auto-Encoder#^53810a]]

- [[Auto-Encoder and Stochastic Auto-Encoder]]

![[Sparse Auto-Encoder and Regularized Auto-Encoder#^e81e41]]

- [[Sparse Auto-Encoder and Regularized Auto-Encoder]]
- [[Regularized Loss Minimization]]

>[!important] Definition
>The **contractive autoencoder (CAE)** learns both *encoder function* $f$ and *decoder function* $g$ that minimize the *reconstruction error* with **regularization penalty** on the **derivative** of *hidden units*
>$$
>\min_{f, g}\sum_{i=1}^{n}L(X_{i} , g(f(X_{i})) ) + \lambda\,\sum_{i}\lVert \nabla_{x} h_{i}\rVert^2 
>$$   
>where 
>- $L: \mathbb{R}^{d} \times \mathbb{R}^{d} \to \mathbb{R}$ is the loss function that measures the *similarity* between the *input* and the *reconstructed input*.
>- The penalty is defined as $$\sum_{i}\lVert \nabla_{x} h_{i}\rVert^2    = \left\lVert  \frac{ \partial f }{ \partial x }   \right\rVert_{F}^{2}$$
>	- $$\frac{ \partial f }{ \partial x } := Df \in \mathbb{R}^{s\times d}$$ is the *Jacobian matrix* for encoder $f: \mathbb{R}^{d} \to \mathbb{R}^{s}$.
>	- $\lVert \cdot \rVert_{F}$ is the **Frobenius norm** $$\lVert A \rVert_{F} := \sqrt{\sum_{i}\sum_{j} A_{i,j}^2}.$$

- [[Jacobian Matrix and Jacobian Determinant]]
- [[Contraction Function]]

## Explanation

>[!quote]
>The name **contractive** arises from the way that the CAE warps space. Specifically, because the CAE is trained to *resist perturbations of its input*, it is encouraged to map a neighborhood of input points to a smaller neighborhood of output points.  We can think of this as **contracting the input neighborhood to a smaller output neighborhood.**
>
>-- [[Deep Learning by Goodfellow]] pp 511 - 512
  
- [[Contraction Function]]


>[!quote]
>To clarify, the CAE is **contractive only locally**—all perturbations of a training point $x$ are mapped *near* to $f (x)$. *Globally*, two different points $x$ and $x'$ may be mapped to $f(x)$ and $f(x')$ points that are farther apart than the original points. It is plausible that $f$ could be *expanding in-between or far from the data manifolds* (see, for example, what happens in the 1-D toy example of figure 14.7). When the $\Omega(h)$ penalty is applied to sigmoidal units, one easy way to *shrink the Jacobian* is to make the sigmoid units *saturate* to $0$ or $1$. This encourages the CAE to encode input points with *extreme values* of the sigmoid, which may be interpreted as a binary code. It also ensures that the CAE will *spread* its code values throughout most of the *hypercube* that its sigmoidal hidden units can span.
>
>-- [[Deep Learning by Goodfellow]] pp 512  


>[!quote]
>We can think of the *Jacobian matrix* $J$ at a point $x$ as **approximating** the nonlinear encoder $f(x)$ as being a *linear operator*. This allows us to use the word “contractive” more formally. In the theory of linear operators, a *linear operator* is said to be **contractive** if the *norm* of $J x$ remains less than or equal to $1$ for all unit-norm $x$. In other words, $J$ is *contractive* if it **shrinks the unit sphere**. We can think of the CAE as penalizing the *Frobenius norm of the local linear approximation of* $f (x)$ at *every training point* $x$ in order to encourage each of these local linear operators to become a contraction.
>
>-- [[Deep Learning by Goodfellow]] pp 512  


>[!quote]
>The **goal** of the CAE is to *learn the __manifold structure__* of the data. Directions $x$ with large $J x$ rapidly change $h$, so these are likely to be directions that approximate the *tangent planes of the manifold*.
>
>-- [[Deep Learning by Goodfellow]] pp 512  

- [[Smooth Manifold]]







-----------
##  Recommended Notes and References


- [[Latent Variable Models]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Artificial Neural Network and Deep Learning]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 496 - 498, 510 - 513
- [[Deep Learning Foundations and Concepts by Bishop]] pp 563 - 567
- Rifai, S., Vincent, P., Muller, X., Glorot, X., & Bengio, Y. (2011, June). Contractive auto-encoders: Explicit invariance during feature extraction. In _Proceedings of the 28th international conference on international conference on machine learning_ (pp. 833-840).