---
tags:
  - concept
  - statistics/estimation
  - math/probability
  - machine_learning/models
  - math/information_theory
  - math/information_geometry
  - math/convex_analysis
keywords:
  - exponential_family
  - kl_divergence
  - maximum_likelihood_estimation
  - maximum_entropy_learning
  - fisher_information
  - information_geometry
topics:
  - probability
  - machine_learning_models
  - statistics/estimation
  - information_geometry
  - information_theory
  - convex_analysis
name: Exponential Family of Distributions
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Exponential Family of Distributions

![[Parametric Models#^408b6c]]

>[!important] Definition
>A *parametric family* $\left\{ \mathcal{P}_{\theta}: \theta \in \Theta \right\}$ dominated by a *$\sigma$-finite measure* $\nu$ on $(\Omega, \mathscr{F})$ is called an **exponential family** *if and only if* its probability density function has the form
>$$
> f_{\theta}(\omega) := \frac{d\mathcal{P}_{\theta}}{d\nu}(\omega) = \exp\left( \left\langle  \eta(\theta)\,,\, T(\omega)   \right\rangle - A(\theta) \right)\;h(\omega), \quad \omega \in \Omega. 
>$$
>where 
>- $T: \Omega \to \mathbb{R}^d$ is a *random $d$-vector* with a fixed positive integer $d$,  
>- $\eta: \Theta \to \mathbb{R}^d$ is a *function*,  
>- $h: \Omega \to [0,\infty)$ is a *nonnegative Borel function* on $(\Omega, \mathscr{F})$, and 
>- $$
>A(\theta) = \log \left(\int_{\Omega}\,\exp\left( \left\langle  \eta(\theta)\,,\, T(\omega)   \right\rangle \right)\;h(\omega)\, d\nu(\omega) \right).
>$$
>The function $Z(\theta) := \exp \left(A(\theta)\right)$ is called a **partition function** or **cumulant function** or **normalization factor.**
>- Define the **domain** of *partition function* $A(\theta)$ as $$\mathcal{D} := \left\{ \theta \in \Theta: A(\theta) < \infty \right\}. $$ 

^b32aa5

- [[Parametric Models]]
- [[Probability Density Function of Random Variable]]
- [[Borel Measure]]
- [[Measurable Function]]
- [[Sufficient Statistics]]

## Explanation


## Canonical Form of Exponential Family

>[!important] Definition
>In an exponential family, consider the *reparameterization* $$\eta = \eta(\theta),$$ and the density function
>$$
>f_{\eta}(\omega) = \exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle - A(\eta) \right)\;h(\omega), \quad \omega \in \Omega. 
>$$
>where the log-partition function becomes
>$$
>A(\eta) = \log \left(\int_{\Omega}\,\exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle \right)\;h(\omega)\, d\nu(\omega) \right).
>$$
>
>This form is called **the canonical form** or **the natural parameterization**  of *exponential family*
>- The new *parameter* $\eta$ is called the **natural parameter**.
>- The new *parameter space* $$\mathcal{D} := \left\{ \eta(\theta): A(\theta) < \infty, \; \theta \in \Theta  \right\} \subset \mathbb{R}^d$$ is called the **natural parameter space**.
>- An exponential family in *canonical form* is called a **natural exponential family**.

^6d86a1


## Minimal Representation

>[!important] Definition
>Let $\{ f_{\theta}: \theta\in \Theta \}$ be an exponential family with sufficient statistics $T: \mathcal{X} \to \mathbb{R}^d$, i.e. the density function with respect to $\sigma$-finite measure $\nu$ is 
>$$
>f_{\theta}(x) = \exp\left( \left\langle  \eta(\theta)\,,\, T(x)   \right\rangle - A(\theta) \right)\;h(x), \quad x \in \mathcal{X}. 
>$$
>
>The representation $f_{\theta}(x)$ is called **minimal representation** if there **does not exist** a nonzero vector $w \in \mathbb{R}^d$ such that the *linear combination*
>$$
>\begin{align*}
>\left\langle w\,,\, T(x) \right\rangle := \sum_{i=1}^{d} w^{i}\; T^i(x) = \text{const.} \quad \nu\text{-a.s.}
>\end{align*}
>$$
>In other word, there is a **unique parameter** $\theta \in \Theta$ associated with each distribution, or, the map $$\theta \mapsto \mathcal{P}_{\theta}$$ is **one-to-one**.

^232ce4

- [[Injective Function]]

## Overcomplete Representation

