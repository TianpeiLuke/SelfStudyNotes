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
topics:
  - probabilistic_graphical_model
name: Maximum Entropy Learning for Approximate Inference in PGM
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Maximum Entropy Learning for Approximate Inference in PGM

### Maximum Entropy Learning for Exact Inference

![[Maximum Entropy Learning of Clique Tree PGM#^f81f88]]

![[Maximum Entropy Learning of Clique Tree PGM#^e2fab5]]

>[!important] Definition
>Let $\mathcal{P}_{\Phi}$ be a *Bayesian network* or *Markov network* that *factorizes* according to $\mathcal{G}$, and $\Phi$ be a set of *factors* in $\mathcal{P}$.
>
>The **maximum entropy learning** of the exact inference on $\mathcal{P}_{\Phi}$ can be formulated in **compact form**
>$$
>\begin{align*}
>  \min_{(\beta, \mu) \in \mathscr{C}}\;& \mathbb{KL}\left( \mathcal{Q}_{\beta, \mu} \left\|\right. \mathcal{P}_{\Phi} \right) \\[5pt]
>  \text{s.t. }\;&\, (\beta, \mu)\in \mathbb{M}(\mathcal{G})
>\end{align*}
>$$
>
>This is equivalent to **maximize the energy functional (ELBO)**
>$$
>\begin{align*}
>  \max_{(\beta, \mu) \in \mathscr{C}}\;& \mathcal{L}(\mathcal{Q}_{\beta, \mu}, \Phi; \mathcal{X}) = \left\langle  \theta_{\Phi}\,,\,\beta \right\rangle + H(\mathcal{Q}_{\beta, \mu}) \\[5pt]
>  \text{s.t. }\;&\, (\beta, \mu)\in \mathbb{M}(\mathcal{G})
>\end{align*}
>$$
>where $\mathbb{M}(\mathcal{G})$ is the **marginal polytope** associated with graph $\mathcal{G}$.

- [[Marginal Polytope and Local Consistent Polytope]]
- [[Maximum Entropy Learning of Clique Tree PGM]]


### Exact Inference on Clique Tree

>[!important] 
>The idea behind the **belief propagation** and **belief update algorithm** is to
>1. **identify** that the **objective** *energy functional* $\mathcal{L}$ or the *entropy functional* $H$ has a **tractable, factorized** form $\hat{\mathcal{L}}$.
>2. **identify** that the constraints on **global consistency** (i.e. the marginal polytope) $\mathbb{M}(\mathcal{G})$ is **equivalent** to the **local consistency** (i.e. local consistency polytope) $\mathbb{L}(\mathcal{G})$
>   
>In other word, for **calibrated clique tree**, the following optimization problem is the solve the original maximum entropy learning problem and the inference is **exact**.   

>[!important] Definition
>For  clique tree $\mathcal{T}$ , the maximum entropy learning problem above can be reformulated as the **variational inference problem** 
>$$
>\begin{align*}
>  \max_{(\beta, \mu) \in \mathscr{C}}\;& \hat{\mathcal{L}}(\mathcal{Q}_{\beta, \mu}, \Phi; \mathcal{X}) \\[5pt]
>  \text{s.t. }\;&\, (\beta, \mu)\in \mathbb{L}(\mathcal{T})
>\end{align*}
>$$
>where $\mathbb{L}(\mathcal{T}) = \mathbb{M}(\mathcal{T})$ is the **local consistent polytope**.

### Approximate the Entropy or Energy Functional and Constraint Set

>[!important] 
>For cluster graph $\mathcal{G}$, the idea behind the **belief propagation** and **belief update algorithm** is to
>1. **approximate** the **objective** *energy functional* $\mathcal{L}$ or the *entropy functional* $H$ by **tractable, factorized** form $\hat{\mathcal{L}}$.
>2. **relax** of the constraints on **global consistency** (i.e. the marginal polytope) $\mathbb{M}(\mathcal{G})$ with the **local consistency** (i.e. local consistency polytope) $\mathbb{L}(\mathcal{G})$

>[!quote]
>**Clique tree calibration** optimizes the *factored energy functional*, which is **exact for clique trees**. The optimization is performed over the space of *calibrated clique potentials*. For clique trees, any set of *calibrated clique potentials* must arise from a real distribution, and so this space is precisely the **marginal polytope**. As a consequence, both our **objective** and our **constraint space** are *exact*, so our solution represents the exact posterior.


>[!important] Definition
>The **Bethe variational inference problem** can be formulated as
>$$
>\begin{align*}
>  \max_{(\beta, \mu) \in \mathscr{C}}\;& \hat{\mathcal{L}}(\mathcal{Q}_{\beta, \mu}, \Phi; \mathcal{X}) \\[5pt]
>  \text{s.t. }\;&\, (\beta, \mu)\in \mathbb{L}(\mathcal{G})
>\end{align*}
>$$
>where $\mathbb{L}(\mathcal{G}) \supseteq \mathbb{M}(\mathcal{G})$ is the **local consistent polytope**.


- [[Bethe Entropy Approximation and Factorized Energy Functional]]
- [[Bethe Variational Inference for Clique Tree]]
- [[Variational Inference for Clique Tree]]
- [[Loopy Belief Propagation Algorithm for Cluster Graph]]

>[!quote]
>**Cluster-graph (loopy) belief propagation** optimizes the *factored energy functional*, which is **approximate for loopy graphs**. The optimization is performed over the space of *locally consistent* pseudo-marginals, which is a **relaxation** of the marginal polytope. Thus, both the objective and the constraint space are approximate.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 473


### Approximate the Message

>[!important] 
>The idea behind the **expectation propagation** is to
>1. **approximate** the *energy functional* $\mathcal{L}$ or the *entropy functional* $H$ by **tractable, factorized** objective function $\hat{\mathcal{L}}$.
>2. **project** the *marginal distribution* of each sepset $S_{i,j}$ into an *exponential family* with *sufficient statistic* $T_{i,j}$
>3. **replace** the *global consistency constraints* (i.e. the marginal polytope) $\mathbb{M}(\mathcal{G})$  with the **expectation consistent constraints** $\mathbb{E}(\mathcal{G}; T)$ on each sepset.



>[!important] Definition
>The **expectation propagation inference problem** can be formulated as
>$$
>\begin{align*}
>  \max_{(\beta, \mu) \in \mathscr{C}}\;& \hat{\mathcal{L}}(\mathcal{Q}_{\beta, \mu}, \Phi; \mathcal{X}) \\[5pt]
>  \text{s.t. }\;&\, (\beta, \mu)\in \mathbb{E}(\mathcal{G}; T)
>\end{align*}
>$$
>where $\mathbb{E}(\mathcal{G}; T)$ consists of **expectation consistency constraints** with *sufficient statistic* $T_{i,j}$ for each edge $ij\in E(\mathcal{G})$.
>
>- In particular, assume that for each sepset $S_{i,j}$, the corresponding marginal distribution $\mathcal{Q}_{i,j} \in \mathscr{P}_{T_{i,j}}$ is from an *exponential family of distributions*, with *sufficient statistics* $T_{i,j}$. Then the **expectationi consistent constraint** is
>$$
>\mathbb{E}_{ \mu_{i,j} }\left[  T_{i,j}(S_{i,j}) \right] = \mathbb{E}_{ \beta_{j} }\left[  T_{i,j}(S_{i,j}) \right],\quad \forall ij\in E(\mathcal{G})
>$$

- [[Exponential Family of Distributions]]
- [[Factorized Message for Approximate Belief Propagation]]
- [[Sum-Product Expectation Propagation Algorithm]]
- [[Sum-Product Belief-Update Expectation Propagation Algorithm]]
- [[Expectation Propagation and Exponential Family Messages]]
- [[Variational Inference Formulation of Expectation Propagation]]

>[!quote]
>**Expectation propagation** over clique trees optimizes the *factored energy functional*, which is the exact objective in this case. However, the *constraints* define a space of *pseudo-marginals* that are not even entirely consistent — **only their moments are required to match**. Thus, the constraint space here is a **relaxation** of our constraints, even when the structure is a tree. Expectation propagation over *cluster graphs* adds, on top of these, all of the *approximations* induced by belief propagation.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 474


### Approximate the Family of Feasible Distributions

>[!important] Definition
>The **structured variational inference problem** can be formulated as
>$$
>\begin{align*}
>  \max_{\mathcal{Q} \in \mathscr{M}}\;& \mathcal{L}(\mathcal{Q}, \Phi; \mathcal{X}) \\[5pt]
>  \text{s.t. }\;&\, \mathcal{Q} \in \mathscr{M}
>\end{align*}
>$$
>or
>$$
>\begin{align*}
>  \min_{\mathcal{Q} \in \mathscr{M}}\;& \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}_{\Phi} \right) \\[5pt]
>  \text{s.t. }\;&\, \mathcal{Q} \in \mathscr{M}
>\end{align*}
>$$
>where $\mathscr{M}$ is a *family of probability distributions* with **tractable form**.

- [[Structured Variational Approximation]]
- [[Mean Field Approximation]]

>[!quote]
>Finally, **structured variational methods** optimize the *exact* factored energy functional, for a class of distributions that is (generally) *less expressive* than necessary to encode $P_{\Phi}$. As a consequence, the *constraint space* is actually a **tightening** of our original constraint space. Because the objective function is exact, the result of this optimization provides a **lower bound** on the value of the exact optimization problem. As we will see, such bounds can play an important role in the context of learning.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 474


## Explanation

>[!quote]
>This general framework opens the door to the development of many other approaches. Each of the methods that we described here involves a **design choice** in three dimensions: the **objective function** that we aim to optimize, the **space of (pseudo-)distributions** over which we perform our optimization, and the **algorithm** that we choose to use in order to perform the optimization. Although these three decisions affect each other, *these dimensions are sufficiently independent* that we can improve each one separately.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 474



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
