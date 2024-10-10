---
tags:
  - concept
  - machine_learning/models
  - statistics/estimation
  - statistics/inference
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/inference
  - probabilistic_graphical_models/algorithm
keywords:
  - inverse_covariance_estimation
  - precision_matrix
  - multivariate_gaussian_distribution
topics:
  - machine_learning_models
  - probabilistic_graphical_model
  - statistics/inference
  - statistics/estimation
name: Inverse Covariance Estimation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Inverse Covariance Estimation

![[Gaussian Random Vector#^a97326]]

- [[Gaussian Random Vector]]

>[!important] Definition
>Let $X\sim \mathcal{N}(0, \Sigma)$, i.e. the p.d.f. of $X\in \mathbb{R}^{d}$ is of the form
>$$
>\mathcal{N}(x; 0, \Sigma) = \frac{1}{\sqrt{(2\pi)^{d}|\det(\Sigma)| }}\exp \left(-\frac{1}{2}x^T\,\Sigma^{-1}\,x\right)
>$$
>where $\Sigma \succ 0$.
>- We denote the *inverse of covariance matrix* as **the precision matrix** $$\Theta = \Sigma^{-1} \succ 0$$
>- The above p.d.f. in terms of *precision matrix* is given by $$\mathcal{N}(x; 0, \Theta) = \frac{\sqrt{ |\det(\Theta)| }}{\sqrt{(2\pi)^{d}}}\exp \left(-\frac{1}{2}x^T\,\Theta\,x\right)$$
>- The *log-likelihood function* of $\Theta$ is given by $$-\frac{1}{2}x^T\,\Theta\,x + \frac{1}{2}\log \det|\Theta| - \frac{d}{2}\log (2\pi)$$
>  
>The task of **inverse covariance estimation** is to find the *maximum likelihood estimation* of $\Theta\in \mathcal{S}_{++}^{n}$, i.e.
>$$
>\begin{align*}
> \min_{\Theta \in \mathbb{R}^{d\times d}} \;&\; \frac{1}{2}x^T\,\Theta\,x - \frac{1}{2}\log \det|\Theta| \\[5pt]
> \text{s.t. }\;&\;\Theta \succ 0
>\end{align*}
>$$
>where
>- the first term $$\frac{1}{2}x^T\,\Theta\,x = \frac{1}{2}\left\langle  x\,,\,\Theta x    \right\rangle = \text{tr}\left(\frac{1}{2}x x^{T}\,\Theta\right)$$ is *linear* in $\Theta$
>- and the second term  $$g(\Theta):= - \frac{1}{2}\log \det|\Theta|$$ is **convex**, since $\log \det \Theta$ is *concave* for any $\Theta \succ 0.$
>- and $\mathcal{S}_{++}^{n}$ is *convex set*.
>- So the *inverse covariance estimation* is a **convex programming problem**.

- [[Maximum Likelihood Estimation]]
- [[Positive Semidefinite Transformation]]
- [[Trace of Matrix]]
- [[Determinant of Linear Transformation]]
- [[Convex Function]]
- [[Convex Set]]
- [[Convex Optimization Problem]]

>[!info]
>The *log-determinant term* is seen as **regularization term** on the spectrum of $\Theta$
>
>For $$g(\Theta):= - \frac{1}{2}\log \det|\Theta|,$$ the following holds $$ - \frac{1}{2}\log \det|\Theta| = -\frac{1}{2} \log \prod_{i=1}^{d}\lambda_{i}(\Theta) = -\frac{1}{2}\sum_{i=1}^{d}\log \lambda_{i}(\Theta)$$ where $\lambda_{i}$ is the eigenvalues of $\Theta$, which are all *real positive*.
>- This is essentially the same term as in **barrier method** since $$-\log \lambda_{i}(\Theta) \to \infty \text{ when }\lambda_{i} \to 0$$
>- Thus we can drop the $\Theta \succ 0$ requirement due to above.

- [[Interior Point Method or Barrier Method for Convex Optimization]]

>[!important] Definition
>Let $X\sim \mathcal{N}(0, \Sigma)$,  and $\Theta = \Sigma^{-1}$.
>
>The **inverse covariance estimation** is to find the *maximum likelihood estimation* of $\Theta\in \mathcal{S}_{++}^{n}$ given sample $X\in \mathbb{R}^{d}$ by solving the following *convex optimization problem*
>$$
>\begin{align*}
> \min_{\Theta \in \mathbb{R}^{d\times d}} \;&\; \frac{1}{2}\text{tr}\left(X X^T\,\Theta\right) - \frac{1}{2}\log \det \Theta \\[5pt]
> \text{s.t. }\;&\;\Theta = \Theta^{T}
>\end{align*}
>$$

^d75d16

>[!important] 
>The **optimal solution** of *inverse covariance estimation* given a set of $n > d$ samples $\{ X_{i}, i=1\,{,}\ldots{,}\,n \}$ is
>$$
>\Theta = \left(\frac{1}{n}X_{i}X_{i}^{T}\right)^{-1} = \hat{\Sigma}^{-1}
>$$
>which is the *inverse of sample covariance matrix*.

## Explanation

### Proof of Convexity of Log-Det for Positive Definite Matrix

>[!info]
>To see why $g(\Theta)$ is convex,  for any $V\in \mathcal{S}_{++}^{n}$ and  $t\in \mathbb{R}_{+}$ so that $\Theta + tV \succ 0$, define
>$$
>\begin{align*}
>f(t) &:= g(\Theta + t V) = - \frac{1}{2}\log \det|\Theta + tV| \\[5pt]
>&= - \frac{1}{2}\log \det \left(\Theta^{1 / 2} \left(I + t \Theta^{-1 / 2}V\Theta^{-1 / 2}\right) \Theta^{1 / 2}\right) \\[5pt]
>&= - \frac{1}{2}\log \left( \det(\Theta^{1 / 2}) \det \left(I + t \Theta^{-1 / 2}V\Theta^{-1 / 2}\right)  \det (\Theta^{1 / 2})\right) \\[5pt]
>&= - \frac{1}{2}\log\det \left(I + t \Theta^{-1 / 2}V\Theta^{-1 / 2}\right) - \frac{1}{2} \log \det(\Theta)  \\[5pt]
>&= - \frac{1}{2}\log\det \left(I + t \Theta^{-1 / 2}V\Theta^{-1 / 2}\right) + f(0)  \\[5pt]
>&= - \frac{1}{2}\sum_{i=1}^{n} \log \left(1+ t\lambda_{i}\right)+ f(0) 
>\end{align*}
>$$
>where $$\Theta^{-1 / 2}V\Theta^{-1 / 2} = U\text{diag}(\lambda_{1}\,{,}\ldots{,}\,\lambda_{n})U^{T}$$ is the **eigen-decomposition** of $\Theta^{-1 / 2}V\Theta^{-1 / 2} \succ 0$
> 
>Then
>$$
> \frac{d}{dt} f(t) = -\frac{1}{2} \sum_{i=1}^{n} \frac{\lambda_{i}}{1+ t\lambda_{i}}
>$$
>and the **Hessian** is *positive*
>$$
>\frac{d^2}{dt^2} f(t) = \frac{1}{2} \sum_{i=1}^{n} \frac{\lambda_{i}^2}{(1+ t\lambda_{i})^2} > 0.
>$$
>So $g(\Theta)$ is **convex**.

- [[Convex Optimization by Boyd]] pp 74
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Interior Point Method or Barrier Method for Convex Optimization]]

