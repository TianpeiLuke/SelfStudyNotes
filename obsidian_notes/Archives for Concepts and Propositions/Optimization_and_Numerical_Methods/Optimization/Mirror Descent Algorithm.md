---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - mirror_descent_algorithm
topics:
  - optimization/algorithm
name: Mirror Descent Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Mirror Descent Algorithm

>[!important] Definition
>Consider the *convex optimization problem*
>$$
>\begin{align*}
> \min\; & f(x)\\
> \text{s.t. }& x \in \mathcal{X}
>\end{align*}
>$$
>where $f: \mathbb{R}^{n}\to \mathbb{R}$ is a *convex function*, and $\mathcal{X}$ is a *closed convex set*.
>
>The **mirror descent algorithm** solves the following problem at each iteration $k$
>$$
>x_{k+1} \in \arg\min_{x \in \mathcal{X}}\left\{ \ell(x; x_{k}) + D_{k}(x, x_{k}) \right\} 
>$$
>where
>-  $\ell(x;x_{0})$ is the **linearization** of $f$ at $x_{k}$ by *subgradients* $$\ell(x; x_{k}) := f(x_{k}) + \left\langle  g_{k}\,,\, x - x_{k}    \right\rangle, \quad g_{k} \in \partial f(x_{k})$$
>- $D_{k}: \mathbb{R}^n \times \mathbb{R}^n \to \mathbb{R}_{+}$ is a (nonquadratic) **proximal term** 

^1b2c18


- [[Bregman Divergence]]
- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]
- [[Proximal Gradient Algorithm]]
- [[Generalized Proximal Method]]
- [[Subdifferential of Convex Function]]
- [[Subgradient Methods]]
- [[Follow-The-Regularized-Leader Algorithm]]

>[!example]
>Assume that $f$ is convex and differentiable.
>
>The **classical mirror descent** uses the **Bregman divergence** as proximal term
>$$
>x_{k+1} \in \arg\min_{x} \left\{ f(x_{k}) + \left\langle \nabla f(x_{k}) , x - x_{k} \right\rangle + \mathbb{D}_{\psi}\left(  x\left\|\right. x_{k} \right) \right\} 
>$$
>where
>$$
>\mathbb{D}_{\psi}\left(  x\left\|\right. x_{k} \right) := \psi(x) - \psi(x_{k}) - \left\langle \nabla \psi(x_{k}) , x - x_{k} \right\rangle.
>$$




## Explanation

>[!info]
>We can derive mirror descent from **proximal gradient** algorithm, 
>$$
>x_{k+1} \in \arg\min_{x \in \mathcal{X}}\left\{ \ell(x; x_{k}) + \frac{1}{2\alpha_{k}}\lVert x - x_{k} \rVert^2  \right\} 
>$$
>as
>$$
>\arg\min_{x}\left\{   \left\langle  \nabla f(x_{k})\,,\, x - x_{k} \right\rangle + \frac{1}{2\alpha_{k}}\lVert x - x_{k} \rVert^2 \right\}  = \arg\min_{x}\left\{  \frac{1}{2\alpha_{k}}\lVert x- x_{k} + \alpha_{k}\;\nabla f(x_{k}) \rVert^2 \right\}
>$$

- [[Proximal Gradient Algorithm]]

>[!info]
>**Mirror descent algorithm** is best suited for non-differentiable convex loss function $f$.
>
>For instance,
>- the **hinge loss** $$f(x) := \max\left\{0, 1 - y\,g(x) \right\} $$
>- the **least absolute deviation** $$f(x) := \lVert y - Ax \rVert_{1}$$

- [[Hinge Loss as Surrogate Loss Function]]
- [[Least Absolute Deviations]]
- [[Least Absolute Deviations Solution via Iterative Re-weighted Least Square]]


## Gradient Descent 

