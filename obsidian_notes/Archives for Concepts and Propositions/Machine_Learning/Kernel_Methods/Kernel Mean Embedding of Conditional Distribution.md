---
tags:
  - concept
  - machine_learning/kernel_methods
  - kernel_mean_embedding
  - kme
  - KME
keywords:
  - kernel_mean_embedding_distribution
topics:
  - machine_learning/kernel_methods
name: Kernel Mean Embedding of Conditional Distribution
date of note: 2024-11-11
---

## Concept Definition

>[!important]
>**Name**: Kernel Mean Embedding of Conditional Distribution

![[Kernel Mean Embedding of Distribution#^19844b]]

![[Covariance Operator in Reproducing Kernel Hilbert Space#^39f1ad]]

![[Covariance Operator in Reproducing Kernel Hilbert Space#^52cec0]]


- [[Kernel Mean Embedding of Distribution]]
- [[Covariance Operator in Reproducing Kernel Hilbert Space]]

>[!important] Definition (Feature Map)
>Let $\mathcal{X}\times \mathcal{Y}$ be *product measurable space* and let $\mathcal{H}_{X}$ and $\mathcal{H}_{Y}$ be two *reproducing kernel Hilbert spaces (RKHS)* with *measurable kernels* $K_{X}$ and $K_{Y}$, respectively.
>- Let $(X, Y)$ be random variables from joint distribution $\mathcal{P}_{X,Y}$ on $\mathcal{X}\times \mathcal{Y}$ with *marginal distribution* $\mathcal{P}_{X}$ and $\mathcal{P}_{Y}$, respectively.
>- Assume that $$\mathcal{H}_{X} \subset L^2(\mathcal{X}, \mathcal{P}_{X}), \quad  \mathcal{H}_{Y} \subset L^2(\mathcal{Y}, \mathcal{P}_{Y})$$
>- Denote the map $\varphi$ and $\phi$ as the *canonical feature map* corresponding to kernel $K_{Y}$ and $K_{X}$. That is,
>	- $\varphi: \mathcal{Y}\to \mathcal{H}_{Y}$ is defined as $$\varphi(y) := K_{Y}(y, \cdot)$$
>	- and $\phi: \mathcal{X}\to \mathcal{H}_{X}$ is defined as  $$\phi(x) := K_{X}(x, \cdot)$$
>  
>The **conditional mean embedding** of *conditional distribution* $\mathcal{P}(Y|X)$ is defined as a *bounded linear operator*
>$$
>\mathcal{U}_{Y|X} : \mathcal{H}_{X} \to \mathcal{H}_{Y}
>$$ 
>such that 
>$$
>\mathcal{U}_{Y|x} := \mathbb{E}_{ Y|x }\left[ \varphi(Y)  \,|\,X  = x\right] = \mathcal{U}_{Y|X}\;\phi(x)
>$$
>where $\mathcal{U}_{Y|x}$ is called the **conditional embedding** of $\mathcal{P}(Y|X=x)$.
>- The operator $\mathcal{U}_{Y|X}$ represents the **conditioning operation** that applies to feature map $\phi(x)\in \mathcal{H}_{X}$.
>- Moreover, the **conditional expectation** of any $g\in \mathcal{H}_{Y}$ given $X=x$ can be computed via $$\mathbb{E}_{ Y|x }\left[ g(Y)  \,|\,X  = x\right] = \left\langle  g\,,\, \mathcal{U}_{Y|x}   \right\rangle_{\mathcal{H}_{Y}}, \quad \forall g\in \mathcal{H}_{Y}.$$


- [[Bounded Linear Operator and Norm of Operator]]
- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[Conditional Expectation]]
- [[Conditional Probability]]

>[!important] Definition (Covariance Operator)
>Let $\mathcal{X}\times \mathcal{Y}$ be *product measurable space* and let $\mathcal{H}_{X}$ and $\mathcal{H}_{Y}$ be two *reproducing kernel Hilbert spaces (RKHS)* with *measurable kernels* $K_{X}$ and $K_{Y}$, respectively.
>- Let $(X, Y)$ be random variables from joint distribution $\mathcal{P}_{X,Y}$ on $\mathcal{X}\times \mathcal{Y}$ with *marginal distribution* $\mathcal{P}_{X}$ and $\mathcal{P}_{Y}$, respectively.
>- Assume that $$\mathcal{H}_{X} \subset L^2(\mathcal{X}, \mathcal{P}_{X}), \quad  \mathcal{H}_{Y} \subset L^2(\mathcal{Y}, \mathcal{P}_{Y})$$
>- Denote the map $\varphi$ and $\phi$ as the *canonical feature map* corresponding to kernel $K_{Y}$ and $K_{X}$. That is,
>	- $\varphi: \mathcal{Y}\to \mathcal{H}_{Y}$ is defined as $$\varphi(y) := K_{Y}(y, \cdot)$$
>	- and $\phi: \mathcal{X}\to \mathcal{H}_{X}$ is defined as  $$\phi(x) := K_{X}(x, \cdot)$$
>- Let $\mathcal{K}_{X,X}: \mathcal{H}_{X}\to \mathcal{H}_{X}$ and $\mathcal{K}_{Y,X}: \mathcal{H}_{X}\to \mathcal{H}_{Y}$ be the *covariance operator* on $X$ and *cross-covariance operator* from $X$ to $Y$, respectively. 
>
>Then the **conditional mean embedding** $\mathcal{U}_{Y|X}$ is defined as
>$$
>\mathcal{U}_{Y|X} := \mathcal{K}_{Y,X}\,\mathcal{K}_{X,X}^{-1},
>$$
>and the **conditional mean embedding** $\mathcal{U}_{Y|x}$ is defined as
>$$
>\mathcal{U}_{Y|x} := \mathcal{K}_{Y,X}\,\mathcal{K}_{X,X}^{-1}\;\phi(x).
>$$


![[kernel_mean_embedding_cond_prob.png]]


![[Covariance Operator in Reproducing Kernel Hilbert Space#^5a6926]]

>[!info]
>Note that 
>$$
>\begin{align*}
>\mathcal{K}_{X,X}\;\mathbb{E}_{ Y,X }\left[g(Y)\,|\,X=\cdot\right] = \mathcal{K}_{X,Y}\,g \\[8pt]
> \implies \mathbb{E}_{ Y,X }\left[g(Y)\,|\,X=\cdot\right] = \mathcal{K}_{X,X}^{-1}\mathcal{K}_{X,Y}\,g 
>\end{align*}
>$$
>Since $\mathbb{E}_{ Y,X }\left[g(Y)\,|\,X\right]\in \mathcal{H}_{X}$, we use the reproducing property so that
>$$
>\mathbb{E}_{ Y,X }\left[g(Y)\,|\,X=x\right] = \left\langle  \mathbb{E}_{ Y,X }\left[g(Y)\,|\,X\right]\,,\, \phi(x)   \right\rangle_{\mathcal{H}_{X}}
>$$
>
>Thus take conjugate transport of $\mathcal{K}_{X,X}^{-1}\mathcal{K}_{X,Y}$ on both sides
>$$
>\begin{align*}
>\mathbb{E}_{ Y,X }\left[g(Y)\,|\,X=x\right] &=  \left\langle  \mathbb{E}_{ Y,X }\left[g(Y)\,|\,X\right]\,,\, \phi(x)   \right\rangle_{\mathcal{H}_{X}} \\[8pt]
>  &= \left\langle  \left(\mathcal{K}_{X,X}^{-1}\;\mathcal{K}_{X,Y}\right)\,g  \,,\,\phi(x)     \right\rangle_{\mathcal{H}_{X}} \\[8pt]
>  &= \left\langle  g \,,\,\left(\mathcal{K}_{X,X}^{-1}\;\mathcal{K}_{X,Y}\right)^{*}\,\phi(x)     \right\rangle_{\mathcal{H}_{Y}} \\[8pt]
>  &= \left\langle  g  \,,\,\mathcal{K}_{Y,X}\,\mathcal{K}_{X,X}^{-1}\,\phi(x)     \right\rangle_{\mathcal{H}_{Y}} \\[8pt]
> &= \left\langle  g  \,,\,\mathcal{U}_{Y|x} \right\rangle_{\mathcal{H}_{Y}}
>\end{align*}
>$$
>- The last equality is based on the second definition.
>- We see that the **second definition** *satisfies* the **first definition.**
>- Note that this works when $X$ is *discrete random variables*. For *continuous random variables*, this is an **approximation** since $\mathcal{K}_{X,X}$ may not *invertiable.*


### Empirical Estimator of Conditional Mean Embedding

>[!important] Proposition
>Let $\mathcal{X}\times \mathcal{Y}$ be *product measurable space* and let $\mathcal{H}_{X}$ and $\mathcal{H}_{Y}$ be two *reproducing kernel Hilbert spaces (RKHS)* with *measurable kernels* $K_{X}$ and $K_{Y}$, respectively.
>- Let $(X, Y)$ be random variables from joint distribution $\mathcal{P}_{X,Y}$ on $\mathcal{X}\times \mathcal{Y}$ with *marginal distribution* $\mathcal{P}_{X}$ and $\mathcal{P}_{Y}$, respectively.
>- Denote the map $\varphi$ and $\phi$ as the *canonical feature map* corresponding to kernel $K_{Y}$ and $K_{X}$. That is,
>	- $\varphi: \mathcal{Y}\to \mathcal{H}_{Y}$ is defined as $$\varphi(y) := K_{Y}(y, \cdot)$$
>	- and $\phi: \mathcal{X}\to \mathcal{H}_{X}$ is defined as  $$\phi(x) := K_{X}(x, \cdot)$$	  
>- Let $\{ (x_{1}, y_{1}) \,{,}\ldots{,}\, (x_{n}, y_{n}) \}$ be i.i.d. samples from $\mathcal{P}_{X,Y}$.
>
>The **conditional mean embedding** $\mu_{Y|x}$ can be estimated as
>$$
>\hat{\mu}_{Y|x} = \Phi \left(K + n\,\lambda\,I\right)^{-1}\,k_{x}
>$$
>where 
>- $$\Phi := (\varphi(y_{1}) \,{,}\ldots{,}\,\varphi(y_{n}))^{T}$$
>- $$K := [K_{X}(x_{i}, x_{j})] $$
>- $$k_{x} := (K_{X}(x, x_{1}) \,{,}\ldots{,}\, K_{X}(x, x_{n}))^{T}$$
>  
>We may *reformulated* it as the **empirical kernel mean** $$\hat{\mu}_{Y|x} = \Phi\,\beta :=  \sum_{i=1}^{n}\beta_{i}\,\varphi(y_{i}) \in \mathcal{H}_{Y}$$ with *coefficients* $$\beta := \left(K + n\,\lambda\,I\right)^{-1}\,k_{x}.$$  

>[!info]
>This is the **kernel ridge regression**.

- [[Ridge Regression and L2 Regularization]]





## Explanation

>[!quote]
>Unlike the *marginal distribution* $P(X)$, the *conditional distribution* $P(Y |X)$ captures the **functional relationship** between two random variables, namely $X$ and $Y$. 
>
>Hence, the **conditional mean embedding** extends the *capability* of *kernel mean embedding* to model more **complex dependency** in various applications such as 
>- *dynamical systems* (Song et al. 2009, Boots et al. 2013), 
>- *Markov decision processes* and *reinforcement learning* (Grünewälder et al. 2012, Nishiyama et al. 2012), 
>- *latent variable model* (Song et al. 2010b; 2011a;b), 
>- *kernel Bayes rule* (Fukumizu et al. 2011), and 
>- *causal discovery* (Janzing et al. 2011, Sgouritsa et al. 2013, Chen et al. 2014).
>  
>-- [[Kernel Mean Embedding of Distributions by Muandet]] pp 70  

- [[State Space Models and Nonlinear Dynamic System]]
- [[Extended Kalman Filter]]
- [[Latent Variable Models]]
- [[Gaussian Process Latent Variable Model]]
- [[Bayesian Network on Directed Acyclic Graph]]

>[!quote]
>One should also keep in mind that, **unlike** the *marginal mean embedding*, the operator $$\mathcal{K}_{Y,X}\,\mathcal{K}_{X,X}^{-1}$$ only acts as an **approximation** of the **conditional mean embedding** $$\mathcal{U}_{Y|X}$$ in the *continuous domain* 
>- because the assumption that for all $g \in \mathcal{H}_{Y}$, the *conditional expectation* $$\mathbb{E}_{ Y|X }\left[ g(Y)  \,|\,X  = x\right]$$ is an element of $\mathcal{H}_{X}$ may **not hold in general**.
>  
>-- [[Kernel Mean Embedding of Distributions by Muandet]] pp 74  




-----------
##  Recommended Notes and References


- [[Measure Space and Countably Additive Measure]]
- [[RKHS of Gaussian Process]]
- [[RKHS of Gaussian Random Function]]
- [[RKHS of Gaussian Random Function in Hilbert Space]]
- [[Gaussian Process]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 58 - 59,  891
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 70 - 94
- [[Density Estimation for Statistics and Data Analysis by Silverman]]
- Wikipedia [Kernel_embedding_of_distributions](https://en.wikipedia.org/wiki/Kernel_embedding_of_distributions)