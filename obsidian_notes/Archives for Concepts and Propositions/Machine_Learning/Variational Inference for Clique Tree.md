---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/theory
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/inference
keywords:
  - variational_inference
  - probabilistic_graphical_model
  - clique_tree
topics:
  - probabilistic_graphical_model
name: Variational Inference for Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Variational Inference for Graphical Model

![[Maximum Entropy Learning of Clique Tree PGM#^f81f88]]

>[!important] Definition
>We can define the **evidence lower bound (ELBO)** for the variational distribution $\mathcal{Q}$ 
>$$
>\begin{align*}
>\mathcal{L}(\mathcal{Q}, \hat{\mathcal{P}}_{\Phi}; \mathcal{X}) &:= \mathbb{E}_{ \mathcal{Q} }\left[ \log \left(\frac{\hat{\mathcal{P}}_{\Phi}(\mathcal{X})}{\mathcal{Q}(\mathcal{X})}\right) \right] \\[5pt]
>&= \mathbb{E}_{ \mathcal{Q} }\left[\log \hat{\mathcal{P}}_{\Phi}(\mathcal{X}) \right]  - \mathbb{E}_{ \mathcal{Q} }\left[  \log \mathcal{Q} \right] \\[10pt]
>&= \sum_{\phi\in \Phi}\mathbb{E}_{ \mathcal{Q} }\left[  \log(\phi) \right] + H_{\mathcal{Q}}(\mathcal{X})
\end{align*}
>$$

- [[Maximum Entropy Learning of Clique Tree PGM]]

>[!info]
>$$
>\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}_{\Phi} \right) = \log Z - \mathcal{L}(\mathcal{Q}, \hat{\mathcal{P}}_{\Phi}; \mathcal{X}) 
>$$

>[!important] Definition
>The **variational inference** algorithms solve the following *optimization problem*
>$$
>\begin{align*}
>  \min_{\mathcal{Q} \in \mathscr{P}_{\mathscr{C}}}\;& -\mathcal{L}(\mathcal{Q}, \hat{\mathcal{P}}_{\Phi}; \mathcal{X}) \\[5pt]
>  \text{s.t. }& \mu_{i,j}(s_{i,j}) = \sum_{C_{i} \setminus S_{i,j}}\beta_{i}(c_{i}),\;\; \forall ij\in E(T), \forall s_{i,j}\in \text{Val}(S_{i,j}) \\ 
>  &\sum_{c_{i}}\beta_{i}(c_{i}) = 1,\;\; \forall i \in V(T).\\
>  &\beta_{i}(c_{i}) \ge 0,\;\; \forall i \in V(T),\; c_{i} \in \text{Val}(C_{i})
>\end{align*}
>$$
>where 
>- $\beta := \left(\beta_{i}, i\in V(T)\right)$,  
>- $\mu := \left(\mu_{i,j}, \, ij\in E(T)\right),$
>- $\mathcal{Q}$ is a **clique tree measure**  $$\mathcal{Q}\in \mathscr{P}_{\mathscr{C}} := \left\{ \frac{\prod_{i\in V(T)}\beta_{i}}{\prod_{ij\in E(T)}\mu_{i,j}}: (\{ \beta_{i},\; i\in V(T) \}\,\cup\, \{ \mu_{i,j},\; ij\in E(T) \}) \in\mathscr{C} \right\} $$
>- and the **unormalized likelihood function** is of the factorized form with initial potentials $$\hat{\mathcal{P}}_{\Phi}(\mathcal{X}) := \prod_{\phi \in \Phi}\phi(U_{\phi}).$$

^5fe294



## Explanation


## Necessary Condition for Optimal Solution and Message Passing Algorithm


- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[Stationary Point of Variational Inference for Clique Tree]]




-----------
##  Recommended Notes and References


- [[Evidence Lower Bound]]
- [[Expectation-Maximization Algorithm]]
- [[Variational Inference vs EM Algorithm]]


- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network Distribution to Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 387
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 73 - 92
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
