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
topics:
  - probabilistic_graphical_model
name: Mean Field Approximation for PGM
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Mean Field Approximation for PGM

![[Evidence Lower Bound#^c74005]]

![[Evidence Lower Bound#^afb000]]

- [[Evidence Lower Bound]]

>[!important] Definition
>The **naive mean field algorithms** assume that the *variational distribution* $q\in \mathcal{Q}$ is within the class of distributions that are the *product of independent marginals*
>$$
>\mathcal{Q}_{\text{mean field}} := \left\{ q \in \mathcal{M}(\mathcal{Z}): q(Z_{1} \,{,}\ldots{,}\,Z_{k}) = \prod_{i} q(Z_{i}) \right\} 
>$$
>
>The **ELBO** or **negative variational free energy** under the *mean field assumption* is given by
>$$
>\begin{align*}
>\mathcal{L}(q, \theta; x) &= \mathbb{E}_{ q\in \mathcal{Q}_{\text{mean}} }\left[ \log p_{\theta}(x, Z) - \log q(Z) \right] \\[5pt]
>&= \mathbb{E}_{ q\in \mathcal{Q}_{\text{mean}} }\left[ \log p_{\theta}(x, Z)\right] - \mathbb{E}_{ q\in \mathcal{Q}_{\text{mean}} }\left[ \log q(Z) \right]\\[5pt]
>&= \sum_{Z\in \mathcal{Z}}\left(\prod_{i=1}^{k}q(Z_{i})\right)\log p_{\theta}(x, Z) + \sum_{i=1}^{k}H(q(Z_{i}))
>\end{align*}
>$$

>[!important] Definition
>Let $\mathcal{P}_{\Phi}$ be a *Bayesian network* or *Markov network* over $\mathcal{X}$ that *factorizes* according to $\mathcal{G}$, and $\Phi$ be a set of *factors* in $\mathcal{P}$.
>
>The **naive mean field algorithm** on $\mathcal{P}_{\Phi}$ can be formulated in **compact form**
>$$
>\begin{align*}
>  \min_{\{\mathcal{Q}(X_{i})\}}\;& \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}_{\Phi} \right) \\[5pt]
>  \text{s.t. }\;&\, \mathcal{Q}(X) = \prod_{i\in \mathcal{V}(\mathcal{G})}\mathcal{Q}(X_{i})\\[5pt]
>  &\, \sum_{Z_{i}\in \mathcal{Z}_{i}}\mathcal{Q}(X_{i}) = 1,\quad \forall i\in \mathcal{V}(\mathcal{G})
>\end{align*}
>$$
>- Instead of estimation the joint variational distribution $\mathcal{Q}$, the mean field algorithm estimates *each marginal distribution* independently.
>  
>Equivalently, we can represent it as **maximizing the variational free energy**   
>$$
>\begin{align*}
>  \max_{\{ \mathcal{Q}(X_{i}) \}}\;& \mathcal{L}(\mathcal{Q}, \Phi; \mathcal{X}) = - \mathbb{E}_{ \mathcal{Q} }\left[  \log \mathcal{P}_{\Phi}  \right] - \sum_{i\in \mathcal{V}}H_{\mathcal{Q}}(X_{i}) \\[5pt]
>  \text{s.t. }\;&\, \mathcal{Q}(X) = \prod_{i\in \mathcal{V}}\mathcal{Q}(X_{i})\\[5pt]
>  &\, \sum_{X_{i}\in \mathcal{X}_{i}}\mathcal{Q}(X_{i}) = 1,\quad \forall i\in \mathcal{V}
>\end{align*}
>$$

- [[Maximum Entropy Learning for Approximate Inference in PGM]]
- [[Marginal Polytope and Local Consistent Polytope]]



## Explanation





-----------
##  Recommended Notes and References

- [[Structured Variational Approximation]]
- [[Information Projection and Moment Projection]]

- [[Kullback-Leibler Divergence]]
- [[Cross-Entropy Loss Function]]
- [[Maximum Entropy Learning]]

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network on Undirected Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 449 - 469
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 125 - 147
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
