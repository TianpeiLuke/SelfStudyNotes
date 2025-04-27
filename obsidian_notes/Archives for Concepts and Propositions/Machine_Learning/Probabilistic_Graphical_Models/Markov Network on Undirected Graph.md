---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/theory
  - markov_random_field
  - MRF
  - markov_network
keywords:
  - markov_network
  - markov_random_field
topics:
  - probabilistic_graphical_model
name: Markov Network on Undirected Graph
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Markov Network on Undirected Graph

### Factors

>[!important] Definition
>Let $X$ be a set of *random variables*. 
>
>We define a **factor** as a function $\phi: \mathcal{X} \to \mathbb{R}$ where $\mathcal{X}$ is the domain of $X$.
>
>- A factor is **non-negative** if all its *entries* are *non-negative*.
>- The set of variables $X$ is called the **scope** *of factor* and denoted as $\text{scope}(\phi).$

^2a1ab6

>[!info]
>- in *Bayesian network*, a [[Local Probabilistic Models]] is a **probability measure** (on $X_{i}$) given *each assignment* of $X_{Pa(i)}$
>$$
>\sum_{x\in \mathcal{X}}\mathcal{P}(X_{i} = x | X_{Pa(i)} = x_{-i}) = 1
>$$
>The *influence* in a locally probability model (CPD) is **directional** and the measure is completed determined by the assignment on $X_{Pa(i)}$, not vice versa.
>- On the other hand, a factor need not satisfies the *normalization constraint* i.e.
>$$
>\sum_{x\in \mathcal{X}}\phi(X_{i}= x; X_{-i} = x_{-i}) \neq 1.
>$$ 
>This is because we do not have the notion of directionality as well as "parent node". The **influence** between random variables in a factor is **mutual and symmetric**.

>[!quote]
>A **factor** is only **one contribution** to the **overall joint distribution**. The distribution *as a whole* has to take into consideration the contributions from *all of the factors involved*.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 108




>[!important] Definition
>Let $X, Y, Z$ be three sets of random variables, and let $\phi_{1}(X, Y)$ and $\phi_{2}(Y, Z)$ are two factors. 
>
>We define the **factor product** as a factor $\psi: \mathcal{X} \times \mathcal{Y} \times \mathcal{Z} \to \mathbb{R}$ so that
>$$
>\psi(X, Y, Z) := \phi_{1}(X, Y) \, \phi_{2}(Y, Z),\quad \forall X\in \mathcal{X}, Y\in \mathcal{Y}, Z \in \mathcal{Z}.
>$$
>The key aspect to note about this definition is the fact that the two factors $\phi_{1}$ and $\phi_{2}$ are multiplied in a way that “*matches up*” the common part $Y$.

^421079

### Markov Network

>[!important] Definition
>Let $\mathcal{H} = (\mathcal{V}, \mathcal{E})$ be an (undirected) graph.
>
>The *joint probability density function* $\mathcal{P}_{\Phi}$  with factors $$\Phi := \left\{ \phi_{1} \,{,}\ldots{,}\, \phi_{K}\right\} $$ is said to **factorize according to $\mathcal{H}$** if
>$$
> P(X_{v}\,,\, v\in \mathcal{V}) = \frac{1}{Z}\prod_{k=1}^{K}\phi_{k}(X_{D_{k}})
>$$
>where
>-  the **partition function** is defined as $$Z = \sum_{x \in \mathcal{X}}\prod_{k=1}^{K}\phi_{k}(X_{D_{k}}),$$ where the summation is over the entire sample space $\mathcal{X}$
>- Each $D_{k}$ is a **complete subgraph** for $\mathcal{H}$, called the **clique subgraph.**
>- Each $\phi_{k}(X_{D_{k}})$ is called a **clique potential.**
>

- [[Complete Graph Clique and Triangle]]
- [[Gibbs Measure and Energy-based Model]]
- [[Exponential Family of Distributions]]
- [[Log-Partition Function and Score Function of Graphical Models]]