>[!example]
>Assume that $f$ is convex and differentiable, and the proximal term $D_{k}$ is a quadratic norm.
>
> We have the **mirror descent**
>$$
>x_{k+1} \in \arg\min_{x}\;\left\{ f(x_{k}) + \left\langle \nabla f(x_{k}), x - x_{k}  \right\rangle + \frac{1}{\alpha_{k}}\lVert x - x_{k} \rVert_{2}^2 \right\} 
>$$
>which leads to solution
>$$
>x_{k+1} = x_{k} - \alpha_{k} \nabla f(x_{k})
>$$
>This is the **gradient descent algorithm.**

^3e19a2

- [[Gradient Descent Algorithm]]
- Allen-Zhu, Z., & Orecchia, L. (2016). _Linear Coupling: An Ultimate Unification of Gradient and Mirror Descent_ (arXiv:1407.1537). arXiv. [https://doi.org/10.48550/arXiv.1407.1537](https://doi.org/10.48550/arXiv.1407.1537)


## Multiplicative Weights

- [[Exponential Weights Algorithm as Mirror Descent]]
- [[Weighted Average Forecast via Potential]]
- [[Weighted Majority Algorithm for Binary Loss]]
- Nedić, A., & Lee, S. (2014). On Stochastic Subgradient Mirror-Descent Algorithm with Weighted Averaging. _SIAM Journal on Optimization_, _24_(1), 84–107. [https://doi.org/10.1137/120894464](https://doi.org/10.1137/120894464)


## Online Mirror Descent

- [[Follow-The-Regularized-Leader Algorithm]]
- [[Perceptron Algorithm]]
- Duchi, J., Shalev-Shwartz, S., Singer, Y., & Tewari, A. (2010). Composite Objective Mirror Descent. _Proceedings of the 23rd Annual Conference on Learning Theory (COLT 2010)_, 14–26. [http://eprints.pascal-network.org/archive/00007140/](http://eprints.pascal-network.org/archive/00007140/)
- McMahan, B. (2011). Follow-the-Regularized-Leader and Mirror Descent: Equivalence Theorems and L1 Regularization. _Proceedings of the Fourteenth International Conference on Artificial Intelligence and Statistics_, 525–533. [https://proceedings.mlr.press/v15/mcmahan11b.html](https://proceedings.mlr.press/v15/mcmahan11b.html)


## Mirror Descent and Information Geometry

- Raskutti, G., & Mukherjee, S. (2015). The Information Geometry of Mirror Descent. _IEEE Transactions on Information Theory_, _61_(3), 1451–1457. IEEE Transactions on Information Theory. [https://doi.org/10.1109/TIT.2015.2388583](https://doi.org/10.1109/TIT.2015.2388583)


## Mirror Descent and ODE

- [[Ordinary Differential Equations]]
- Krichene, W., Bayen, A., & Bartlett, P. L. (2015). Accelerated Mirror Descent in Continuous and Discrete Time. _Advances in Neural Information Processing Systems_, _28_. [https://proceedings.neurips.cc/paper/2015/hash/f60bb6bb4c96d4df93c51bd69dcc15a0-Abstract.html](https://proceedings.neurips.cc/paper/2015/hash/f60bb6bb4c96d4df93c51bd69dcc15a0-Abstract.html)
- Amid, E., & Warmuth, M. K. K. (2020). Reparameterizing Mirror Descent as Gradient Descent. _Advances in Neural Information Processing Systems_, _33_, 8430–8439. [https://proceedings.neurips.cc/paper/2020/hash/604b37ea63ea51fa5fb3d8a89ec056e6-Abstract.html](https://proceedings.neurips.cc/paper/2020/hash/604b37ea63ea51fa5fb3d8a89ec056e6-Abstract.html)



-----------
##  Recommended Notes and References


- [[Bregman Projection]]
- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Convex Function]]
- [[Polyhedron and Polytope]]
- [[Strongly Convex Function]]

- [[Exponential Weights Algorithm as Mirror Descent]]
- [[Online Convex Optimization]]

- [[Generalized Proximal Method]]
- [[Gradient Descent Algorithm]]
- [[Approximation Method for Optimization]]

- [[Convex Optimization Algorithms by Bertsekas]] pp 382
- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]] pp 142
- [[Introduction to Online Convex Optimization by Hazan]] pp 77 - 81