>[!important] Definition
>Let $\{ f_{\theta}: \theta\in \Theta \}$ be an exponential family with sufficient statistics $T: \mathcal{X} \to \mathbb{R}^d$, i.e. the density function with respect to $\sigma$-finite measure $\nu$ is 
>$$
>f_{\theta}(x) = \exp\left( \left\langle  \eta(\theta)\,,\, T(x)   \right\rangle - A(\theta) \right)\;h(x), \quad x \in \mathcal{X}. 
>$$
>
>The representation $f_{\theta}(x)$ is called **overcomplete representation** if there **exist** a nonzero vector $w \in \mathbb{R}^d$ such that the *linear combination*
>$$
>\begin{align*}
>\left\langle w\,,\, T(x) \right\rangle := \sum_{i=1}^{d} w^{i}\; T^i(x) = \text{const.} \quad \nu\text{-a.s.}
>\end{align*}
>$$
>In other word, there exists an **entire affine subset** of parameter vectors $\theta$, each associated with *the same distribution*.



## Log-Partition Function

- [[Log-Partition Function of Exponential Family]]


## Score Function

>[!important]
>The **score function** of natural exponential family 
>$$
>\begin{align*}
>\frac{\partial}{ \partial \eta }\log f_{\eta} &= \frac{\partial}{ \partial \eta }\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle - A(\eta) \right)\\
>&=  T(\omega) - \frac{\partial}{ \partial \eta }A(\eta)\\[5pt]
>&=  T(\omega) -  \mathbb{E}_{ f_{\theta} }\left[ T \right]
\end{align*}
>$$
>where
>$$
>A(\eta) = \log \left(\int_{\Omega}\,\exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle \right)\;h(\omega)\, d\nu(\omega) \right).
>$$
>
>We can see that the **gradient of log-likelihood function** (i.e. the score function) depends on 
>- the **sufficient statistic** $T$
>- and the **gradient** of **log-partition function** $A(\eta)$, which is the **expectation** of $T$
>
>The interpretation of the **score function** of exponential family is that it equals to 
>$$
>\text{sample mean } - \text{population mean }
>$$

^c95a01

- [[Likelihood Function]]

## Mean Parameterization of Exponential Family

>[!important] Definition
>Let $X$ be sample from population $\mathcal{P}$ with p.d.f. $f$ with respect to dominating *$\sigma$-finite measure* $\nu$. Let $T(X) \in \mathbb{R}^d$ be **sufficient statistic** of parameter $\theta \in \Theta \subset \mathbb{R}^d$ associated with $\mathcal{P}$.
>
>The **mean parameter** $\mu = (\mu^1 \,{,}\ldots{,}\, \mu^d) \in \mathbb{R}^d$ *associated with* $T$ is defined by the equation
>$$
>\mu^{i} =  \mathbb{E}_{ \mathcal{P} }\left[ T^{i}(X) \right] = \int_{\mathcal{X}}\,T^{i}(x)\,f(x)\,d\nu(x), \quad i=1 \,{,}\ldots{,}\,d.
>$$
>
>Define the set 
>$$
>\mathcal{M} := \left\{ \mu \in \mathbb{R}^d:  \exists \mathcal{P} \text{ such that }  \mu = \mathbb{E}_{\mathcal{P}}\left[ T(X) \right] \right\}. 
>$$
>as the set of all **realizable mean parameters**.

^056e11

