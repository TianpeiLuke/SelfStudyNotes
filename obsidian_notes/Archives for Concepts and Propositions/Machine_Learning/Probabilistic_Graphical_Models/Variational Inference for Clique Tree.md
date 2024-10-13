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
  - cluster_graph
topics:
  - probabilistic_graphical_model
name: Variational Inference for Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Variational Inference for Graphical Model

### Maximum Entropy Learning via Energy Functional

![[Maximum Entropy Learning of Clique Tree PGM#^f81f88]]

![[Energy Functional for Probabilistic Graphical Model#^c01c98]]

- [[Energy Functional for Probabilistic Graphical Model]]
- [[Maximum Entropy Learning of Clique Tree PGM]]

>[!info]
>$$
>\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}_{\Phi} \right) = \log Z - \mathcal{L}(\mathcal{Q}, \hat{\mathcal{P}}_{\Phi}; \mathcal{X}) 
>$$

>[!important] Definition
>Let $\mathcal{G}$ be a cluster graph associated with potential set $\Phi$.
>
>The **maximum entropy learning** algorithms can be reformulated as the *optimization problem*
>$$
>\begin{align*}
>  \max_{\mathcal{Q} \in \mathscr{P}_{\mathscr{C}}}\;& \mathcal{L}(\mathcal{Q}, \Phi; \mathcal{X}) \\[5pt]
>  \text{s.t. }\;&\, \mu_{i,j}(s_{i,j}) = \mathbb{E}_{ \mathcal{Q}_{\beta, \mu} }\left[  \mathbb{1}_{s_{i,j}}\{S_{i,j}\} \right],\;\; \forall ij\in E(\mathcal{G}), \forall s_{i,j}\in \text{Val}(S_{i,j}) \\[5pt] 
>  &\beta_{i}(c_{i}) = \mathbb{E}_{ \mathcal{Q}_{\beta, \mu} }\left[  \mathbb{1}_{c_{i}}\{C_{i}\} \right],\;\; \forall i \in V(\mathcal{G}), \forall c_{i}\in \text{Val}(C_{i}).
>\end{align*}
>$$
>where 
>- $\beta := \left(\beta_{i}, i\in V(\mathcal{G})\right)$,  and
>- $\mu := \left(\mu_{i,j}, \, ij\in E(\mathcal{G})\right)$ are **marginals**, 
>- $\mathcal{Q}_{\beta, \mu}$ is a **clique tree measure**  $$\mathcal{Q}_{\beta, \mu}\in \mathscr{P}_{\mathscr{C}} := \left\{ \frac{\prod_{i\in V(\mathcal{G})}\beta_{i}}{\prod_{ij\in E(\mathcal{G})}\mu_{i,j}}: (\beta, \mu) \in\mathscr{C} \right\} $$
>- and the **unormalized likelihood function** is of the factorized form with initial potentials $$\hat{\mathcal{P}}_{\Phi}(\mathcal{X}) := \prod_{\phi \in \Phi}\phi(U_{\phi}).$$

^5fe294

>[!important] Definition
>The **maximum entropy learning** can be formulated in **compact form**
>$$
>\begin{align*}
>  \max_{(\beta, \mu) \in \mathscr{C}}\;& \mathcal{L}(\mathcal{Q}_{\beta, \mu}, \Phi; \mathcal{X}) \\[5pt]
>  \text{s.t. }\;&\, (\beta, \mu)\in \mathbb{M}(\mathcal{G})
>\end{align*}
>$$

>[!info]
>For $\mathcal{Q}_{\beta, \mu}$ clique tree measure, the *ELBO* or the *energy functional* has the form $$\mathcal{L}((\beta, \mu), \Phi; \mathcal{X}) := \left\langle  \theta\,,\,\beta \right\rangle + H(\mathcal{Q}_{\beta, \mu})$$
>
>Note that $H(\mathcal{Q}_{\beta, \mu})$ is usually **intractable** and **non-concave**, but it is *differentiable*.


### Marginal Polytope and Local Consistent Polytope

- [[Marginal Polytope and Local Consistent Polytope]]

### Variational Inference by Maximizing the Factorized Energy Functional

![[Bethe Entropy Approximation and Factorized Energy Functional#^2acf67]]

>[!important] Definition
>The **variational inference** with **factorized energy functional** can be defined as
>$$
>\begin{align*}
>  \max_{(\beta, \mu)}\;& \hat{\mathcal{L}}((\beta,\mu), \Phi; \mathcal{X}) \\[5pt]
>  \text{s.t. }& \mu_{i,j}(s_{i,j}) = \sum_{C_{i} \setminus S_{i,j}}\beta_{i}(c_{i}),\;\; \forall ij\in E(T), \forall s_{i,j}\in \text{Val}(S_{i,j}) \\ 
>  &\sum_{c_{i}}\beta_{i}(c_{i}) = 1,\;\; \forall i \in V(T).\\
>  &\beta_{i}(c_{i}) \ge 0,\;\; \forall i \in V(T),\; c_{i} \in \text{Val}(C_{i})
>\end{align*}
>$$
>where 
>- $\beta := \left(\beta_{i}, i\in V(T)\right)$,  
>- $\mu := \left(\mu_{i,j}, \, ij\in E(T)\right),$
>- the *factorized energy functional* is defined as $$\hat{\mathcal{L}}((\beta,\mu), \Phi; \mathcal{X}) := \sum_{i\in V(T)}\mathbb{E}_{\beta_{i}}\left[\log \psi(C_{i})\right] + \sum_{i\in V(T)}H_{\beta_{i}}(C_{i}) - \sum_{ij \in E(T)}H_{\mu_{i,j}}(S_{i,j})$$
>- and the **unormalized likelihood function** is of the factorized form with initial potentials $$\hat{\mathcal{P}}_{\Phi}(\mathcal{X}) := \prod_{\phi \in \Phi}\phi(U_{\phi}).$$

>[!info]
>In compact form, 
>$$
>\begin{align*}
>  \max_{\mathcal{Q}_{\beta, \mu} \in \mathscr{P}_{\mathscr{C}}}\;& \hat{\mathcal{L}}(\mathcal{Q}, \Phi; \mathcal{X}) \\[5pt]
>  \text{s.t. }& (\beta, \mu) \in \mathbb{L}(T)
>\end{align*}
>$$

- [[Bethe Variational Inference for Clique Tree]]
- [[Bethe Entropy Approximation and Factorized Energy Functional]]
- [[Marginal Polytope and Local Consistent Polytope]]
- [[Bethe Variational Inference for Clique Tree]]

## Explanation

>[!important]
>The energy functional defined above has close relationship to the dual of log-partition function $$A^{*}(\mu) = \sup_{\theta}\left\{ \left\langle  \mu\,,\,\theta    \right\rangle - A(\theta)\right\} = -H(p_{\theta}), \quad A(\Phi) = \log Z = \log \int \hat{\mathcal{P}}_{\Phi} $$
>Note that for graphical model in exponential family, the **pseudomarginals** are the **mean parameterization** of the exponential family. Denote
>$$
> \mu_{i} := \beta_{i}; \;\; \mu_{i,j} = \mu_{i,j}\;\; (\text{marginal in sepset})
>$$
>Then 
>$$
>\begin{align*}
>\mathcal{L}(\mu, \Phi; \mathcal{X}) &:= \left\langle  \theta\,,\,\mu \right\rangle + H(\mathcal{Q}_{\mu}) \\[5pt]
>&=  \left\langle  \theta\,,\,\mu \right\rangle - A^{*}(\mu)
>\end{align*}
>$$
>Thus by [[Convex Conjugate Function]], we see 
>$$
>\max_{\mu}\,\mathcal{L}(\mu, \Phi; \mathcal{X}) = \left(A^{*}(\mu)\right)^{*} = A(\Phi)
>$$

- [[Shannon Entropy]]
- [[Mutual Information]]


## Approximations in Variational Inference

>[!info]
>Note that the ELBO is usually **intractable**
>$$\mathcal{L}((\beta, \mu), \Phi; \mathcal{X}) := \left\langle  \theta\,,\,\beta \right\rangle + H(\mathcal{Q}_{\beta, \mu})$$
>In variational inference, we approximate it using a **tractable energy function** that **factorize** according to graph $\mathcal{G}$.
>$$\hat{\mathcal{L}}((\beta, \mu), \Phi; \mathcal{X}) := \left\langle  \theta\,,\,\beta \right\rangle + H_{\text{Bethe}}(\mathcal{Q}_{\beta, \mu})$$


>[!important] 
>The **Bethe variational inference problem** has two approximations:
>- it approximates the *marginal polytope* $\mathbb{M}(\mathcal{G})$ by the *local consistent polytope* $\mathbb{L}(\mathcal{G})$
>- it approximates the *entropy* / *ELBO* / *energy functional* by the *factorized* version
>  
>  
>$$
>\begin{align*}
> \max_{\mathcal{Q}_{\beta, \mu} \in \mathscr{P}_{\mathscr{C}}}\; \mathcal{L}(\mathcal{Q}, \Phi; \mathcal{X}) \;\;&\implies \quad \max_{\mathcal{Q}_{\beta, \mu} \in \mathscr{P}_{\mathscr{C}}}\; \hat{\mathcal{L}}(\mathcal{Q}, \Phi; \mathcal{X}) \\[5pt]
> \text{ s.t. } (\beta, \mu) \in \mathbb{M}(T) \;\;&\implies\quad \text{ s.t. } (\beta, \mu) \in \mathbb{L}(T)
>\end{align*}
>$$

>[!info]
>- For **clique tree** $T$, the above approximation of energy functional is **exact**.
>- For **cluster graph** $\mathcal{G}$, the above approximation is **inexact**.




## Necessary Condition for Optimal Solution and Message Passing Algorithm


- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[Stationary Point of Bethe Variational Inference Problem]]




-----------
##  Recommended Notes and References


- [[Maximum Entropy Learning of Clique Tree PGM]]
- [[Evidence Lower Bound]]
- [[Expectation-Maximization Algorithm]]
- [[Variational Inference vs EM Algorithm]]


- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network Distribution to Graph]]

- [[Information Projection and Moment Projection]]

- [[Probabilistic Graphical Models by Koller]] pp 385 - 390, 396-406, 411 - 418
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 73 - 92
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
