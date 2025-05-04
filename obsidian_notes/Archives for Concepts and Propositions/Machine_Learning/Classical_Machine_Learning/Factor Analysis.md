---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - machine_learning/latent_variable_model
  - machine_learning/dimensionality_reduction
  - factor_analysis
  - FA
keywords:
  - factor_analysis
topics:
  - unsupervised_models
  - machine_learning_models
  - probabilistic_graphical_model
name: Factor Analysis
date of note: 2024-09-04
---

## Concept Definition

>[!important]
>**Name**: Factor Analysis

![[Latent Variable Models#^68d885]]

- [[Latent Variable Models]]

>[!important] Definition
>The **factor analysis (FA)** is a special case of *latent variable model* where both *prior* of hidden variable and the *likelihood function* of observations are *Gaussian*.
>
>$$
>\left\{
>\begin{align*}
> p(z) &= \mathcal{N}(z\,|\, \mu_{0}\,,\, \Sigma_{0}) \\[5pt]
> p(x\,|\,z, \theta) &= \mathcal{N}(x\,|\, Wz + \mu, \Psi)
>\end{align*}
>\right.
>$$
>where $z\in \mathbb{R}^{s}$, $x\in \mathbb{R}^{d}$. 
>- The matrix  $W \in \mathbb{R}^{d\times s}$ is called the **factor loading matrix**.
>- The covariance $\Psi$ on likelihood is usually assumed to be **diagonal** $$\Psi = \text{diag}\left\{ \psi_{1} \,{,}\ldots{,}\, \psi_{d} \right\}$$


![[factor_analysis_dpgm.png]]

## Explanation

>[!info]
>Since Gaussian prior is a **conjugate prior** for Gaussian likelihood, the *factor analysis* models have **closed form** solutions for 
>-  **marginal distribution**   $$p(x; \theta)$$
>- **posterior distribution**   $$p(z\,|\, x)$$

- [[Conjugate Prior Distribution for Bayesian Inference]]

## Marginal Likelihood Function

>[!important] 
>We can compute the **marginal likelihood** in closed form
>$$
>\begin{align*}
> p(x; \theta) &= \int \mathcal{N}(x\;|\;Wz + \mu, \Psi)\, \mathcal{N}\left( z\;|\; \mu_{0}, \Sigma_{0} \right)\,dz\\[5pt]
> &= \mathcal{N}\left( x\;|\; W\mu_{0} + \mu\,, \, \Psi + W\,\Sigma_{0}\,W^{T} \right)
>\end{align*}
>$$
>where the mean and covariance are
>$$
>\mu_{x} := W\mu_{0} + \mu, \quad \Sigma_{x} :=  \Psi + W\,\Sigma_{0}\,W^{T} := \Psi + \widehat{W}\,\widehat{W}^{T}.
>$$
>- Denote $$\widehat{W} = W\,\Sigma_{0}^{-1/2}.$$ 
>	- This corresponds to the process of **whitening**. 
>	- With whitening in the data, we can assume, without loss of generality, that $\Sigma_{0} = I$.
>- We see that $$\Sigma_{x} :=  \Psi + \widehat{W}\,\widehat{W}^{T}$$ is a **low rank decomposition.**
>

^a9ed6d

- [[Marginal and Conditional Distribution of Gaussian]]

>[!important] 
>The **marginal log-likelihood function** is 
>$$
>\begin{align*}
>&\log p(x; \theta) \\[5pt]
>&= -\frac{nd}{2}\log(2\pi) - \frac{n}{2}\log\det\,\lvert \Psi + W\,\Sigma_{0}\,W^{T}  \rvert  - \frac{1}{2}\sum_{i=1}^{n}\left\langle x_{i} , \left(  \Psi + W\,\Sigma_{0}\,W^{T}  \right)^{-1} x_{i} \right\rangle \\[5pt]
>&= - \frac{n}{2}\left[ d\log(2\pi) + \log\det\,\lvert \Psi + W\,\Sigma_{0}\,W^{T} \rvert + \left\langle \left(  \Psi + W\,\Sigma_{0}\,W^{T}  \right)^{-1} ,  S\right\rangle_{tr} \right] 
>\end{align*}
>$$
>where the sample covariance matrix is
>$$
>S = \frac{1}{n}\sum_{i=1}^{n}x_{i}\,x_{i}^{T}.
>$$
>- Note that by *Schur complement*, and *matrix determinant lemma* $$\log \det \left(  \Psi + W\,\Sigma_{0}\,W^{T}  \right) = \log \det(\Psi) + \log\det \left( \Sigma_{0}^{-1} +  W^{T}\Psi^{-1}W \right)$$ 
>	- The right hand side  takes $O(s^3 + d)$ to compute.
>- The **Mahalanobis distance** can also be computed using the Schur complement $$\begin{align*} &\left\langle \left(  \Psi + W\,\Sigma_{0}\,W^{T}  \right)^{-1} ,  S\right\rangle_{tr} \\[5pt] &= \left\langle  \Psi^{-1} ,  S\right\rangle_{tr} - \left\langle \Psi^{-1}W\left(\Sigma_{0}^{-1} +  W^{T}\Psi^{-1}W \right)^{-1}W^{T}\Psi^{-1},  S\right\rangle_{tr} \end{align*}$$ 
>	- which takes $O(s^3 + sd)$ to compute

^cb4966

- [[Schur Complement and Inversion of Block Matrix]]

## Posterior Distribution

>[!important]
>The **posterior distribution** can be computed in closed form as well.
>$$
>p(z \,|\, x) = \mathcal{N}(z\;|\; \mu_{z|x}, \Sigma_{z|x})
>$$
>where
>$$
>\begin{align*}
> \mu_{z|x} &= \mu_{0} + W^{T}\,\left( \Psi + W\,\Sigma_{0}\,W^{T}  \right)^{-1}\left(x - \mu \right) \\[5pt]
> \Sigma_{z|x} &= \Sigma_{0} - W^{T}\,\left( \Psi + W\,\Sigma_{0}\,W^{T}  \right)^{-1}\,W
>\end{align*}
>$$
>
>Applying the **Sherman-Morrison-Woodury Matrix inversion** gives us 
>$$
>\left( \Psi + W\,\Sigma_{0}\,W^{T}  \right)^{-1} = \Psi^{-1} - \Psi^{-1}W\left(\Sigma_{0}^{-1} +  W^{T}\Psi^{-1}W \right)^{-1}W^{T}\Psi^{-1}   
>$$
>- Note that $$\Psi + W\,\Sigma_{0}\,W^{T} \in S_{+}(d) \subset \mathbb{R}^{d\times d}$$ but $$\Sigma_{0}^{-1} +  W^{T}\Psi^{-1}W \in S_{+}(s) \subset   \mathbb{R}^{s \times s}$$

- [[Marginal and Conditional Distribution of Gaussian]]
- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]


## Inference on Factor Analysis Model


>[!info]
>The inference task for parameter $\theta$ can be done with *maximum likelihood estimation* on *marginal likelihood*
>$$
>\theta^{*} = \arg\max_{\theta} \log\,p(x; \theta)
>$$
>Since the marginal log-likelihood (evidence) has close form solution, the objective function can be derived directly.

- [[Maximum Likelihood Estimation]]

>[!info]
>Alternatively, we can use **expectation maximization (EM)** to maximize the **ELBO**, i.e. the *lower bound* of the marginal likelihood
>$$
>\begin{align*}
>\theta &=  \max_{\theta} \mathcal{L}(q, \theta; x)\\[5pt]
>&:= \mathbb{E}_{ q }\left[ \log \left(\frac{p_{\theta}(x, Z)}{q(Z)}\right) \right] \\[5pt]
>&= \mathbb{E}_{q }\left[ \log \left(\frac{p(x | Z, \theta)\,p(Z)}{q(Z)}\right) \right]\\[5pt]
>&\le \log p(x; \theta)
>\end{align*}
>$$

- [[Evidence Lower Bound]]
- [[Expectation-Maximization Algorithm]]
- [[Expectation-Maximization Algorithm for Exponential Family]]


## Unidentifiability of the Parameters

>[!important] Definition
>The parameters of a FA model are **unidentifiable**. 
>
>In fact, the estimate of $W$ is equivalent up to an orthogonal transformation $R$
>$$
>W \simeq WR
>$$
>- In other word, the **factor analysis model** is **symmetry** to orthogonal transformation. 
>
>- Geometrically, multiplying $W$ by an orthogonal matrix is like rotating $z$ before generating $x$; but since $z$ is drawn from an **isotropic Gaussian**, this makes no difference to the likelihood.
>  
>Consequently, we *cannot uniquely identify* $W$, and therefore *cannot uniquely identify the latent factors*, either. This is called the “**factor rotations problem**”.  

- [[Three Components of Intelligence System]]

>[!important]
>- We can say that FA models identify the **range space** of linear map from $W$, $\mathcal{R}(W)$,  **not a unique matrix representation** of $W$. 
>
>- So FA models can be seen as learning on Grassmann manifold $$W \in Gr(d, s)$$

>[!quote]
>To break this symmetry, several solutions can be used, 
>- **Forcing $W$ to have orthogonal columns.**  
>	- see [[Principal Component Analysis]] and [[Probabilistic Principal Component Analysis]]
>- **Forcing W to be lower triangular.**
>	- One way to resolve *permutation unidentifiability*, which is popular in the Bayesian community, is to ensure that the *first visible feature* is only generated by *the first latent factor*; 
>	- The disadvantage of this method is that the first $L$ visible variables, known as the **founder variables**, affect the interpretation of the latent factors, and so must be chosen carefully.
>- **Sparsity promoting priors on the weights.** 
>	- see $L_{1}$ regularization, [[LASSO and Sparsity-Induced Least Square]]
>- **Choosing an informative rotation matrix**. 
>	- There are a variety of heuristic methods that try to find rotation matrices $R$ which can be used to modify $W$ (and hence the latent factors) so as to try to increase the *interpretability*, typically by encouraging them to be (approximately) sparse.
>- **Use of non-Gaussian priors for the latent factors**.
>	- e.g. [[Independent Component Analysis]]
>	- e.g. [[Nonnegative Matrix Factorization or NMF]]
>	  
>	  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 934	  

## Nonlinear Factor Analysis

>[!info]
>We can replace the linear decoder to be nonlinear decoder $f(w; \theta)$ in likelihood
>$$
>p(x|z) = \mathcal{N}(x\,|\, f(z; \theta), \sigma^2I)
>$$
>The resulting model is an *autoencoder*, which is seen as the **nonlinear factor analysis** model. 

- [[Auto-Encoder and Stochastic Auto-Encoder]]

## Gaussian Mixtures

- [[Gaussian Mixture Models]]





-----------
##  Recommended Notes and References


- [[Gaussian Mixture Models]]
- [[Probabilistic Principal Component Analysis]]
- [[Canonical Correlation Analysis]]
- [[Principal Component Analysis]]
- [[Latent Variable Models]]

- [[Linear Dynamic System]]

- [[Expectation-Maximization Algorithm]]
- [[Expectation-Maximization Algorithm for Exponential Family]]


- [[Elements of Statistical Learning by Hastie]] pp 678
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 930 - 933
- [[Deep Learning Foundations and Concepts by Bishop]] pp 513, 520 - 521
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 89, 107