### Negative Precision Matrix as Natural Parameter

![[Natural Parameter and Mean Parameter for Gaussian Distribution#^683466]]


>[!info]
>The *negative precision matrix* is a **natural parameter** of Gaussian distribution.

- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]


## Sparse Inverse Covariance Estimation

- [[Sparse Inverse Covariance Estimation for GGM with Known Structure]]
- [[Graph LASSO and Structured Learning in Gaussian Graphical Model]]

## Related Semidefinite Programming Problems

>[!info]
>Since the log-determinant term requires the eigenvalues of $\Theta$ to be as *large as possible*, we can define a similar problem
>$$
>\begin{align*}
> \min_{u, \Theta \in \mathbb{R}^{d\times d}} \;&\; \frac{1}{2}\text{tr}\left(X X^T\,\Theta\right)  \\[5pt]
> \text{s.t. }\;&\; \Theta \succeq u I 
>\end{align*}
>$$
>- This is a **semidefinite programming (SDP)** problem.

- [[Semidefinite Programming]]

>[!info]
>Another similar **SDP problem** is
>$$
>\begin{align*}
> \min_{u, \Theta \in \mathbb{R}^{d\times d}} \;&\; \frac{1}{2}\text{tr}\left(X X^T\,\Theta\right)  \\[5pt]
> \text{s.t. }\;&\; \left\langle  u_{i}\,,\,\Theta u_{i} \right\rangle = \text{tr}\left(u_{i}u_{i}^{T}\Theta\right) \le c_{i}, \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> &\;\Theta \succeq 0
>\end{align*}
>$$




-----------
##  Recommended Notes and References



- [[Canonical Form of Gaussian Graphical Model]]



- [[Elements of Statistical Learning by Hastie]] pp 631 - 634
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 25, 38, 
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]] pp 265
- [[High Dimensional Probability An Introduction by Vershynin]] pp 100, 130, 237
- [[Convex Optimization by Boyd]] pp 355 - 357


- [[Gaussian Process]]
- [[Gaussian Measure]]
- [[Gaussian Random Function]]


- [[Convex Optimization Problem]]