>[!important] Definition
>A **Markov network** is a pair $(\mathcal{H}, P_{\Phi})$ where $P_{\Phi}$ *factorizes according to* $\mathcal{H}$, and where $P_{\Phi}$ is specified as a set of *clique potentials* associated with cliques in $\mathcal{H}$. 


## Explanation

>[!info]
>As we *dropped the probabilistic notion* on the factor definition, a factor is merely an convenient tool for **local computation**. 
>
>In other word, in Markov network, the *probabilistic information* is only maintained in **global sense**. 
>- At each **local sub-system**, no probabilistic notion and constraints are required.   


>[!info]
>$$
>\text{ local probabilistic model } \subseteq \text{ factor }
>$$
>as we define
>$$
>\phi(X_{i}, X_{Pa(i)}) := \mathcal{P}(X_{i}\,|\, X_{Pa(i)}).
>$$


>[!quote]
>As we showed, these independencies *cannot be naturally captured in a Bayesian network*: any Bayesian network I-map of such a distribution would necessarily have extraneous edges, and it would not capture at least one of the desired independence statements. More broadly, a Bayesian network requires that we **ascribe a directionality** to **each influence**. In this case, the **interactions** between the variables seem **symmetrical**, and we would like a model that allows us to represent these **correlations without forcing a specific direction to the influence**.
>
>A representation that implements this intuition is an **undirected graph**. As in a Bayesian network, the nodes in the graph of a **Markov network** represent the variables, and the edges Markov network correspond to a notion of *direct probabilistic interaction* between the neighboring variables an interaction that is **not mediated by any other variable** in the network.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 103

>[!quote]
>Although it can be used without loss of generality, the **parameterization** using **maximal clique potentials** generally *obscures structure* that is present in the original set of factors.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 109



>[!info]
>Given a set of conditional independent assertions $\mathcal{I}$, it is not necessarily that there exists a graph $\mathcal{G}$ so that $$\mathcal{I}(\mathcal{G}) = \mathcal{I}.$$
>
>A *Markov network* provides an **extension** of the *Bayesian network* to include broader, *symmetrical interactions* that cannot be modeled by BN in compact manner. 

- [[Perfect Map for Independence Assertions]]

## Consistent Information Transfer within Markov Network 

>[!info]
>Unlike the [[Bayesian Network on Directed Acyclic Graph]], the information transfer between factors do not follow a fixed ordering. 
>
>In order to maintain consistency in **global level**,  if a given **common random variable** are included in *both factors*, there need additional constraints on both factors so that their information on the same variable is **consistent**
>$$
>\sum_{y\in \mathcal{Y}}\phi_{1}(X \in A, y) = \sum_{z\in \mathcal{Z}}\phi_{2}(X \in A, z), \; \forall A\in \mathscr{F}_{X}
>$$

>[!info]
>Note that a Bayesian network does not require additional **consistency** between the neighboring [[Local Probabilistic Models]]  (CPDs) since the **entire probabilistic information** on a random variable $X_{i}$ is kept in **one factor only**.  
>
>In other word, the CPD $$\mathcal{P}(X_{i} \,|\,X_{Pa_{i}})$$ is the only factor that keep information on $X_{i}$. The other factors only **react** to the *assignment* of $X_{i}$ *deterministically.*
>
>In Markov network, the **multiple factors** would keep a copy of $X_{i}$ on *their own*, thus there could be potentially risk for *inconsistency* among *multiple factors*.

>[!info]
>The benefit of Bayesian network over Markov network is that the **local model keep all probabilistic information** and the global model can be easily assembled via factorization. 
>
>This is not the case for Markov network. In order to maintain global consistency in Markov network, **coordination** and **consistency alignment** is required in every step of inference and message-passing. 




-----------
##  Recommended Notes and References


- [[Bayesian Network on Directed Acyclic Graph]]


- [[Graph]]
- [[Probabilistic Graphical Models]]


- [[Probabilistic Graphical Models by Koller]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning Foundations and Concepts by Bishop]] pp 327
- [[Deep Learning by Goodfellow]] pp 556 - 558