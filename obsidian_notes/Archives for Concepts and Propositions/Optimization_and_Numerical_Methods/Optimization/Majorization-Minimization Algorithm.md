---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - majorization_minimization
topics:
  - optimization/algorithm
  - optimization/theory
name: Majorization-Minimization Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Majorization-Minimization Algorithm

![[Generalized Proximal Method#^8944af]]


>[!important] Definition
>Consider the optimization task
>$$
>\min_{x\in \mathcal{X}} f(x)
>$$
>where $f: \mathbb{R}^{\infty} \to (-\infty,\infty]$ is continuous function.
>
>The  **majorization-minization (MM) algorithm** is an alternative formulation of the *generalized proximal algorithm*. 
>
>Specifically, at each iteration $k$, it solves the following problem:
>$$
>x_{k+1} \in \arg\min_{x\in \mathbb{R}^{n}}M_{k}(x, x_{k})
>$$ 
>where $M_{k}:\mathbb{R}^{n}\times \mathbb{R}^{n} \to (-\infty,+\infty]$ is called a **minorized funciton** or a **surrogate function** which satisfies the following conditions for all $k=1\,{,}\ldots{,}\,$
>- $$M_{k}(x_{k}, x_{k}) = f(x_{k})$$
>- $$M_{k}(x, x_{k}) \ge f(x),\quad \forall x\in \mathbb{R}^{n}$$

^918339

- [[Surrogate Loss Minimization]]




>[!important] Definition
>Define the **regularization term** 
>$$
>D_{k}(x, y) := M_{k}(x, y) - M_{k}(x, x)
>$$
>for any $x,y\in \mathbb{R}^{n}.$
>
>The **majorization-minimization algorithm** is equivalent to the **generalized proximal algorithm** as
>$$
>\begin{align*}
>x_{k} \in \arg\min_{x\in \mathbb{R}^{n}}& M_{k}(x, x_{k}) \\[5pt]
>&=    M_{k}(x, x) + M_{k}(x, x_{k}) - M_{k}(x, x)\\[5pt]
>&= f(x) + D_{k}(x, x_{k})
>\end{align*}
>$$


- [[Generalized Proximal Method]]
- [[Bregman Divergence Minimization]]
- [[Entropy Minimization Algorithm]]

### Construction of Minorized Surrogate Function

#### First Order Taylor Expansion and Bregman Divergence Minimization

![[Bregman Divergence#^b31c31]]


![[Bregman Divergence Minimization#^745bcc]]

>[!important] 
>If the objective function can be decomposed into two terms $$f(x) = f_{0}(x) - g(x)$$ where $g$ is a **differentiable convex function**, which satisfies the following first-order inequality 
>$$
>g(x) \ge g(y) + \left\langle \nabla g(y) , x - y \right\rangle
>$$
>Thus if we define the **minorizing surrogate function**
>$$
>M_{k}(x, y) := f_{0}(x) - g(y) - \left\langle \nabla g(y) , x - y \right\rangle
>$$
>we have that
>- $$M_{k}(x_{k}, x_{k}) = f(x_{k})$$
>- $$M_{k}(x, x_{k})  \ge f_{0}(x) - g(x) = f(x), \quad \forall x$$
>  
>The **divergence** defined by
>$$
>\begin{align}
>M_{k}(x, y) &:= f_{0}(x) - g(y) - \left\langle \nabla g(y) , x - y \right\rangle \\[5pt]
>&= f(x) + g(x) - g(y) - \left\langle \nabla g(y) , x - y \right\rangle \\[5pt]
>&= f(x) + \mathbb{D}_{g}\left( x \left\|\right. y \right)
>\end{align}
>$$  
>Thus the **MM algorithm** is equivalent to
>$$
>\begin{align}
>x_{k+1} \in \arg\min_{x}&\left\{f(x)  + \mathbb{D}_{g}\left( x\left\|\right. x_{k}\right) \right\}
>\end{align}
>$$
>which is the **Bregman divergence minimization.**
>- Note that for fixed $y$, the surrogate function $M_{k}(x, y)$ is **linear** in $x$.

^aad1a0

- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]
- [[Convex Function]]
- [[Bregman Divergence]]
- [[Bregman Divergence Minimization]]
- [[Bregman Projection]]

#### Convexity and Jensen's inequality

![[Jensen Inequality#^df6fae]]

- [[Jensen Inequality]]

#### Cauchy-Schwartz Inequality

![[Cauchy-Schwartz Inequality#^11b65d]]

- [[Cauchy-Schwartz Inequality]]


#### Schur Complement

![[Schur Complement and Inversion of Block Matrix#^ad7e0f]]

>[!important]
>Suppose that $m, n \in \mathbb{N}$, and a matrix $M \in \mathbb{R}^{(m+n) \times (m+n)}$ can be **partitioned** into four *blocks* as
>$$
>\begin{align*}
> M &= \left[\begin{array}{cc}
> A & B\\
> B^{T}& C
>\end{array}\right] 
>\end{align*}
>$$
>where $A \in \mathbb{R}^{m\times m}$, $B\in \mathbb{R}^{m\times n}$, $C \in \mathbb{R}^{n\times n}$
>
>Assume that $C \succ\, 0$, thus $$M \succeq\,0 \quad \iff \quad M / C \succeq\, 0$$
>which indicates that
>$$
> M / C := A - B\,C^{-1}\,B^{T} \succeq\, 0 \quad \iff \quad A \succeq B\,C^{-1}\,B^{T}.
>$$


- [[Schur Complement and Inversion of Block Matrix]]


## Explanation

>[!info]
>The conditions
>- $$M_{k}(x_{k}, x_{k}) = f(x_{k})$$
>- $$M_{k}(x, x_{k}) \ge f(x),\quad \forall x\in \mathbb{R}^{n}$$
>- $$x_{k+1} \in \arg\min_{x} M_{k}(x, x_{k})$$
>
>lead to the conclusion that 
>$$
>f(x_{k+1}) \le M_{k}(x_{k+1}, x_{k}) \le M_{k}(x_{k}, x_{k}) = f(x_{k})
>$$
>Thus the *values* of objective functions for **MM algorithm** are **monotonically decreasing**
>$$f(x_{1})\, \ge f(x_{2})\,{\ge}\ldots{\ge}\,f(x_{k})\, \ge f(x_{k+1}) \ge \ldots$$



## Examples

### Expectation-Maximization

![[Expectation-Maximization Algorithm#^0c7718]]

>[!example] 
>Define the **majorization function** as
>$$
>M_{k}(\theta, \mu) := -Q(\theta; \mu) :=  \mathbb{E}_{ z\sim p }\left[-\ell(\theta; x, z)\;|\; x, \mu  \right]
>$$
>
>Thus the corresponding **majorization-minimization** optimizes the following problem for each iteration $k$: 
>$$
>\begin{align*}
>\theta_{k+1} \in \arg\min_{\theta\in \Theta} &\; M_{k}(\theta, \theta_{k})\\[5pt]
>&= \mathbb{E}_{ z\sim p }\left[-\ell(\theta; x, z)\;|\; x, \theta_{k}  \right] 
>\end{align*}
>$$
>which is the **expectation-maximization** algorithm.

- [[Expectation-Maximization Algorithm]]

### Difference of Convex Program

![[Difference of Convex Optimization and Concave-Convex Procedure#^f02812]]

![[Difference of Convex Optimization and Concave-Convex Procedure#^6d9a69]]

- [[Difference of Convex Optimization and Concave-Convex Procedure]]



### Inverse Covariance Estimation



- [[Inverse Covariance Estimation]]
- [[Sparse Inverse Covariance Estimation for GGM with Known Structure]]
- [[Graph LASSO and Structured Learning in Gaussian Graphical Model]]


### Iteratively Reweighted Least Square

#### LASSO and Sparse Linear Regression

>[!example]
>Consider the regression with *sparisity-inducing norm*
>$$
>\min_{x} \lVert Ax - b \rVert_{2}^2 + \lambda  \lVert x \rVert_{p}^{p}
>$$
>where  $p\in (0, 1]$.
>- Note that for **concave function** $\lvert x \rvert^{p}$ with $p\in (0, 1]$ $$\lvert x \rvert^{p} \le \frac{p}{2} \lvert x_{k} \rvert^{p-2}\,x^{2}$$
>- Thus $$\lVert x \rVert_{p}^{p} = \sum_{i=1}^{d}\lvert x_{i} \rvert^{p} \le  \sum_{i=1}^{d}w_{i}^{(t)}x_{i}^2 = \lVert D_{t}\,x \rVert_{2}^2 $$ where $$D_{t} = \text{diag}(\sqrt{w_{1}^{(t)}}\,{,}\ldots{,}\,\sqrt{w_{d}^{(t)}}), \quad w_{i}^{t} =  \frac{p}{2} \lvert x_{i}^{(k)} \rvert^{p-2}$$
>
>Thus the **surrogate function** is 
>$$
>M_{k}(x, x_{k}) = \lVert Ax - b \rVert_{2}^2 + \lVert D_{t}\,x \rVert_{2}^2 
>$$
>and the **MM algorithm** becomes an **iterative reweighted least square**
>$$
>\begin{align*}
>\min_{x}\; &\lVert Ax - b \rVert_{2}^2 + \lVert D_{t}\,x \rVert_{2}^2  
>\end{align*}
>$$

- [[LASSO and Sparsity-Induced Least Square]]


#### Least Absolute Deviations

>[!example]
>The **least  absolute deviations (LAD) problem** can be represented in compact form as
>$$
>\min_{\beta \in \mathbb{R}^{d+1}} \lVert y- X\,\beta \rVert_{p}^{p} 
>$$
>where $X\in \mathbb{R}^{m\times (d+1)}$ are the *design matrix*.
>
>We can define the surrogate function as
>$$
>M(\beta, \beta_{k}) = \sum_{i=1}^{m}w_{i}^{(t)}\left( y_{i} - X_{i,:}\beta \right)^{2}
>$$
>where $$w_{i}^{(t)} := \lvert y_{i} - X_{i,:}\beta_{t}  \rvert^{p-2} $$
>
>Then the corresponding *majorization-minimization algorithm* can be interpreted as the **iteratively reweighed least square** 
>$$
>\beta_{k+1} \in \arg\min_{\beta}\;\left\{ \sum_{i=1}^{m}w_{i}^{(t)}\left( y_{i} - X_{i,:}\beta \right)^{2} \right\} 
>$$

- [[Logistic Regression Solution via Iterative Reweighted Least Square]]
- [[Least Absolute Deviations Solution via Iterative Re-weighted Least Square]]







-----------
##  Recommended Notes and References




- [[Convex Optimization Algorithms by Bertsekas]] pp 392
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 281 - 283
- [[sunMajorizationMinimizationAlgorithmsSignal2017]]; Sun, Y., Babu, P., & Palomar, D. P. (2017). Majorization-Minimization Algorithms in Signal Processing, Communications, and Machine Learning. _IEEE Transactions on Signal Processing_, _65_(3), 794–816. IEEE Transactions on Signal Processing. [https://doi.org/10.1109/TSP.2016.2601299](https://doi.org/10.1109/TSP.2016.2601299); 
- Wikipedia [MM_algorithm](https://en.wikipedia.org/wiki/MM_algorithm)