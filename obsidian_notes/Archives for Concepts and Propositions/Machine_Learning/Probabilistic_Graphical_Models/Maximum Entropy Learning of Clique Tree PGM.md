---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/inference
keywords:
  - maximum_entropy_learning
  - probabilistic_graphical_model
  - clique_tree
topics:
  - probabilistic_graphical_model
name: Maximum Entropy Learning of Clique Tree PGM
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Maximum Entropy Learning of Clique Tree Graphical Model

>[!important] Definition
>Let $T$ be a *clique tree* for $\mathcal{P}_{\Phi}$, i.e. $T$ satisfies the *running intersection property* and *family preservation property*. Moreover, suppose that we are given a set of *beliefs* $$(\{ \beta_{i},\; i\in V(T) \}\,\cup\, \{ \mu_{i,j},\; ij\in E(T) \}) := (\beta, \mu) \in \mathscr{C}$$ and 
>- $C_{i}$ denotes the *clique* $i$ in $T$, 
>- $\beta_{i}$ denotes the *clique belief* over $C_{i}$,  
>- $\mu_{i,j}$ denotes the *sepset belief* over $S_{i,j}$ for each $ij\in E(T),$ and
>- $\mathscr{C}$ is the *configuration space* of all possible beliefs $(\beta, \mu)$
>
>The **goal** is to make inference on factorized distribution 
>$$\mathcal{P}_{\Phi}(\mathcal{X}) := \frac{1}{Z}\prod_{\phi \in \Phi}\phi(U_{\phi}) = \frac{1}{Z}\hat{\mathcal{P}}_{\Phi}(\mathcal{X}).$$
>
>Consider a family of **clique tree measures** of the form $$\mathcal{Q}(\mathcal{X}) := \frac{\prod_{i\in V(T)}\beta_{i}}{\prod_{ij\in E(T)}\mu_{i,j}}$$
>- Due to the *calibration requirement*, the set of beliefs in $\mathscr{C}$ defines the **marginal consistency constraints** $$\mu_{i,j}(S_{i,j}) = \sum_{C_{i} \setminus S_{i,j}}\beta_{i}(C_{i}) = \sum_{C_{j} \setminus S_{i,j}}\beta_{j}(C_{j}).$$
>- Also the **normalization constraint** $$\sum_{c_{i}}\beta_{i}(c_{i}) = 1$$
>- Denote $$\mathscr{P}_{\mathscr{C}} := \left\{ \frac{\prod_{i\in V(T)}\beta_{i}}{\prod_{ij\in E(T)}\mu_{i,j}}: (\{ \beta_{i},\; i\in V(T) \}\,\cup\, \{ \mu_{i,j},\; ij\in E(T) \}) \in\mathscr{C} \right\} $$
> 

^f81f88

>[!important] Definition
>The *exact inference problem* for clique-tree structured graphical model can be viewed as the **maximum entropy learning** with **moment constraints**.
>
>Specifically, the exact inference can be obtained as the following **convex optimization problem**  
>$$
>\begin{align*}
>  \min_{(\beta, \mu) \in \mathscr{C}}\;& \mathbb{KL}\left( \mathcal{Q}_{\beta, \mu} \left\|\right. \mathcal{P}_{\Phi} \right) \\[5pt]
>  \text{s.t. }\;&\, \mu_{i,j}(s_{i,j}) = \mathbb{E}_{ \mathcal{Q}_{\beta, \mu} }\left[  \mathbb{1}_{s_{i,j}}\{S_{i,j}\} \right],\;\; \forall ij\in E(T), \forall s_{i,j}\in \text{Val}(S_{i,j}) \\[5pt] 
>  &\beta_{i}(c_{i}) = \mathbb{E}_{ \mathcal{Q}_{\beta, \mu} }\left[  \mathbb{1}_{c_{i}}\{C_{i}\} \right],\;\; \forall i \in V(T), \forall c_{i}\in \text{Val}(C_{i}).
>\end{align*}
>$$
>where 
>- $\beta := \left(\beta_{i}, i\in V(T)\right)$,  
>- $\mu := \left(\mu_{i,j}, \, ij\in E(T)\right),$
>- $\mathcal{Q}_{\beta, \mu}$ is a **clique tree measure** $$\mathcal{Q}_{\beta, \mu}(\mathcal{X}) := \frac{\prod_{i\in V(T)}\beta_{i}}{\prod_{ij\in E(T)}\mu_{i,j}},$$
>- and the **prior distribution** is of the factorized form with initial potentials $$\mathcal{P}_{\Phi}(\mathcal{X}) := \frac{1}{Z}\prod_{\phi \in \Phi}\phi(U_{\phi})$$

