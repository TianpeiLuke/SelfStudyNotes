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
name: Mean Field Approximation for Exponential Family
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Mean Field Approximation for Exponential Family

![[Energy Functional for Probabilistic Graphical Model#^144559]]

>[!important] Definition
>Consider an *exponential family* $P_{\phi}$ with a collection $\phi = (\phi_{\alpha}, \alpha \in I)$ of *sufficient statistics* associated with the *cliques* of $\mathcal{G} = (\mathcal{V}, \mathcal{E})$ and natural parameters $\theta^{P}$
>- The space of all *$\phi$-exponential family* that factorizes over $\mathcal{G}$ is $$\mathscr{P} := \left\{P_{\phi} \in \mathcal{M}:  P_{\phi} \vDash \mathcal{I}(\mathcal{G}) \right\}$$ 
>- and the corresponding p.d.f. has the form $$P_{\Phi}(x; \theta^{P}) = \exp \left(\sum_{\alpha \in I} \theta^{P}_{\alpha }\,\phi_{\alpha }(x_{D_{\alpha}}) - A(\theta^{P})\right)$$ where  $A(\theta^{P})$ is the *log-partition function*, $$D_{\phi} := \text{domain}(\phi),\; \implies\; \phi: X_{D_{\phi}} \to \mathbb{R}$$
>- The *unnormalized distribution* $$\tilde{P}_{\Phi}(x; \theta^{P}) = \exp \left(\sum_{\alpha \in I} \theta^{P}_{\alpha }\,\phi_{\alpha }(x_{D_{\alpha}})\right)$$
>  
>The **naive mean field algorithms** assume that the *variational distribution* $Q$ is within the class of distributions that are the *product of independent marginals*
>$$
>\mathcal{Q}_{\text{mean field}} := \left\{ Q \in \mathcal{M}(\mathcal{Z}): Q(X_{v}\,,\, v\in \mathcal{V}) = \prod_{v\in \mathcal{V}} Q(X_{v}) \right\} 
>$$
>Thus the **energy functional** can be factorized as
>$$
>\begin{align*}
>\mathcal{L}(Q, \theta^{P}; \mathcal{X})  &= \left\langle  \mu^{Q}\,,\, \theta^{P}\right\rangle + H_{Q}(X)  \\[5pt]
>&= \left\langle  \mu^{Q}\,,\, \theta^{P}\right\rangle + \sum_{v\in \mathcal{V}}H_{Q_{v}}(X_{v}) \\[5pt]
>&= \sum_{\alpha \in I}\theta_{\alpha}^{P}\,\mu_{\alpha}^{Q} + \sum_{v\in \mathcal{V}}H_{Q_{v}}(X_{v}) 
>\end{align*}
>$$ 
>where $\mu^{Q}$ is the *expected value of sufficient statistics* with respect to $Q$, i.e. 
>$$
>\mu^{Q}_{\alpha} = \mathbb{E}_{ Q }\left[ \phi(X_{D_{\phi_{\alpha}}})\right] = \sum_{X_{\alpha}}\,\left(\prod_{v\in \phi_{\alpha}}Q_{v}(X_{v})\right)\phi_{\alpha}(X_{\alpha}), \quad \forall \alpha\in I.
>$$
>
>The **naive mean field algorithm** on $\mathcal{P}_{\Phi}(x; \theta^{P})$ solves the following optimization problem
>$$
>\begin{align*}
>  \max_{\{Q(X_{i})\}}\;& \mathcal{L}(Q, \theta^{P}; \mathcal{X}) =  \sum_{\alpha \in I}\theta_{\alpha}^{P}\,\mu_{\alpha}^{Q} + \sum_{v\in \mathcal{V}}H_{Q_{v}}(X_{v})\\[5pt]
>  \text{s.t. }\;&\, Q(X) = \prod_{v\in \mathcal{V}}Q(X_{v})\\[5pt]
>  &\, \sum_{X_{v}\in \mathcal{X}_{v}}Q(X_{v}) = 1,\quad \forall v\in \mathcal{V} \\[10pt]
>  &\, \mu^{Q}_{\alpha} = \mathbb{E}_{ Q }\left[ \phi(X_{D_{\phi_{\alpha}}})\right], \quad \forall \alpha\in I 
>\end{align*}
>$$
  

- [[Energy Functional for Probabilistic Graphical Model]]
- [[Maximum Entropy Learning of Exponential Family]]
- [[Marginal Polytope and Local Consistent Polytope]]
- [[Evidence Lower Bound for Exponential Family]]
- [[Kullback-Leibler Divergence for Exponential Family]]





## Explanation





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
