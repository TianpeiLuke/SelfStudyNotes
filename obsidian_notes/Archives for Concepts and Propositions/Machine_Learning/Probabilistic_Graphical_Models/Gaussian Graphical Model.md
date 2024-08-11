---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
keywords:
  - gaussian_graphical_model
  - probabilistic_graphical_model
  - sum_product
  - canonical_form
topics:
  - probabilistic_graphical_model
name: Gaussian Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Gaussian Graphical Model

>[!quote]
>the key difference between inference in the continuous and the discrete case is that the factors can no longer be represented as tables. Naively, we might think that we can represent **factors as Gaussians**, but this is *not the case*. The reason is that **linear Gaussian CPDs are generally not Gaussians**, but are rather a conditional distribution. Thus, we need to find a more *general representation* for factors, that accommodates both Gaussian distributions and linear Gaussian models, as well as any combination of these models that might arise during the course of inference.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 609

- [[Tabular Representation and Function Approximation RL]]

### Canonical Form

- [[Canonical Form of Gaussian Graphical Model]]

### Gaussian Graphical Model

>[!important] Definition
>Given a graph $G$, a Gaussian graphical model is a **multivariate Gaussian distribution** $$\mathcal{P}(x; \mu, \Theta) = \frac{1}{\sqrt{(2\pi)^{n}|\det(\Sigma)| }}\exp \left(-\frac{1}{2}\left(x - \mu\right)^T\,\Theta\,(x - \mu)\right)$$
>such that the *joint precision matrix* $\Theta = [\Theta_{i,j}]$ satisfies the condition
>$$
>\Theta_{i,j} = \left\{ 
>\begin{array}{cc}
> 0 & (i,j) \not\in E(G)\\ 
> \theta_{i,j} \neq 0 & (i,j) \in E(G)
>\end{array}
>\right. 
>$$
>Note that for Gaussian distribution, there exists one-to-one correspondence between the *conditional independence assertion* and *zeros in inverse covariance matrix* $$X_{i} \perp X_{j} \;|\; X_{\mathcal{X} - X_{i} - X_{j}} \iff \Theta_{i,j}  = 0$$
>
>In other word, the **$I$-map** of $G$ has simple expression
>$$
>\begin{align*}
>\mathcal{I}(G) &:= \left\{ X_{i} \perp X_{j} \;|\; X_{\mathcal{X} - X_{i} - X_{j}} , \; ij\in E(G) \right\}\\
>&= \left\{ \Theta_{i,j}  = 0, \; ij\in E(G) \right\} \\
>&= \mathcal{I}(\mathcal{P})
>\end{align*}
>$$

- [[I-Map and Independence Assertion]]
- [[Separation in Markov Network]]
- [[D-Separation in Bayesian Network]]


## Explanation

>[!quote]
>The message passing inference methods have largely revolved around the use of the **Gaussian distribution**. The easiest case is when the distribution is, in fact, a multivariate Gaussian. In this case, many of the challenges described before disappear. In particular, the intermediate factors in a Gaussian network can be described *compactly* using a simple parametric representation called the **canonical form**. This representation is closed under the basic operations using in inference: *factor product*, *factor division*, *factor reduction*, and *marginalization*. Thus, we can define a set of simple data structures that allow the inference process to be performed. Moreover, the *integration operation* required by marginalization is always well defined, and it is guaranteed to produce a *finite* integral under certain conditions; when it is well defined, it has a simple analytical solution. 
>
>As a consequence, a fairly straightforward modification of the discrete sum-product algorithms (whether variable elimination or clique tree) gives rise to an **exact inference algorithm** for **Gaussian networks**.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 607

^777073

## Exact Inference of Gaussian Graphical Model







-----------
##  Recommended Notes and References


- [[Inverse Covariance Estimation]]
- [[Gaussian Process]]
- [[Gaussian Measure]]
- [[Gaussian Random Function]]
- [[Gaussian Random Vector]]




- [[Probabilistic Graphical Models by Koller]] pp 608
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]