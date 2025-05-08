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
  - bethe_entropy_approximation
  - local_consistent_polytope
topics:
  - probabilistic_graphical_model
name: Bethe Variational Inference for Clique Tree
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Bethe Variational Inference for Clique Tree

![[Marginal Polytope and Local Consistent Polytope#^c31624]]

![[Bethe Entropy Approximation and Factorized Energy Functional#^2acf67]]

- [[Bethe Entropy Approximation and Factorized Energy Functional]]
- [[Marginal Polytope and Local Consistent Polytope]]

>[!important] Definition
>The **Bethe variational inference** problem can be formulated as
>$$
>\begin{align*}
>  \max_{(\beta, \mu)}\;&  \sum_{i\in V(G)}\mathbb{E}_{\beta_{i}}\left[\log \psi(C_{i})\right] + \sum_{i\in V(G)}H_{\beta_{i}}(C_{i}) - \sum_{ij \in E(G)}H_{\mu_{i,j}}(S_{i,j})\\[5pt]
>  \text{s.t. }& \mu_{i,j}(s_{i,j}) = \sum_{c_{i} \setminus s_{i,j}}\beta_{i}(c_{i}),\;\; \forall ij\in E(G), \forall s_{i,j}\in \text{Val}(S_{i,j}) \\ 
>  &\sum_{c_{i}}\beta_{i}(c_{i}) = 1,\;\; \forall i \in V(G).\\
>  &\beta_{i}(c_{i}) \ge 0,\;\; \forall i \in V(G),\; c_{i} \in \text{Val}(C_{i})
>\end{align*}
>$$
>where 
>- $\beta := \left(\beta_{i}, i\in V(T)\right)$,  
>- $\mu := \left(\mu_{i,j}, \, ij\in E(T)\right),$
>- and the **unormalized likelihood function** is of the factorized form with initial potentials $$\hat{\mathcal{P}}_{\Phi}(\mathcal{X}) := \prod_{\phi \in \Phi}\phi(U_{\phi}).$$

^9e261d

>[!important] Definition
>The **Bethe variational inference** problem in **compact form** can be formulated as
>$$
>\begin{align*}
>  \max_{(\beta, \mu)}\;& \left\langle  \theta\,,\, \beta \right\rangle + \sum_{i\in V(G)}H_{\beta_{i}}(C_{i}) - \sum_{ij\in E(G)}H_{\mu_{i,j}}(S_{i,j})\\[5pt]
>  \text{s.t. }&\; (\beta, \mu) \in \mathbb{L}(G)
>\end{align*}
>$$
>where 
>$$
>\theta = (\log \psi(c_{i}), \; i\in V(G))
>$$


### Bethe Variational Inference problem in Tree-Structured Graph

>[!important] Definition
>If $T = (V, E)$ is a **tree-structured graph**, with 
>- *edge potentials* $\tau_{i,j}$ for $ij\in E$ and 
>- *node potentials* $\tau_{i}$ for $i\in V$, 
>
>then the **Bethe variational inference** problem in **compact form** can be formulated as
>$$
>\begin{align*}
>  \max_{\tau}\;& \left\langle  \theta\,,\, \tau \right\rangle + \sum_{i\in V}H_{i}(\tau_{i}) - \sum_{ij\in E}I_{ij}(\tau_{i,j}\;\|\;\tau_{i}\,\tau_{j})\\[5pt]
>  \text{s.t. }& \tau \in \mathbb{L}(T)
>\end{align*}
>$$
>where
>- $$\theta = (\log \psi(c_{i}), \; i\in V(T))$$ 
>- $$I_{ij}(\tau_{i,j}\;\|\;\tau_{i}\,\tau_{j}) = \mathbb{E}_{ \tau_{i,j} }\left[ \log \left(\frac{\tau_{i,j}}{\tau_{i}\,\tau_{j}}\right) \right]$$

- [[Exponential Family and Convex Duality]]

## Explanation

>[!info]
>For a *clique tree* on a *tree-structure graph* $T$, we have that
>- each **clique** $C_{i}$ is a set of **two variables**
>- each **sepset** $S_{i,j}$ is a **single variable** 
>  
>Therefore, 
>- $\beta_{i}$ is a clique belief and it represent the **joint distribution of two variables**
>- $\mu_{i,j}$ is a sepset belief and it represent the **marginal distribution of one variable**

>[!important] 
>The **Bethe variational inference problem** has two approximations:
>- it approximates the *marginal polytope* $\mathbb{M}(\mathcal{G})$ by the *local consistent polytope* $\mathbb{L}(\mathcal{G})$
>- it approximates the *entropy* / *ELBO* / *energy functional* by the *factorized* version
>  
>  
>$$
>\begin{align*}
> \max_{\mathcal{Q}_{\beta, \mu} \in \mathscr{P}_{\mathscr{C}}}\; \mathcal{L}(\mathcal{Q}, \Phi; \mathcal{X}) \;\;&\implies \quad \max_{\mathcal{Q}_{\beta, \mu} \in \mathscr{P}_{\mathscr{C}}}\; \hat{\mathcal{L}}(\mathcal{Q}, \Phi; \mathcal{X}) \\[5pt]
> \text{ s.t. } (\beta, \mu) \in \mathbb{M}(\mathcal{G}) \;\;&\implies\quad \text{ s.t. } (\beta, \mu) \in \mathbb{L}(\mathcal{G})
>\end{align*}
>$$

>[!quote]
>Thus, our optimization problem contains two **approximations**: We are using an **approximation**, *rather than an exact*, **energy functional**; and we are optimizing it over the *space of* **pseudo-marginals**, which is a *relaxation (a superspace)* of the *space of all* **coherent probability distributions** that factorize over the cluster graph.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 412


>[!quote]
>Note that this problem has a very simple structure: the **cost function** is given in *closed form*, it is *differentiable*, and the **constraint set** $\mathbb{L}(G)$ is a *polytope* specified by a small number of constraints. Given this special structure, one might suspect that there should exist a relatively simple algorithm for solving this optimization problem (4.16). Indeed, the **sum-product algorithm** turns out to be exactly such a method.
>
>-- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 83

>[!quote]
>The **connection** between the **sum-product algorithm** and the **Bethe variational principle** has a number of important consequences. **First**, it provides a **principled basis** for applying the *sum-product algorithm* for **graphs with cycles**, namely as a particular type of *iterative method* for attempting to satisfy *Lagrangian conditions*. It should be noted, however, that this connection between sum-product and the Bethe problem in itself provides **no guarantees on the convergence** of the sum-product updates on graphs with cycles. ..... However, with the exception of **trees** and other *special cases* \[110, 167, 188\], the *Bethe variational problem* is usually a **nonconvex problem**, in that $H_{\text{Bethe}}$ fails to be *concave*. As a consequence, there are frequently *local optima*, so that even when using a convergent algorithm, there are no guarantees that it will find the global optimum.
>...
>Another important consequence of the Bethe/sum-product connection is in suggesting a *number of avenues* for **improving** upon the ordinary sum-product algorithm, via **progressively better approximations** to the *entropy function* and *outer bounds* on the *marginal polytope*.
>
>-- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 87
## Solution of Bethe Variational Inference

- [[Stationary Point of Bethe Variational Inference Problem]]



-----------
##  Recommended Notes and References


- [[Variational Inference for Clique Tree]]

- [[Evidence Lower Bound]]
- [[Expectation-Maximization Algorithm]]
- [[Comparison of Variational Inference vs EM Algorithm]]


- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network Distribution to Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 387, 405, 411- 412, 446
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 73 - 92
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