^e2fab5

- [[Maximum Entropy Learning]]
- [[Marginal Polytope and Local Consistent Polytope]]
- [[Clique Tree and Graph and Running Intersection Property]]
- [[Clique Tree Calibration]]
- [[Kullback-Leibler Divergence]]

>[!important] Definition
>The **maximum entropy learning** of the exact inference problem can be formulated in **compact form**
>$$
>\begin{align*}
>  \min_{(\beta, \mu) \in \mathscr{C}}\;& \mathbb{KL}\left( \mathcal{Q}_{\beta, \mu} \left\|\right. \mathcal{P}_{\Phi} \right) \\[5pt]
>  \text{s.t. }\;&\, (\beta, \mu)\in \mathbb{M}(\mathcal{G})
>\end{align*}
>$$


### Existence and Uniqueness of Optimal Solution

>[!important] Theorem
>If $T$ is an **$I$-map** of  $\mathcal{P}_{\Phi}$, then there exists a **unique solution** to the **maximal entropy learning** problem above.

- [[I-Map and Independence Assertion]]
- [[Soundness and Faithfulness of D-Separation in Bayesian Net]]
- [[Soundness and Faithfulness of Separation in Markov Net]]

>[!info]
>The optimal solution can be found via **belief propagation algorithm** or **belief update algorithm**.

- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Sum-Product Belief-Update Message Passing Algorithm for Clique Tree]]

## Explanation

>[!quote]
>Recall that the end product of **belief propagation** is a **calibrated cluster tree**. Also recall that a calibrated set of beliefs for the cluster tree represents a **distribution**. In **exact inference** we find a set of *calibrated beliefs* that represent $\mathcal{P}_{\Phi}(\mathcal{X})$. That is, we find beliefs that *match the distribution* represented by given set of **initial potentials**. Thus, we can view exact inference as searching over the set of distributions $\mathcal{Q}$ that are *representable* by the *cluster tree* to find a distribution $\mathcal{Q}^{*}$ that **matches** $\mathcal{P}_{\Phi}$.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 382

- [[Clique Tree Invariant of Sum Product and Reparameterization of PGM]]
- [[Clique Tree Calibration]]

>[!important] 
>In solving this optimization problem, we conceptually **examine different configurations of beliefs** that satisfy the **marginal consistency constraints**, and we select the configuration that *minimize the objective*.

## Maximum Entropy Problem via Energy Functional Form

![[Energy Functional for Probabilistic Graphical Model#^c01c98]]

![[Variational Inference for Clique Tree#^5fe294]]

- [[Energy Functional for Probabilistic Graphical Model]]
- [[Evidence Lower Bound]]
- [[Variational Inference for Clique Tree]]
- [[Stationary Point of Bethe Variational Inference Problem]]

>[!important] Definition
>The **maximum entropy learning** of the exact inference problem can be formulated in **compact form**
>$$
>\begin{align*}
>  \max_{(\beta, \mu) \in \mathscr{C}}\;& \mathcal{L}(\mathcal{Q}_{\beta, \mu}, \Phi; \mathcal{X}) \\[5pt]
>  \text{s.t. }\;&\, (\beta, \mu)\in \mathbb{M}(\mathcal{G})
>\end{align*}
>$$




-----------
##  Recommended Notes and References

- [[Maximum Entropy Learning]]
- [[Maximum Entropy Learning of Exponential Family]]
- [[Information Projection and Moment Projection]]

- [[Sum-Product Variable Elimination]]


- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network Distribution to Graph]]

- [[Convex Optimization Problem]]
- [[Kullback-Leibler Divergence]]

- [[Probabilistic Graphical Models by Koller]] pp 382 - 386
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 56-58, 73 - 92
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
