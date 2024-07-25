---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/theory
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/representation
keywords:
  - clique_tree_calibration
  - clique_tree_measure
  - reparameterization
  - clique_tree_invariant
topics:
  - probabilistic_graphical_model
name: Clique Tree Measure for Sum-Product and Reparameterization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Clique Tree Measure for Sum-Product and Reparameterization

![[Sum-Product Message Passing Algorithm for Clique Tree#^1e148a]]

![[Sum-Product Message Passing Algorithm for Clique Tree#^d4e300]]

### Convergence Distribution

>[!info]
>At calibration, we have $$\beta_{i} = \psi_{i}\,\cdot\,\prod_{k\in N(i)}\delta_{k\to i}$$
>Also 
>$$
>\begin{align*}
>\mu_{i,j}(S_{i,j}) &= \sum_{C_{i} \setminus S_{i,j}}\beta_{i}(C_{i})\\
>&= \sum_{C_{i} \setminus S_{i,j}}\psi_{i}\,\cdot\,\prod_{k\in N(i)}\delta_{k\to i}\\
>&=  \sum_{C_{i} \setminus S_{i,j}}\psi_{i}\,\cdot\,\delta_{j\to i}\prod_{k\in (N(i) - j)}\delta_{k\to i}\\
>&= \delta_{j\to i}\sum_{C_{i} \setminus S_{i,j}}\psi_{i}\,\cdot\,\prod_{k\in (N(i) - j)}\delta_{k\to i}\\
>&= \delta_{j\to i}\,\delta_{i\to j}
>\end{align*}
>$$

- [[Sum-Product Message Passing Algorithm for Clique Tree]]

>[!important] Proposition
>At **convergence** of the **belief propagation algorithm**, we have 
>$$
>\hat{\mathcal{P}}_{\Phi}(\mathcal{X}) = \frac{\prod_{i\in V(T)}\,\beta_{i}(C_{i})}{\prod_{ij \in E(T)}\,\mu_{i,j}(S_{i,j})}
>$$ 

### Reparameterization of PGM

>[!important] Definition 
>From the equation
>$$
>\hat{\mathcal{P}}_{\Phi}(\mathcal{X}) = \frac{\prod_{i\in V(T)}\,\beta_{i}(C_{i})}{\prod_{ij \in E(T)}\,\mu_{i,j}(S_{i,j})},
>$$ 
>the clique $\{\beta_{i}, i\in V(T)\}$ and $\{ \mu_{i,j},\; ij\in E(T) \}$  provide a **reparameterization** of the *unnormalized measaure*.
>
>This property is called the **clique tree invariant.**

^d162e9


### Clique Tree Measure

![[Clique Tree Calibration#^d56b22]]

![[Clique Tree Calibration#^ec693c]]

>[!quote]
>A **calibrated clique tree** is more than simply a **data structure** that stores the results of probabilistic inference for all of the cliques in the tree. As we now show, it can also be viewed as an **alternative representation** of the measure $\hat{\mathcal{P}}_{\Phi}(\mathcal{X})$.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 361


>[!important] Definition
>We define the **measure** *induced by a calibrated tree* $T$ to be
>$$
>\mathcal{Q}(\mathcal{X}) = \frac{\prod_{i\in V(T)}\,\beta_{i}(C_{i})}{\prod_{ij \in E(T)}\,\mu_{i,j}(S_{i,j})},
>$$ 
>where for any $ij\in E(T)$, $$\mu_{i,j}(S_{i,j}) = \sum_{C_{i} \setminus S_{i,j}}\beta_{i}(C_{i}) = \sum_{C_{j} \setminus S_{i,j}}\beta_{j}(C_{j}).$$

- [[Clique Tree Calibration]]

>[!info]
>$$
>\log \mathcal{Q}(\mathcal{X}) = \sum_{i\in V(T)}\beta_{i}(C_{i}) - \sum_{ij\in E(T)}\mu_{i,j}(S_{i,j})
>$$


>[!important] Theorem
>Let $T$ be a *clique tree* over $\Phi$, and let $\beta_{i}(C_{i})$ be a set of **calibrated potentials** for $T$.
>
>Then $$\hat{\mathcal{P}}_{\Phi} \propto \mathcal{Q}$$ *if and only if*
>- for each $i\in V(T)$, we have $$\beta_{i}(C_{i}) \propto \hat{\mathcal{P}}_{\Phi}(C_{i}).$$

## Explanation

>[!important]
>We can view the **clique tree** as an **alternative representation** of the **joint measure**, one that directly reveals the **clique marginals**.


>[!important]
>It is important to see that for **exponential family** $\mathcal{P}_{\Phi}$, the clique tree invariant and **reparameterization** corresponds to the transform from *canonical parameterization* to **mean parameterization**. 
>
>That is, both *clique belief* and *sepset beliefs* for *calibrated clique tree measure* can be seen as the *expectation of indicator function* on *cliques and sepsets*
>$$
>\begin{align*}
>\beta_{i} &= \mathbb{E}_{ \mathcal{P}_{\Phi} }\left[ \; \mathbb{1}\{C_{i}\} \;\right] = \mathcal{P}_{\Phi}(C_{i})\\
>\mu_{i,j} &= \mathbb{E}_{ \mathcal{P}_{\Phi} }\left[ \; \mathbb{1}\{S_{i,j}\} \;\right] = \mathcal{P}_{\Phi}(S_{i,j})
\end{align*}
>$$

- [[Exponential Family of Distributions]]
- [[Exponential Family and Convex Duality]]
- [[Characteristic Function of Set]]

## Max-Product Measure

- [[Clique Tree Invariant of Max-Product and Reparameterization]]



-----------
##  Recommended Notes and References


- [[Clique Tree Calibration]]
- [[Clique Tree and Graph and Running Intersection Property]]

- [[Sum-Product Message Passing Algorithm for Clique Tree]]
- [[Correctness of Belief Propagation for Clique Tree]]
- [[Belief-Update Message Passing Algorithm for Clique Tree]]


- [[Probabilistic Graphical Models by Koller]] pp 361 - 363
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 89
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
