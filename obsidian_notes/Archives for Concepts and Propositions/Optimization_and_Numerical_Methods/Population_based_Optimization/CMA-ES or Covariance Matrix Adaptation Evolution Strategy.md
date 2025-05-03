---
tags:
  - concept
  - optimization/theory
  - evolutionary_algorithm
  - evolutionary_computation
keywords:
  - cma_es_algorithm
  - covariance_matrix_adaptation_evolutionary_strategy
topics:
  - evolutionary_algorithm
name: CMA-ES or Covariance Matrix Adaptation Evolution Strategy
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: CMA-ES or *Covariance Matrix Adaptation Evolution Strategy*

![[EDA or Estimation of Distribution Algorithm#^ad5721]]


### Algorithm

> [!important] Definition  
> The **Covariance Matrix Adaptation Evolution Strategy (CMA-ES)** is a *stochastic*, *derivative-free* algorithm that adapts a *multivariate Gaussian search distribution* to minimize a real-valued objective $$\mathbb R^n\to\mathbb R.$$
> 
> - _Require_: objective $f:\mathbb R^n\to\mathbb R$.
>     
> - _Require_: 
> 	- initial *mean* $\mathbf m_0\in\mathbb R^n$ 
> 	- initial *step-size* $\sigma_0>0$.
>     
> - _Require_: 
> 	- *population size* $\lambda$, 
> 	- *parent count* $\mu<\lambda$, 
> 	- positive, *normalized weights* $w_1\ge\cdots\ge w_\mu$, $\sum_iw_i=1$.
>     
> - _Require_: 
> 	- *learning rates* $c_\sigma$, $c_c$, $c_1$, $c_\mu$​ 
> 	- *damping* $d_\sigma$.
>- **Initialize** the search distribution: 
>	- $$\mathbf{m}\leftarrow\mathbf{m}_0,\quad \sigma\leftarrow\sigma_0,\quad \mathbf{C}\leftarrow\mathbf{I}_n,\quad \mathbf{p}_\sigma\leftarrow\mathbf{0},\quad \mathbf{p}_c\leftarrow\mathbf{0}.$$
>- While not _converged_:
> 
> 	- **Sample** $\lambda$ *offspring* 
> 		- $$\mathbf y_k\sim\mathcal N(\mathbf0,\mathbf C)$$ 
> 		- $$\mathbf x_k=\mathbf m+\sigma\,\mathbf y_k,\quad k=1,\dots,\lambda.$$
> 	- **Evaluate** and **sort** so that $$f(\mathbf x_{(1)})\le f(\mathbf x_{(2)})\le\cdots\le f(\mathbf x_{(\lambda)}).$$
> 	- **Update mean** $$\mathbf m_{\rm old}\leftarrow\mathbf m,\qquad \mathbf m\leftarrow\sum_{i=1}^\mu w_i\,\mathbf x_{(i)}.$$
> 	- **Evolution path for step-size** $$\mathbf p_\sigma\leftarrow (1-c_\sigma)\,\mathbf p_\sigma +\sqrt{c_\sigma(2-c_\sigma)\,\mu_{\rm eff}}\; \mathbf C^{-\tfrac12}\frac{\mathbf m-\mathbf m_{\rm old}}{\sigma}$$ where $$\mu_{\rm eff}=1/\sum_iw_i^2.$$
> 	- **Evolution path for covariance** $$\mathbf p_c\leftarrow (1-c_c)\,\mathbf p_c +h_\sigma\,\sqrt{c_c(2-c_c)\,\mu_{\rm eff}}\; \frac{\mathbf m-\mathbf m_{\rm old}}{\sigma},$$ with $h_\sigma$​ an indicator of successful step-size control.​
> 	- **Adapt covariance matrix** $$\mathbf C\leftarrow (1 - c_1 - c_\mu)\,\mathbf C + c_1\,\mathbf p_c\,\mathbf p_c^\top + c_\mu\sum_{i=1}^\mu w_i\,\mathbf y_{(i)}\,\mathbf y_{(i)}^\top.$$
> 	- **Adapt step-size** $$\sigma\leftarrow \sigma\, \exp\!\left(\dfrac{c_\sigma}{d_\sigma} \left(\dfrac{\|\mathbf p_\sigma\|}{\mathbb E\|\mathcal N(0,I)\|}-1\right)\right).$$
> - _Return_: the current mean $\mathbf m$ as the approximate minimizer.

- [[EDA or Estimation of Distribution Algorithm]]
- [[Gaussian Random Vector]]
- [[Nelder-Mead Simplex Method]]

## Explanation

>[!quote]
>The **CMA-ES** method of [Han16], which stands for “**covariance matrix adaptation evolution strategy**” is a kind of NES. It is very similar to **CEM** except it updates the parameters in a special way. In particular, instead of computing the new mean and covariance using *unweighted MLE* on the elite set, we attach *weights* to the elite samples based on their *rank*. We then set the new mean to the *weighted MLE* of the elite set. 
>
>The update equations for the covariance are more complex. In particular, “**evolutionary paths**” are also used to accumulate the search directions across successive generations, and these are used to update the covariance. It can be shown that the resulting updates approximate the **natural gradient** of $L(\theta)$ without explicitly modeling the **Fisher information matrix**.

- [[Natural Evolutionary Strategies]]
- [[Cross-Entropy Method for EDA]]
- [[Fisher Metric or Information Metric of Statistical Manifold]]



-----------
##  Recommended Notes and References


- [[EDA or Estimation of Distribution Algorithm]]
- [[Cross-Entropy Method for EDA]]
- [[Gaussian Random Vector]]
- [[Covariance Function of Gaussian Process]]
- [[Positive Semidefinite Transformation]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


- [[Evolutionary Strategies]]
- [[Derivative-Free Optimization]]



- [[BFGS Algorithm]]
- [[Limited Memory BFGS]]
- [[Conjugate Gradient Algorithm Nonlinear]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 298 - 307
- [[Introduction to Evolutionary Computing by Eiben]] 
- Hansen, N. (2016). The CMA evolution strategy: A tutorial. _arXiv preprint arXiv:1604.00772_.
- Wikipedia [CMA-ES](https://en.wikipedia.org/wiki/CMA-ES)