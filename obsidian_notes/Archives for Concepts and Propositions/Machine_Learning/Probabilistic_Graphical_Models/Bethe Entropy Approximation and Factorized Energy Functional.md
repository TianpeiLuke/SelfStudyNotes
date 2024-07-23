---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/theory
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/inference
keywords:
  - probabilistic_graphical_model
  - bethe_entropy_approximation
  - factorized_energy_functional
  - factorized_elbo
topics:
  - probabilistic_graphical_model
name: Bethe Entropy Approximation and Factorized Energy Functional
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Bethe Entropy Approximation and Factorized Energy Functional

![[Maximum Entropy Learning of Clique Tree PGM#^c01c98]]

### Cluster Tree 

>[!important] Definition
>Given a  *cluster tree* $T$ with a set of *beliefs* $(\beta, \mu)$, and an *assignment* $\alpha$ that maps *factors* in $\mathcal{P}_{\Phi}$ to *clusters* in $T$, we define the **factorized energy functional**  or **factorized evidence lower bound** as
>$$
>\hat{\mathcal{L}}(\mathcal{Q}_{\beta,\mu}, \Phi; \mathcal{X}) := \sum_{i\in V(T)}\mathbb{E}_{\beta_{i}}\left[\log \psi(C_{i})\right] + \sum_{i\in V(T)}H_{\beta_{i}}(C_{i}) - \sum_{ij \in E(T)}H_{\mu_{i,j}}(S_{i,j})
>$$
>where 
>- $C_{i}$ are *cliques* in $T$ and $\mu_{i}$ is the corresponding *clique belief* for each $i\in V(T)$;
>- $S_{i,j} = C_{i} \cap C_{j}$ are *sepsets* in $T$ and $\mu_{i,j}$ is the corresponding *sepset belief*, for each edge $ij\in E(T)$.
>- $\psi_{i}$ is the initial potential assigned to $C_{i}$, i.e. $$\psi_{i}(C_{i}) = \prod_{\phi: \alpha(\phi) = i}\phi.$$

^2acf67

- [[Clique Tree Calibration]]
- [[Maximum Entropy Learning of Clique Tree PGM]]

>[!important] Definition
>Given a  **cluster tree** $T$ with a set of *beliefs* $(\beta, \mu)$,, the **Bethe entropy approximation**
>$$
>\hat{H}_{\text{Beth}}(\mathcal{Q}_{\beta, \mu}):=  \sum_{i\in V(T)}H_{\beta_{i}}(C_{i}) - \sum_{ij \in E(T)}H_{\mu_{i,j}}(S_{i,j})
>$$
>where 
>- $C_{i}$ are *cliques* in $T$ and $\mu_{i}$ is the corresponding *clique belief* for each $i\in V(T)$;
>- $S_{i,j} = C_{i} \cap C_{j}$ are *sepsets* in $T$ and $\mu_{i,j}$ is the corresponding *sepset belief*, for each edge $ij\in E(T)$.

>[!info]
>In general the entropy functional on $\mathcal{Q}$ cannot be factorized. 
>
>The following factorized entropy functional provides an approximation of the $H_{\mathcal{Q}}$ 

### Cluster Graph


>[!important] Definition
>For a **calibrated cluster graph** $\mathcal{G}$, there are two layers:
>- *clusters* $C_{\phi}$ corresponding to factors $\phi \in \Phi$
>- *univariate clusters* $X_{i}$
>
>Define a set of *beliefs*
>- the *factor beliefs* $(\beta_{\phi}(C_{\phi}), \phi\in \Phi)$,
>- the *univariate beliefs* $(\beta_{i}(X_{i}))$.
>
>Then the **Bethe entropy approximation** has the form
>$$
>\hat{H}_{\text{Beth}}(\mathcal{Q}_{\beta,\mu}):= \sum_{\phi \in \Phi}H_{\beta_{\phi}}(C_{\phi})  - \sum_{i}(d_{i} - 1)H_{\beta_{i}}(X_{i}). 
>$$  
>And the **factorized energy functional** has the form
>$$
>\hat{\mathcal{L}}(\mathcal{Q}_{\beta}, \Phi; \mathcal{X}) := \sum_{\phi \in \Phi}\mathbb{E}_{\beta_{\phi}}\left[\log \phi\right] +  \sum_{\phi \in \Phi}H_{\beta_{\phi}}(C_{\phi})  - \sum_{i}(d_{i} - 1)H_{\beta_{i}}(X_{i})
>$$


## Explanation

>[!info]
>For tree-structured graph $T$, each clique is a pair of nodes $C_{i} = \{i,j\}$ along edge $ij\in E(T)$ with $i \le j$, and the sepset is each node itself $S_{i,j} = \{ i \}$




## Bethe Approximation on Tree-Structured Graph


>[!important] Definition
>Given a  **tree** $T$ with a set of *potentials* $(\tau_{i}, \tau_{i,j})$, the **Bethe entropy approximation**
>$$
>\hat{H}_{\text{Beth}}(\mathcal{Q}_{\tau}):= \sum_{i\in V}H_{i}(\tau_{i}) - \sum_{ij\in E}I_{ij}(\tau_{i,j}\;\|\;\tau_{i}\,\tau_{j}) 
>$$
>where 
>- the **Shanon entropy** $$H_{i}(\tau_{i}) = \mathbb{E}_{ \tau_{i} }\left[  -\log \tau_{i} \right]$$
>- the **mutual information** $$I_{ij}(\tau_{i,j}\;\|\;\tau_{i}\,\tau_{j}) = \mathbb{E}_{ \tau_{i,j} }\left[ \log \left(\frac{\tau_{i,j}}{\tau_{i}\,\tau_{j}}\right) \right]$$
>  
>This is **equivalent** to the form
>$$
>\hat{H}_{\text{Beth}}(\mathcal{Q}_{\tau}):= \sum_{ij\in E}H_{ij}(\tau_{i,j})  - \sum_{i\in V}(d_{i} - 1)H_{i}(\tau_{i}) 
>$$  
>This form is the same as the definition.

 - [[Shannon Entropy]]
 - [[Mutual Information]]




-----------
##  Recommended Notes and References


- [[Bethe Variational Inference for Clique Tree]]
- [[Variational Inference for Clique Tree and Cluster Graph]]

- [[Evidence Lower Bound]]
- [[Variational Inference vs EM Algorithm]]

- [[Cluster Graph and Family Preservation]]
- [[Clique Tree and Graph and Running Intersection Property]]

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network Distribution to Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 386
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 79 - 81
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