![[Exponential Family and Convex Duality#^14b84c]]

- [[Exponential Family and Convex Duality]]

![[Log-Partition Function of Exponential Family#^db3b2e]]

- [[Log-Partition Function of Exponential Family]]

>[!important] Definition
>Let $X \in \mathcal{X}$ be sample from a **minimal exponential family** $\{f_{\eta}: \eta \in \mathcal{D}  \}$. 
>$$
>f_{\eta}(x) = \exp\left( \left\langle  \eta\,,\, T(x)   \right\rangle - A(\eta) \right)\;h(x), \quad x \in \mathcal{X}. 
>$$
>
>Let $\mathcal{M}$ be the set of all **realizable mean parameters** associated with statistic $T: \mathcal{X} \to \mathbb{R}^d$.
>$$
>\mathcal{M} := \left\{ \mu \in \mathbb{R}^d:  \exists \mathcal{P} \text{ such that }  \mu = \mathbb{E}_{\mathcal{P}}\left[ T(X) \right] \right\}. 
>$$
>
>For each $\mu\in \text{int}(\mathcal{M})$,  there exists some $\eta := \eta(\mu)\in \mathcal{D}$ such that
>$$
>  \mu = \mathbb{E}_{ f_{\eta} }\left[ T(X) \right].
>$$ 
>In other word, there exists an *equivalent parameterization* of the exponential family, called the **mean parameterization** such that the p.d.f. has  the form
>$$
>f_{\mu}(x) = \exp\left( \left\langle  \eta(\mu)\,,\, T(x)   \right\rangle - A(\eta(\mu)) \right)\;h(x).
>$$
>where $\mu \in \mathcal{M}.$




## Maximum Likelihood Estimation and Convex Optimization

- [[Maximum Likelihood Estimation of Exponential Family]]

## Maximum Entropy Learning as Dual Formulation

- [[Maximum Entropy Learning of Exponential Family]]

## Log-Concave Likelihood Function

![[Log-Concave Measure#^81a226]]


>[!important] Proposition
>The *likelihood function* of an **exponential family** is **logarithmically concave** 

- [[Likelihood Function]]
- [[Log-Concave and Log-Convex Function]]

>[!info]
>Assume that the p.d.f. of measure in exponential family is
>$$
>f_{\eta}(x) = \exp\left( \left\langle  \eta\,,\, T(x)   \right\rangle - A(\eta) \right)\;, \quad x \in \mathcal{X}. 
>$$
>
>Then the **likelihood function** $\ell(\eta; x ) = \exp(G(\eta; x))$
>$$
>G(\eta; x) := \left\langle  \eta\,,\, T(x)   \right\rangle - A(\eta)
>$$
>is an **concave** in $\eta$. Thus the likelihood function is **log-concave**.





## Convex Duality 

- [[Exponential Family and Convex Duality]]

## Graphical Model 

- [[Exponential Family as Probabilistic Graphical Model]]

## Fisher Information of Exponential Family

>[!info]
>Under **natural parameterization**, the **Fisher information** can be computed as
>$$
>\begin{align*}
> I(\eta) &:= \mathbb{E}_{ f_{\eta} }\left[ \frac{\partial}{ \partial \eta }\log f_{\eta}\; \left( \frac{\partial}{ \partial \eta }\log f_{\eta} \right)^{T}   \right] \\[10pt]
> &= \int_{\Omega}\;\frac{\partial}{ \partial \eta }\log f_{\eta}\; \left( \frac{\partial}{ \partial \eta }\log f_{\eta} \right)^{T}\;f_{\eta}\; d\nu \\
> &= \int_{\Omega}\; \left(T(\omega) - \mathbb{E}_{ f_{\theta} }\left[ T \right]\right) \left(T(\omega) - \mathbb{E}_{ f_{\theta} }\left[ T \right] \right)^T \;f_{\eta}\; d\nu\\
> &=   \mathbb{E}_{ f_{\theta} }\left[ \left( T - \mathbb{E}_{ f_{\theta} }\left[ T \right] \right)\;\left( T - \mathbb{E}_{ f_{\theta} }\left[ T \right] \right)^T \right] \\[10pt]
> &= \text{Cov}(T, T)
>\end{align*}
>$$

^c37891

![[Fisher Information for Exponential Family#^713d66]]


- [[Fisher Information]]
- [[Fisher Information for Exponential Family]]

## Cramér-Rao Lower Bound and UMVUE

>[!important]
>The **Cramér-Rao lower bound** is attained if and only if $f_{\theta}$ is in an **exponential family**.
>
>In other word,  $T(X)$ is an **uniformly minimal variance unbiased estimator (UMVUE)** with $$ \mathbb{E}_{\mathcal{P}_{\eta}}\left[ T(X) \right] = \mu(\eta).$$
>
>As a consequence of Fisher information formula, any **linear function** of  $T$ is also **UMVUE**

- [[Mathematical Statistics by Shao]] pp 171
- [[Uniformly Minimum Variance Unbiased Estimation]]
- [[Cramér-Rao Lower Bound]]


## Information Geometry of Exponential Family

- [[Exponential Family as Affine Subspace in Statistical Manifold]]






-----------
##  Recommended Notes and References


- [[Likelihood Function]]
- [[Sufficient Statistics]]
- [[Minimal Sufficient Statistics]]
- [[Fisher Information]]


- [[Generalized Linear Models]]


- [[Maximum Likelihood Estimation]]




- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 96 - 99
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Methods of Information Geometry by Amari]]
- [[Probabilistic Graphical Models by Koller]] pp 261 - 284
- [[Convex Analysis by Rockafellar]]
- [[Convex Optimization by Boyd]]