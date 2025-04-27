---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/representation
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/theory
  - mean_field_approximation
keywords:
  - mean_field_approximation
topics:
  - probabilistic_graphical_model
name: Mean Field Approximation for Exponential Family
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Mean Field Approximation for Exponential Family

![[Energy Functional for Probabilistic Graphical Model#^144559]]

### Tractable Family and Approximation of Mean Parameter Space

![[Structured Variational Approximation#^3ca63f]]
![[Structured Variational Approximation#^4cc9e0]]

- [[Structured Variational Approximation]]

### Naive Mean Field Approximation

>[!important] Definition
>Consider an *exponential family* $P_{\phi}$ with a collection $\phi = (\phi_{\alpha}, \alpha \in I)$ of *sufficient statistics* associated with the *cliques* of $\mathcal{G} = (\mathcal{V}, \mathcal{E})$ and natural parameters $\theta$
>- The space of all *$\phi$-exponential family* that factorizes over $\mathcal{G}$ is $$\mathscr{P} := \left\{P_{\phi} \in \mathcal{M}:  P_{\phi} \vDash \mathcal{I}(\mathcal{G}) \right\}$$ 
>- and the corresponding p.d.f. has the form $$P_{\Phi}(x; \theta) = \exp \left(\sum_{\alpha \in I} \theta_{\alpha }\,\phi_{\alpha }(x_{\alpha}) - A(\theta)\right)$$ where  $A(\theta)$ is the *log-partition function*, $$X_{\alpha} := \text{scope}(\phi_{\alpha}),\; \implies\; \phi_{\alpha}: X_{\alpha} \to \mathbb{R}$$
>- The *unnormalized distribution* $$\tilde{P}_{\Phi}(x; \theta) = \exp \left(\sum_{\alpha \in I} \theta_{\alpha }\,\phi_{\alpha }(x_{\alpha})\right)$$
>  
>The **naive mean field algorithms** assume that the *variational distribution* $Q$ is within the class of distributions that are the *product of independent marginals*
>$$
>\begin{align*}
>\mathcal{Q}_{\text{mean field}} &:= \left\{ Q \in \mathcal{M}(\mathcal{Z}): Q(X_{v}\,,\, v\in \mathcal{V}) = \prod_{v\in \mathcal{V}} Q(X_{v}) \right\} \\[5pt]
>&=  \{ Q:\; Q \vDash \mathcal{F} := (\mathcal{V}, \emptyset) \}
>\end{align*}
>$$
>- $\mathcal{F}:= (\mathcal{V}, \emptyset) \subset \mathcal{G}$ is a subgraph with *no edges*.
>- Assume that $Q$ is from an exponential family $$Q \in \mathcal{Q}_{\text{mean field}}\cap \mathscr{P}_{\Phi}$$
>- This means that the space of mean parameters $\mu^{Q}$ of $Q$ under *mean field approximation* is $$\mathbb{M}_{\mathcal{F}}(\mathcal{G}) = \{\mu = (\mu_{\alpha}) \in \mathbb{R}^{d}, \;\; \mathbb{E}_{ \eta }\left[  \phi_{\alpha}(X) \right] =  \mu_{\alpha}, \;\; \text{ where }\eta_{\alpha} = 0,\; \forall \alpha\in I \setminus I_{\mathcal{F}} \}$$ 
>- The *restriction* of dual function $A^{*}(\mu)$ on $\mathbb{M}_{\mathcal{F}}(\mathcal{G})$ is given by $$A^{*}(\mu)\big|_{\mathbb{M}_{\mathcal{F}}(\mathcal{G})} := A_{\mathcal{F}}^{*}(\mu).$$
>
>Thus the **energy functional** can be factorized as
>$$
>\begin{align*}
>\mathcal{L}(\mu^{Q}, \theta; \mathcal{X})  &= \left\langle  \mu^{Q}\,,\, \theta\right\rangle + H_{Q}(X)  \\[5pt]
>&:= \left\langle  \mu^{Q}\,,\, \theta\right\rangle - A_{\mathcal{F}}^{*}(\mu^{Q})  \\[5pt]
>&= \left\langle  \mu^{Q}\,,\, \theta\right\rangle + \sum_{v\in \mathcal{V}}H_{Q_{v}}(X_{v})
>\end{align*}
>$$ 
>where $\mu^{Q} = (\mu_{\alpha}^{Q})$ is the *expected value of sufficient statistics* with respect to product measure $Q$, i.e. 
>$$
>\mu^{Q}_{\alpha} = \mathbb{E}_{ Q }\left[ \phi(X_{\alpha})\right] = \sum_{x_{\alpha}}\,\left(\prod_{v\in \text{scope}(\phi_{\alpha})}Q_{v}(x_{v})\right)\phi_{\alpha}(x_{\alpha}), \quad \forall \alpha\in I_{\mathcal{F}}.
>$$
>
>The **naive mean field algorithm** on $\mathcal{P}_{\Phi}(x; \theta)$ solves the following optimization problem
>$$
>\begin{align*}
>  \max_{\mu^{Q}}\;& \mathcal{L}(\mu^{Q}, \theta; \mathcal{X}) =  \left\langle  \mu^{Q}\,,\, \theta\right\rangle - A_{\mathcal{F}}^{*}(\mu^{Q}) \\[5pt]
>  \text{s.t. }\;&\, \mu^{Q} \in \mathbb{M}_{\mathcal{F}}(\mathcal{G})
>\end{align*}
>$$

^9d3014

- [[Energy Functional for Probabilistic Graphical Model]]
- [[Maximum Entropy Learning of Exponential Family]]
- [[Marginal Polytope and Local Consistent Polytope]]
- [[Evidence Lower Bound for Exponential Family]]
- [[Kullback-Leibler Divergence for Exponential Family]]


## Explanation




## Mean Field Approximation for Gaussian Graphical Model

- [[Mean Field Approximation for Gaussian Markov Random Field]]




-----------
##  Recommended Notes and References

- [[Structured Variational Approximation]]
- [[Information Projection and Moment Projection]]

- [[Kullback-Leibler Divergence]]
- [[Cross-Entropy Loss Function]]
- [[Maximum Entropy Learning]]
- [[Evidence Lower Bound]]


- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network on Undirected Graph]]
- [[Exponential Family of Distributions]]


- [[Probabilistic Graphical Models by Koller]] pp 449 - 469
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 125 - 147
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
