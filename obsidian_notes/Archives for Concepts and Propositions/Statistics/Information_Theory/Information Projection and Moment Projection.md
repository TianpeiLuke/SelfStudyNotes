---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - probabilistic_graphical_models/theory
  - probabilistic_graphical_models/algorithm
keywords:
  - information_projection
  - moment_projection
  - maximum_entropy_learning
  - moment_matching
  - alpha_connection
  - e_connection
  - m_connection
topics:
  - information_theory
  - information_geometry
name: Information Projection and Moment Projection
date of note: 2024-07-21
---

## Concept Definition

>[!important]
>**Name**: Information Projection and Moment Projection

>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be *measurable space*, and $\mathcal{P}, \mathcal{Q}$ are two *probability measures* in $\mathscr{F}$. Let $\mathcal{M}_{+}(\mathscr{F})$ be a space of *probability measures* on $\mathscr{F}$.
>
>Suppose that $\mathcal{P}$ *dominates* all measures in $\mathcal{M}_{+}(\mathscr{F})$, i.e.
>$$
>\mathcal{M}_{+}(\mathscr{F}) := \left\{ \mathcal{Q} \text{ probabiliy measure on }\mathscr{F}: \mathcal{Q} \ll \mathcal{P} \right\} 
>$$
>
> Define the **$I$-projection** or **information projection** of $\mathcal{P}$ onto $\mathcal{M}_{+}(\mathscr{F})$ as the *minimizer* of the following optimization problem $$\mathcal{Q}^{I} := \arg\min_{\mathcal{Q}\in \mathcal{M}_{+}(\mathscr{F})}\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P} \right)$$


- [[Kullback-Leibler Divergence]]
- [[Space of Bounded Signed Measures]]
- [[Radon-Nikodym Derivative]]
- [[Absolute Continuity for Measures]]

>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be *measurable space*, and $\mathcal{P}, \mathcal{Q}$ are two *probability measures* in $\mathscr{F}$. Let $\mathcal{M}_{+}(\mathscr{F})$ be a space of *probability measures* on $\mathscr{F}$.
>
>Suppose that $\mathcal{P}$ *is dominated by* any measures in $\mathcal{M}_{+}(\mathscr{F})$, i.e.
>$$
>\mathcal{M}_{+}(\mathscr{F}) := \left\{ \mathcal{Q} \text{ probabiliy measure on }\mathscr{F}: \mathcal{Q} \gg \mathcal{P} \right\} 
>$$
>
> Define the **$M$-projection** or **moment projection** of $\mathcal{P}$ onto $\mathcal{M}_{+}(\mathscr{F})$ as the *minimizer* of the following optimization problem $$\mathcal{Q}^{M} := \arg\min_{\mathcal{Q}\in \mathcal{M}_{+}(\mathscr{F})}\mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{Q} \right)$$



## Explanation

>[!info]
>The [[Maximum Entropy Learning]] can be seen as the **information projection** of *prior* $\mathcal{P}_{0}$ onto the constraint set $\mathcal{M}$ with *expectation matching constraints*.
>$$
>\min_{\mathcal{Q}\in \mathcal{M}_{+}(\mathscr{F})}\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P} \right)
>$$
>
>The [[Maximum Likelihood Estimation]] can be seen as the **moment projection** of *empirical data distribution* onto the *parametric family of models*
>
>$$
>\min_{\mathcal{P}_{\theta}\in \mathscr{P}_{\Theta}}\mathbb{KL}\left( \hat{\mathcal{P}}_{n} \left\|\right. \mathcal{P}_{\theta}  \right)
>$$

- [[Empirical Process and Empirical Measure]]

## Comparison

>[!quote]
>The $M$-projection attempts to **give all assignments** reasonably **high probability**,  whereas the $I$-projection attempts to **focus on high-probability assignments** in $\mathcal{P}$ while maintaining a **reasonable entropy**. In this case, this behavior results in a uniform distribution for the $M$-projection, whereas the $I$-projection places most of the probability mass on one of the two assignments where $\mathcal{P}$ has high probability.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 277

## I-Projection

>[!important]
>Consider the decomposition
>$$
>\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P} \right) = - H(\mathcal{Q}) +  \mathbb{E}_{ \mathcal{Q} }\left[ -\log \mathcal{P} \right]
>$$
>The first term is a **convex functional** of $\mathcal{Q}$ and the second term is a **linear functional** of $\mathcal{Q}$

- [[Evidence Lower Bound]]
- [[Bethe Entropy Approximation and Factorized Energy Functional]]
- [[Convex Function]]

## M-Projection

