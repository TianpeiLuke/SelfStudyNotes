---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - machine_learning/dimensionality_reduction
keywords:
  - principle_component_analysis
  - probabilistic_principle_component_analysis
topics:
  - dimensionality_reduction
  - machine_learning_models
  - unsupervised_models
name: Probabilistic Principle Component Analysis
date of note: 2024-09-04
---

## Concept Definition

>[!important]
>**Name**: Probabilistic Principle Component Analysis

>[!important] Definition
>The **probabilistic principle component analysis (PPCA)** considers the following *factor analysis* model
>$$
>\left\{
>\begin{align*} p(h) &= \mathcal{N}(h \;|\; 0\,;\, I)\\[5pt] p(x|h) &=\mathcal{N}(x\;|\; Vh\,;\,  \sigma^2I)
>\end{align*}
>\right.
>$$ 
>where
>- $h\in \mathbb{R}^{s}$ are *latent variables*, and $x\in \mathbb{R}^{d}$ are *observations*.
>- $V = [v_{1} \,{,}\ldots{,}\,v_{s}]\in \mathbb{R}^{d\times s}$ has *orthogonal columns*, i.e. $$\left\langle v_{i} , v_{j} \right\rangle =0, \quad i\neq j$$
>
>The *marginal distribution* of observation (i.e. **evidence**) is given by 
>$$
>p(x) = \mathcal{N}(x\;|\;0 \,;\, VV^{T} + \sigma^2I)
>$$

- [[Principle Component Analysis]]
- [[Factor Analysis]]

### Maximum Likelihood Estimation

>[!important] Definition
>The **log-likelihood function** for PPCA is given by
>$$
>\begin{align*}
>&\log p(x; V, \sigma) \\[5pt]
>&= -\frac{nd}{2}\log(2\pi) - \frac{n}{2}\log\det\,\lvert VV^{T} + \sigma^2I \rvert  - \frac{1}{2}\sum_{i=1}^{n}\left\langle x_{i} , \left(  VV^{T} + \sigma^2I  \right)^{-1} x_{i} \right\rangle \\[5pt]
>&= - \frac{n}{2}\left[ d\log(2\pi) + \log\det\,\lvert VV^{T} + \sigma^2I \rvert + \left\langle \left(  VV^{T} + \sigma^2I  \right)^{-1} ,  S\right\rangle_{tr} \right] 
>\end{align*}
>$$
>where the sample covariance matrix is
>$$
>S = \frac{1}{n}\sum_{i=1}^{n}x_{i}\,x_{i}^{T}
>$$

- [[Maximum Likelihood Estimation]]
- [[Gaussian Random Vector]]

>[!info]
>We can find the MLE of $V$ by solving the score equation
>$$
>\begin{align*}
> \nabla_{V} \log p(x; V,\sigma) &= 0 \\[5pt]
> \nabla_{V} \log\det\,\lvert VV^{T} + \sigma^2I \rvert + \nabla_{V}\left\langle \left(  VV^{T} + \sigma^2I  \right)^{-1} ,  S\right\rangle_{tr}   &= 0 \\[5pt]
>\end{align*}
>$$

>[!info]
>By **matrix inversion formula**
>$$
>\begin{align*}
>\frac{1}{\sigma^2} \left( I + \frac{1}{\sigma^2} V\,V^{T} \right)^{-1} &= \frac{1}{\sigma^2}\left(  I - \frac{1}{\sigma^2}V\,\left(I + \frac{1}{\sigma^2}V^{T}V\right)^{-1}\,V^{T} \right) \\[5pt]
>&= \frac{1}{\sigma^2}\left(  I - V\,\text{diag}\left( \frac{1}{\sigma^2+ \lVert v_{1} \rVert^2 } \,{,}\ldots{,}\, \frac{1}{\sigma^2+ \lVert v_{n} \rVert^2 }\right)\,V^{T} \right)
>\end{align*}
>$$

- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]


>[!important] Proposition
>Let 
>$$
>S = U\,\Lambda\,U^{T}
>$$
>be the *eigen-decomposition* of sample covariance $S$ 
>- $$\Lambda = \text{diag}(\lambda_{1} \,{,}\ldots{,}\,\lambda_{d}), \quad \text{ where }  \lambda_{1} \ge \lambda_{2} \,{\ge}\ldots{\ge}\,\lambda_{d} \ge 0$$ be *eigenvalues* of $S$
>- $$U = [u_{1} \,{,}\ldots{,}\,u_{d}] \in \mathcal{O}(d)$$ is the orthogonal matrix, whose columns $u_{i}$ are *eigenvectors* of $S$ corresponding to eigenvalue $\lambda_{i}$ 
>
>Then the **maximum likelihood estimation** of $V$ for **PPCA** must satisfy
>$$
>\widehat{V}_{mle} = U_{\lceil s \rceil}\left( \Lambda_{ \lceil s \rceil } - \sigma^2 I\right)^{1/2} Q
>$$
>where 
>- $\Lambda_{ \lceil s \rceil }$ and  $U_{\lceil s \rceil}$ denote the top $s$ largest eigenvalues and their eigenvectors $$U_{\lceil s \rceil} = [u_{1} \,{,}\ldots{,}\,u_{s}], \quad \Lambda_{ \lceil s \rceil } = \text{diag}(\lambda_{1} \,{,}\ldots{,}\,\lambda_{s})$$
>- $Q\in \mathcal{O}(s)$ is an *arbitrary orthogonal matrix* . 
>  
>Moreover, the MLE for **observation variance**  is given by 
>$$
>\sigma_{mle}^2 = \frac{1}{d - s}\sum_{i=s+1}^{d}\lambda_{i}
>$$


>[!info]
>From the MLE solution, we see that the optimal mapping $V$ is **invariant to the orthogonal transformation** within $s$-dimensional subspace.
>
>That is, $$\hat{V}_{mle} \in Gr(d, s)$$ identifies an optimal **$s$-dimensional subspace** in $\mathbb{R}^{d}$. In other word, the maximum likelihood estimation is solving an *optimization* on **Grassmann manifold** 



## Explanation

>[!quote]
>The *advantage* of **PPCA** over **factor analysis** is that the MLE has a *closed form solution*, as we show in Section 28.3.2.2. The advantage of PPCA over **non-probabilistic PCA** is that the model defines a *proper likelihood function*, which makes it easier to extend in various ways e.g., by creating mixtures of PPCA models.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 934




-----------
##  Recommended Notes and References



- [[Factor Analysis]]
- [[Latent Variable Models]]

- [[Principle Component Analysis]]
- [[Gaussian Random Vector]]
- [[Marginal and Conditional Distribution of Gaussian]]
- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 934 - 936
- [[Elements of Statistical Learning by Hastie]]
- Tipping, M. E., & Bishop, C. M. (1999). Probabilistic principal component analysis. _Journal of the Royal Statistical Society Series B: Statistical Methodology_, _61_(3), 611-622.