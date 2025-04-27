---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - GGM
  - gaussian_graphical_model
  - sum_product
  - canonical_form
  - gaussian_markov_random_field
  - Gaussian_MRF
  - MRF
  - markov_random_field
keywords:
  - gaussian_graphical_model
  - probabilistic_graphical_model
  - sum_product
  - canonical_form
  - gaussian_markov_network
  - gaussian_markov_random_field
topics:
  - probabilistic_graphical_model
name: Gaussian Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Gaussian Graphical Model or *Gaussian Markov Random Field*

>[!quote]
>the key difference between inference in the continuous and the discrete case is that the factors can no longer be represented as tables. Naively, we might think that we can represent **factors as Gaussians**, but this is *not the case*. The reason is that **linear Gaussian CPDs are generally not Gaussians**, but are rather a conditional distribution. Thus, we need to find a more *general representation* for factors, that accommodates both Gaussian distributions and linear Gaussian models, as well as any combination of these models that might arise during the course of inference.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 609

### Canonical Form

- [[Canonical Form of Gaussian Graphical Model]]

### Gaussian Graphical Model

>[!important] Definition
>Given an *undirected graph* $G$, a **Gaussian graphical model (GGM)** or **Gausian Markov Random Field (GMRF)** is a multivariate Gaussian distribution $$\mathcal{P}(x; \mu, \Theta^{-1}) = \exp \left(-\frac{1}{2}\left(x - \mu\right)^T\,\Theta\,(x - \mu) - \frac{n}{2} \log(2\pi) + \frac{1}{2} \log \det(\Theta) \right)$$
>such that the **precision matrix** (the **inverse covariance matrix**) $\Theta = [\Theta_{i,j}]$ satisfies the condition
>$$
>\Theta_{i,j} = 0 \quad \text{ for all } ij \not\in E(G)
>$$
>- Note that for Gaussian distribution, there exists one-to-one correspondence between the *local conditional independence assertion* and *zeros in inverse covariance matrix* $$X_{i} \perp X_{j} \;|\; X_{\mathcal{X} - X_{i} - X_{j}} \iff \Theta_{i,j}  = 0$$
>
>- The **minimal $I$-map** of $G$ has simple expression
>$$
>\begin{align*}
>\mathcal{I}(G) &:= \left\{ X_{i} \perp X_{j} \;|\; X_{\mathcal{X} - X_{i} - X_{j}} , \; ij\in E(G) \right\}\\
>&= \left\{ \Theta_{i,j}  = 0, \; ij\in E(G) \right\} \\
>&= \mathcal{I}(\mathcal{P})
>\end{align*}
>$$
>
>- The graph $G$ is called the **concentration graph**. 
>- Since the distribution is **positive**, we can construct graph $G$ that is a **unique minimal $I$-map** for $\mathcal{P}$.

^44a106

- [[Independence in Gaussian Distribution]]
- [[I-Map and Independence Assertion]]
- [[Separation in Markov Network]]
- [[Markov Network on Undirected Graph]]
- [[Positive Distribution]]
- [[Minimal I-Map]]
- [[Probabilistic Graphical Models by Koller]] pp 247


>[!important] Definition
>For multivariate Gaussian distribution, the entry $(i,j)$ of inverse covariance matrix $\Theta$ corresponds to the **partial correlation** between $X_{i}$ and $X_{j}$ given a set of *controlling variables* $\left\{ X_{k}, k \not\in \left\{ i,j \right\} \right\}$.

- [[Linear Regression]]
- [[Partial Correlation]]

>[!important] Definition
>Any Gaussian distribution can be represented as a *pairwise Markov network* with *quadratic node and edge potentials*. This Markov network is generally called a **Gaussian Markov random field** (**GMRF**).



### Information Form of Gaussian Network

>[!important] Definition
>We can reformulate a multivariate Gaussian p.d.f. $\mathcal{N}(\mu, \Sigma)$ in an **information form**
>$$
>\begin{align*}
> \mathcal{N}(x; K, h) &= \exp \left( -\frac{1}{2} \left\langle Kx , x \right\rangle + \left\langle h, x \right\rangle + g \right) 
>\end{align*}
>$$
>where 
>$$
>\begin{align*}
> K &= \Sigma^{-1}\\
> h &= \Sigma^{-1}\mu = K\mu\\
> g &= - \frac{1}{2}\left\langle \Sigma^{-1}\mu , \mu \right\rangle - \log \left( (2\pi)^{n / 2}\, |\det(\Sigma)|^{1 / 2}\right)
>\end{align*}
>$$
>- $K$ is **precision matrix**, or **information matrix**, or **inverse covariance matrix** of Gaussian distribution. $$K \succ 0.$$
>- $h = K\mu$ is called the **potential vector**.
>- $(K, h)$ forms **canonical parameters** for Gaussian distribution for *sufficient statistics* $X, XX^T.$
>- $g$ is the *log-partition function.*
>