>[!important]
>Consider the decomposition of $M$-projection
>$$
>\mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{Q} \right) = - H(\mathcal{P}) +  \mathbb{E}_{ \mathcal{P} }\left[ -\log \mathcal{Q} \right] \; \propto \; \mathbb{E}_{ \mathcal{P} }\left[ -\log \mathcal{Q} \right] 
>$$
>The first term is a *constant* for given $\mathcal{P}$.


>[!important] Proposition
>Let $\mathcal{P}$ be a distribution over $(X_{1}\,{,}\ldots{,}\,X_{n})$, and let $\mathcal{M}$ be a *family of distributions* **consistent** with $\mathcal{G}_{\emptyset} = (V, \emptyset)$, the empty graph.
>
>Then 
>$$
> \mathcal{Q}^{M} := \arg\min_{\mathcal{Q} \vDash \mathcal{G}_{\emptyset}}\mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{Q} \right)
>$$
>is the **product of marginal distributions**
>$$
>\mathcal{Q}^{M}(X_{1}\,{,}\ldots{,}\,X_{n}) = \prod_{i=1}^{n}\mathcal{P}(X_{i})
>$$

- [[Product Measure]]
- [[Probabilistic Graphical Models]]

>[!important] Proposition
>Let $\mathcal{P}$ be a distribution over $(X_{1}\,{,}\ldots{,}\,X_{n})$, and let $\mathcal{G}$ be a  **Bayesian network structure**. 
>
>Then 
>$$
> \mathcal{Q}^{M} := \arg\min_{\mathcal{Q} \vDash \mathcal{G}}\mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{Q} \right)
>$$
>is the **product of local probabilistic models (CPDs)**
>$$
>\mathcal{Q}^{M}(X_{1}\,{,}\ldots{,}\,X_{n}) = \prod_{i}\mathcal{P}(X_{i}\,|\,X_{Pa^{\mathcal{G}}(i)})
>$$

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Local Probabilistic Models]]


### Exponential Family

![[Exponential Family and Convex Duality#^cb178d]]

- [[Exponential Family and Convex Duality]]
- [[Exponential Family of Distributions]]

>[!info]
>The above equation constraint 
>$$
> \mathbb{E}_{ \mathcal{Q}^{M} }\left[ T(x) \right] =  \mathbb{E}_{ \mathcal{P} }\left[ T(X) \right]
>$$
>is called the **moment matching constraint**. For exponential family, the $M$-projection **preserves** the *expectation of sufficient statistics*.

### M-Project Function

![[Log-Partition Function of Exponential Family#^e9381e]]

[[Log-Partition Function of Exponential Family]]

![[Convex Conjugate of Log-Partition Function of Exponential Family#^cdf6cd]]


>[!important] 
>Let $\mathcal{M}$ be the set of mean parameters of some probability measure $\mathcal{P}_{\eta}$ in an *exponential family*
>$$
>\mathcal{M} := \left\{ \mu \in \mathbb{R}^d:  \exists \mathcal{P}_{\eta} \text{ such that }  \mu = \mathbb{E}_{\mathcal{P}_{\eta}}\left[ T(X) \right] \right\}. 
>$$
>
>Define the **$M$-project operation** as a mapping from *mean parameters* to *natural parameters*, i.e.
>$$
>\text{M-project}(\mu) = \eta = (\nabla A)^{-1}(\mu)
>$$
>where $\eta$ is a *natural parameter* of some distribution $\mathcal{P}_{\eta}$ in an exponential family and $A$ is the corresponding *log-partition function*.

- [[Log-Partition Function of Exponential Family]]
- [[Convex Conjugate of Log-Partition Function of Exponential Family]]

>[!info]
>The $M$-project operation is called the **backward mapping.**
>
>For generalized linear model, it corresponding to the **link function**.

- [[Generalized Linear Models]]

## Information Geometry

>[!important]
>In information geometry,
>-  the **$I$-projection** corresponds to the *orthogonal projection* under the **$e$-connection** $\nabla^{e} = \nabla ^{(-1)}$.
>
>- the **$M$-projection** corresponds to  the *orthogonal projection* under the **$m$-connection,** $\nabla^{m} = \nabla ^{(1)}$ 

- [[e-Connection and m-Connection]]
- [[alpha-Connection on Statistical Manifold]]




-----------
##  Recommended Notes and References

- [[e-Connection and m-Connection]]


- [[Maximum Entropy Learning]]
- [[Maximum Likelihood Estimation]]

- [[Measure Space and Countably Additive Measure]]


- [[Elements of Information Theory by Cover]]
- [[Probabilistic Graphical Models by Koller]] pp 274 - 278