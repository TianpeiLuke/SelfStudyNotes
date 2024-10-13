---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/representation
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/theory
keywords:
  - mean_field_approximation
  - gaussian_graphical_model
topics:
  - probabilistic_graphical_model
name: Mean Field Approximation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Mean Field Approximation for Gaussian Markov Random Field

![[Mean Field Approximation for Exponential Family#^9d3014]]

- [[Mean Field Approximation for Exponential Family]]
- [[Mean Field Approximation for PGM]]

![[Gaussian Graphical Model#^44a106]]

>[!important] Definition
>Let $\mathcal{G}$ be an undirected graph, and $\mathcal{N}(x; \mu,E)$ be a *Gaussian graphical model (GGM)*  under the *mean parameterization* i.e. $$\mathcal{N}(x; \mu, E) = \exp \left(-\frac{1}{2}  \left(x - \mu\right)^{T}\left(E - \mu\,\mu^{T}\right)^{-1}\,\left(x - \mu\right)  + A^{*}(\eta, E) + \frac{d}{2} \right)$$
>where
>- $$\mu = \mathbb{E}_{ p }\left[  X \right], \quad E = \mathbb{E}_{ p }\left[  X\,X^{T} \right] = \Sigma + \mu\,\mu^{T}$$
>- and the *dual function of log-partition*, i.e. *negative entropy* parameterized by mean parameters is given by  $$A^{*}(\mu, E) := -H(\eta, E) = -\frac{d}{2}\left\{ \log(2\pi) + 1 \right\} - \frac{1}{2} \log \det \left\lvert E - \eta\,\eta^{T}  \right\rvert $$
>- The *canonical parameterization* of this model is denoted as $\mathcal{N}(x; \theta, \Theta)$.
>  
>Under the **naive mean field assumption** with $\mathcal{F} = (\mathcal{V}, \emptyset)$, the set of *tractable mean parameters* is of the form $$\mathcal{M}_{\mathcal{F}}(\mathcal{G}) = \left\{ (\mu, E) \in \mathbb{R}^{d} \times \mathcal{S}_{++}^{d}\;|\; E - \mu\mu^{T} = \text{diag}(E - \mu \mu^{T}) \succeq 0 \right\} $$  
>- This is because the native mean field assumes *all variables are independent*, which is equivalent to say that *covariance matrix* under naive mean field is *diagonal*  $$\Sigma =  E - \mu\mu^{T} = \text{diag}(\Sigma).$$ 
>
>The **restriction** of dual function on $\mathcal{M}_{\mathcal{F}}(\mathcal{G})$ is of form 
>$$
>\begin{align*}
>A_{\mathcal{F}}^{*}(\mu, E) &= -\frac{d}{2}\left\{ \log(2\pi) + 1 \right\} - \frac{1}{2} \log \det \left\lvert \text{diag}\left(E - \eta\,\eta^{T} \right) \right\rvert \\[5pt]
>&= -\frac{d}{2}\left\{ \log(2\pi) + 1 \right\} - \frac{1}{2} \sum_{i=1}^{d}\log \left(E_{ii} - \mu_{i}^2\right)
>\end{align*}
>$$
>
>Thus, the **native mean field approximation** of *Gaussian graphical model* $\mathcal{N}(x; \theta, \Theta)$ is obtained by solving the following optimization
>$$
>\begin{align*}
> \max_{\mu, E}\;&\; \left\langle  \theta\,,\,\mu \right\rangle + \frac{1}{2}\text{tr}\left(\Theta\,E\right) -A_{\mathcal{F}}^{*}(\mu, E) \\[5pt]
> \text{s.t.}\;&\; E_{ii} - \mu_{i}^2 > 0,\, \quad i=1\,{,}\ldots{,}\,d \\[5pt]
> &\; E_{i,j} = \mu_{i}\mu_{j},\, \quad i\neq j=1\,{,}\ldots{,}\,d
>\end{align*}
>$$
>where $(\theta, \Theta)$ are *canonical parameters* of target distribution $\mathcal{N}(x; \theta, \Theta).$
>- Note that the inequality constraint $E_{ii} - \mu_{i}^2 > 0$ is the natural domain for log function. The term $$- \frac{1}{2} \sum_{i=1}^{d}\log \left(E_{ii} - \mu_{i}^2\right)$$ is actually the **logarithmic barrier function.** Thus we can drop the inequality constraint.


- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]
- [[Gaussian Graphical Model]]
- [[Diagonal Matrix and Block Diagonal Matrix]]
- [[Logarithmic Barrier Function and Central Path for Interior Point Methods]]

### Solution to Mean Field Approximation

>[!important] Definition
>Note that we can include both the inequality constraint and the equality constraint into the objective function. 
>
>The **native mean field approximation** of *Gaussian graphical model* $\mathcal{N}(x; \theta, \Theta)$ is obtained by solving the following optimization
>$$
>\begin{align*}
> \max_{\mu_{i}, E_{ii}}\;&\; \sum_{i=1}^{d}\theta_{i}\,\mu_{i} + \frac{1}{2}\sum_{i\neq j=1}^{d}\Theta_{i,j}\mu_{i}\mu_{j} + \frac{1}{2}\sum_{i=1}^{d}\Theta_{ii}E_{ii} + \frac{1}{2} \sum_{i=1}^{d}\log \left(E_{ii} - \mu_{i}^2\right) 
>\end{align*}
>$$
>where $(\theta, \Theta)$ are *canonical parameters* of target distribution $\mathcal{N}(x; \theta, \Theta).$
>- Note that $$\Theta_{i,j} = 0, \quad \forall (i,j)\not\in \mathcal{E}.$$
>- This is a **quadratic optimization problem** with **log-barrier term.** $$\max_{\mu, E} \left\langle  \theta\,,\,  \mu  \right\rangle + \frac{1}{2}\mu^{T}(\Theta - \text{diag}(\Theta))\mu + \text{tr}(\Theta\,\text{diag}(E)) - \phi(\text{diag}(E - \mu \mu^{T}))$$
>
>The *necessary condition* for optimal solution of above problem satisfies the following equations:
>$$
>\left\{
>\begin{align*}
> \frac{1}{(E_{ii} - \mu_{i}^2)} &= - \Theta_{ii}, \quad i=1\,{,}\ldots{,}\,d\\[5pt]
> \frac{\mu_{i}}{(E_{ii} - \mu_{i}^2)} &= \theta_{i} + \sum_{j\in N(i)}  \Theta_{ij}\mu_{j}, \quad i=1\,{,}\ldots{,}\,d\
>\end{align*}
>\right.
>$$

^a12fee

- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[KKT Matrix and KKT System for Optimization with Equality Constraints]]
- [[Quadratic Programming]]
- [[Barrier Method for Convex Optimization]]


>[!info]
>Consider the *objective* 
>$$
>L(\mu, E) := \sum_{i=1}^{d}\theta_{i}\,\mu_{i} + \frac{1}{2}\sum_{i\neq j=1}^{d}\Theta_{i,j}\mu_{i}\mu_{j} + \frac{1}{2}\sum_{i=1}^{d}\Theta_{ii}E_{ii} + \frac{1}{2} \sum_{i=1}^{d}\log \left(E_{ii} - \mu_{i}^2\right) 
>$$
>Take the derivative with respect to both $\mu$ and $E_{ii}$
>$$
>\begin{align*}
> \nabla_{\mu_{i}} L &= \theta_{i} + \Theta_{i,j}\mu_{j}\,\mathbb{1}\{ j\in N(i) \} + \frac{1}{2} \frac{1}{E_{ii} - \mu_{i}^2}(-2\mu_{i}) = 0, \quad i=1\,{,}\ldots{,}\,d\\[5pt]
> \nabla_{E_{ii}} L &= \frac{1}{2}\Theta_{ii} + \frac{1}{2} \frac{1}{E_{ii} - \mu_{i}^2} = 0, \quad i=1\,{,}\ldots{,}\,d\\[5pt]
>\end{align*}
>$$

### Naive Mean Field Approximation Algorithms

>[!important] Definition
>The **native mean field approximation** of *Gaussian graphical model* $\mathcal{N}(x; \theta, \Theta)$ is obtained by solving the following optimization
>$$
>\begin{align*}
> \max_{\{\mu_{i}, E_{ii}\}_{i=1}^{d}}\;&\; \sum_{i=1}^{d}\theta_{i}\,\mu_{i} + \frac{1}{2}\sum_{i\neq j=1}^{d}\Theta_{i,j}\mu_{i}\mu_{j} + \frac{1}{2}\sum_{i=1}^{d}\Theta_{ii}E_{ii} + \frac{1}{2} \sum_{i=1}^{d}\log \left(E_{ii} - \mu_{i}^2\right) 
>\end{align*}
>$$
>where $(\theta, \Theta)$ are *canonical parameters* of target distribution $\mathcal{N}(x; \theta, \Theta).$ And $$\Theta_{i,j} = 0, \quad \forall (i,j)\not\in \mathcal{E}.$$
>
>The **Mean Field approximation algorithm** solves above problem using *coordinate ascent* as follow:
>- *Require*:  *Canonical parameters* $\theta\in \mathbb{R}^{d}$ and $\Theta\in \mathcal{S}_{++}^d$ for the target Gaussian graphical model
>- *Require*: *Initial mean parameters*  $\mu_{i}^{0}$ and $E_{ii}^{0}$ for all $i=1\,{,}\ldots{,}\,d$
>- For $t=1\,{,}\ldots{,}\,$ until convergence:
>	- For $i=1\,{,}\ldots{,}\,d$:
>		- Update **mean parameter** $$\mu_{i}^{(t)} = - \frac{1}{\Theta_{ii}}\left(\theta_{t} + \sum_{j\in N(i), j<i}\Theta_{i,j}\,\mu_{j}^{(t)} + \sum_{j\in N(i),\, j > i}\Theta_{i,j}\,\mu_{j}^{(t-1)}\right)$$
>- When converges:
>	- Update the **second moment parameter** $$E_{ii} = -\frac{1}{\Theta_{ii}} + \mu_{i}^2.$$
>- Return the *mean parameters of variational distribution* $(\mu_{i}, E_{ii})_{i=1}^{d}$.

- [[Gauss-Seidel Iteration for Sparse Linear System]]
- [[Jacobi Iteration for Sparse Linear System]]



## Explanation

>[!important]
>The **naive mean field approximation algorithm** of Gaussian graphical model is the same as the **Gauss-Seidel iteration**
>
>In essence, it solves $\mu$ via the **sparse normal system**
>$$
>  \Theta \mu = - \theta 
>$$
>- Note that this fits the mapping between mean and canonical parameters for the target distribution $P_{\Phi}$. That is, for the  $P_{\Phi} := \mathcal{N}(\theta, \Theta)$, the **true mean parameter** should be given by $$\mu^{P} = -\Theta^{-1}\theta$$
>- In other word, the **mean field approximation** $\mu^{Q}$ *guarantee* to converge to the **true mean** $\mu^{P}$ i.e.  $$\mu^{Q} \rightarrow \mu^{P} := \Theta^{-1}\theta$$ if $\Theta$ is *strictly diagonally dominant*

^b5abb1

- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]
- [[Newton Method]]
- [[Normal Equations and Newton System of Equations]]




-----------
##  Recommended Notes and References

- [[Structured Variational Approximation]]
- [[Information Projection and Moment Projection]]

- [[Kullback-Leibler Divergence]]
- [[Maximum Entropy Learning]]

- [[Mean Field Approximation for PGM]]
- [[Gaussian Graphical Model]]
- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]
- [[Gaussian Belief Propagation]]


- [[Gauss-Seidel Iteration for Sparse Linear System]]
- [[Jacobi Iteration for Sparse Linear System]]
- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]


- [[Probabilistic Graphical Models by Koller]] pp 449 - 469
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 135 - 136
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
