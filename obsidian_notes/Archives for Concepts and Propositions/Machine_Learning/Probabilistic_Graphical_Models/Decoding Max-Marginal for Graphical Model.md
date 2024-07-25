---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/theory
keywords:
  - max_product
  - probabilistic_graphical_model
  - max_marginal
topics: 
name: Decoding Max-Marginal for Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Decoding Max-Marginal for Graphical Model

![[Max-Product Variable Elimination#^ad6150]]

>[!important] Proposition
>The following two conditions are **equivalent**:
>- The set of node beliefs $$\{ \text{MaxMarg}_{\hat{\mathcal{P}}_{\Phi}}(X_{i}),\;\; X_{i} \in \mathcal{X} \}$$ is **unambiguous** with $$x_{i}^{*} = \arg\max_{x_{i}}\text{MaxMarg}_{\hat{\mathcal{P}}_{\Phi}}(X_{i}).$$ the **unique optimizing value** for $X_{i}$
>- $\hat{\mathcal{P}}_{\Phi}$ has a **unique MAP assignment** $$(x_{1}^{*} \,{,}\ldots{,}\,x_{n}^{*}).$$

>[!info]
>Thus, if there are no ties in any of the calibrated node beliefs, we can find the **unique MAP assignment** by **locally optimizing** the *assignment* to each variable **separately**.
>
>For **ambiguous** case, we can use the **Traceback algorithm** in [[Max-Product Variable Elimination]]


>[!important] Definition
>Let $\beta_{i}(C_{i})$ be a belief in a *max-calibrated clique tree*. 
>
>We say that an *assignment* $\xi^{*}$ has the **local optimality property** if, for each clique $C_{i}$ in the tree, we have that 
>$$
>\xi^{*}\big|_{C_{i}} \in \arg\max_{c_{i}}\beta_{i}(c_{i}).
>$$ 
>that is, the *assignment to* $C_{i}$ in $\xi^{*}$ *optimizes* the $C_{i}$ *belief*.

>[!important] Definition
>The task of finding a *locally optimal assignment* $\xi^{*}$ given a *max-calibrated* set of beliefs is called the **decoding task**.


### Clique Tree Measure and Local Optimality Property 

>[!important] Theorem
>Let $\beta_{i}(C_{i})$ be a set of **max-calibrated** *beliefs* in a **clique tree** $T$, with $\mu_{i,j}$ the associated *sepset beliefs*. Let $\mathcal{Q}_{T}$ be the **clique tree measure** defined as $$\mathcal{Q}_{T}(\mathcal{X}) = \frac{\prod_{i\in V(T)}\,\beta_{i}(C_{i})}{\prod_{ij \in E(T)}\,\mu_{i,j}(S_{i,j})}.$$
>
>Then an assignment $\xi^{*}$ satisfies the **local optimality property** relative to the beliefs $\{ \beta_{i}(C_{i}), \; i\in V(T) \}$, i.e. $$\xi^{*}\big|_{C_{i}} \in \arg\max_{c_{i}}\beta_{i}(c_{i}),$$  *if and only if* it is the **global MAP assignment** relative to $\mathcal{Q}_{T}$ $$\xi^{*} = \arg\max_{\xi} \mathcal{Q}_{T}(\xi).$$

- [[Maximum A Posteriori Probability Query of Graphical Model]]


## Explanation

>[!quote]
>For generic probability measures, the **assumption of unambiguity** is not overly stringent, since we can always **break ties** by introducing a slight *random perturbation* into all of the factors, making all of the elements in the joint distribution have slightly different probabilities. However, if the distribution has special structure — **deterministic relationships** or **shared parameters** — that we want to preserve, this type of ambiguity may be *unavoidable*.
>
>--  [[Probabilistic Graphical Models by Koller]] pp 566




-----------
##  Recommended Notes and References


- [[Max-Product Message Passing for Clique Tree]]
- [[Max-Product Belief Update for Clique Tree]]
- [[Max-Product Variable Elimination]]

- [[Clique Tree Calibration]]
- [[Clique Tree and Graph and Running Intersection Property]]

- [[Tree-Order Relation]]
- [[Root and Rooted Tree]]
- [[Tree Graph and Forest]]


- [[Probabilistic Graphical Models by Koller]] pp 565
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