^162c43

- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]
- [[Probabilistic Graphical Models by Koller]] pp 248

## Explanation

>[!quote]
>The message passing inference methods have largely revolved around the use of the **Gaussian distribution**. The easiest case is when the distribution is, in fact, a multivariate Gaussian. In this case, many of the challenges described before disappear. In particular, the intermediate factors in a Gaussian network can be described *compactly* using a simple parametric representation called the **canonical form**. This representation is closed under the basic operations using in inference: *factor product*, *factor division*, *factor reduction*, and *marginalization*. Thus, we can define a set of simple data structures that allow the inference process to be performed. Moreover, the *integration operation* required by marginalization is always well defined, and it is guaranteed to produce a *finite* integral under certain conditions; when it is well defined, it has a simple analytical solution. 
>
>As a consequence, a fairly straightforward modification of the discrete sum-product algorithms (whether variable elimination or clique tree) gives rise to an **exact inference algorithm** for **Gaussian networks**.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 607

^777073

>[!quote]
>**Gaussian graphical models** are the *continuous counter-piece* to **Ising models**. Like Ising models, Gaussian graphical models are **quadratic exponential families.** These families only model the *pairwise interactions between nodes*, i.e., interactions are only on the edges of the underlying graph $G$. But nevertheless, Ising models and Gaussian graphical models are extremely flexible models; in fact, they can capture any pairwise correlation structure that can be constructed for binary or for continuous data.
>
>-- Uhler, C. (2017). Gaussian graphical models: An algebraic and geometric perspective. _arXiv preprint arXiv:1707.04345_.

>[!quote]
>Thus, we can view the **information matrix** $J$ for a *Gaussian density* $p$ as precisely capturing the **pairwise Markov independencies** in a Markov network representing $p$. Because a Gaussian density is a *positive distribution*, we can now use theorem 4.5 to construct a Markov network that is a **unique minimal $I$-map** for $p$: As stated in this theorem, the construction simply introduces an edge between $X_i$ and $X_j$ whenever $(X_{i} \perp X_{j} \,|\, \mathcal{X} − \{X_{i}, X_{j}\})$ does *not hold* in $p$. But this latter condition holds precisely when $J_{i,j} \neq 0$. Thus, we can view the information matrix as directly defining a **minimal $I$-map Markov network** for $p$, whereby nonzero entities correspond to edges in the network.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 251

- [[Minimal I-Map]]
- [[Markov Network on Undirected Graph]]

## Marginal Distribution 

>[!important] Proposition
>Let $(X, Y)$ be *joint normal distribution* defind as 
>$$
>p(x, y) = \mathcal{N}\left( (x,y);\; \mu,\, \Sigma \right)
>$$
>where
>$$
>\begin{align*}
> \Sigma &= \left[\begin{array}{cc}
>\Sigma_{x x} & \Sigma_{x y} \\
>\Sigma_{y x} & \Sigma_{y y}
>\end{array}\right] \\[5pt]
> \mu&= \left[\begin{array}{c}
>\mu_{x}  \\
>\mu_{y} 
>\end{array}\right].
>\end{align*}
>$$
>
>Then the **marginal distribution** over $Y$ is 
>$$
>p(y) = \mathcal{N}(y;\, \mu_{y},\, \Sigma_{y}).
>$$

>[!quote]
>To **marginalize** a Gaussian over a subset of the variables,  one essentially needs to compute their **pairwise covariances**, which is precisely generating the distribution in its covariance form.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 250

- [[Marginal and Conditional Distribution of Gaussian]]

## Independence in Gaussian Model

- [[Independence in Gaussian Distribution]]


## Exact Inference of Gaussian Graphical Model

- [[Gaussian Belief Propagation]]





-----------
##  Recommended Notes and References


- [[Inverse Covariance Estimation]]
- [[Gaussian Process]]
- [[Gaussian Bayesian Network]]
- [[Gaussian Random Vector]]


- [[Markov Network on Undirected Graph]]
- [[Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 247 - 258, 608
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- Uhler, C. (2017). Gaussian graphical models: An algebraic and geometric perspective. _arXiv preprint arXiv:1707.04345_.