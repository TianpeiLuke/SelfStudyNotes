---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/algorithm
keywords:
  - sum_product
  - message_passing
  - clique_tree
  - belief_propagation
  - dynamic_programming
topics:
  - probabilistic_graphical_model
name: Sum-Product Message Passing Algorithm for Clique Tree
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Sum-Product Message Passing or *Belief Propagation* for Clique Tree

>[!important] Definition
>Let $T$ be a **clique tree** with cliques $C_{1} \,{,}\ldots{,}\, C_{k}$. 
>
>Denote the *clique index* corresponding some factor $\phi\in \Phi$ as $\alpha(\phi)$, i.e. $$\alpha(\phi) = j \; \iff \; \text{scope}[\phi] \subseteq C_{j}$$
>
>- We define the **initital potential** of $C_{j}$ as $$\psi_{j}(C_{j}) = \prod_{\phi: \alpha(\phi) = j}\phi.$$
>	- Note that each factor is assigned to exactly one clique so $$\prod_{\phi\in \Phi}\phi = \prod_{j}\psi_{j}$$
>- Let $C_{r}$ be the selected **root clique.** 
>- For each clique $C_{i}$, denote the indices of **cliques that are neighbors** of $C_{i}$ as $$N(i) := \left\{j:\; \exists\; C_{j}\text{-}C_{i} \text{ or } C_{i}\text{-}C_{j} \text{ path} \in E(T)  \right\} $$
>- Let the **upstream neighbor** of $i$ in Clique tree be $$\text{Pa}(i):= \left\{ j\in N(i):  C_{j} \cap C_{r}\text{-}C_{i} \text{ path} \neq \emptyset \right\} $$

- [[Clique Tree and Graph and Running Intersection Property]]
- [[Root and Rooted Tree]]
- [[Paths in Graph and Length of Path]]
- [[Tree-Order Relation]]

>[!important] Definition
>The **message**  from clique $C_{i}$ to a neighboring clique $C_{j}$ is computed via the **sum-product message passing** computation
>$$
>\delta_{i \to j} = \sum_{C_{i} \setminus S_{i,j}}\psi_{i} \cdot \prod_{k \in (N(i) - j) }\,\delta_{k\to i}
>$$
>where $S_{i,j}$ is the **sepset** between two neighboring cliques $C_{i}$ and $C_{j}$. By the *running intersection property* of clique tree $$S_{i,j} = C_{i} \cap C_{j}.$$
>
>
>The **sum-product message passing** can be described as the following steps
>1. The *clique* $C_{i}$ **multiplies** all **incoming messages** from its **other neighbors** with its *initial clique potential*, resulting in a factor $\psi$ whose scope is the clique. 
>2. It then **sums out** all variables **except** those in the **sepset** between $C_{i}$ and $C_{j}$, 
>3. Finally, it **sends** the resulting factor as a **message** to $C_{j}$. 

^c3b4f5

- [[Clique Tree and Graph and Running Intersection Property]]

>[!important] Definition
>The message is processed up to the tree, culminating at the *root clique*. 
>
>*At root clique*, when all messages are received, it *multiplies* them with its own potential. The resulting factor is called the **beliefs**. That is,
>$$
>\beta_{r}(C_{r}) = \psi_{r}\,\prod_{k \in N(r)}\delta_{k \to r}
>$$
>
>In particular, the **belief at root clique** represents the **(unnormalized) marginal probability** of the root clique.
>$$
>\beta_{r}(C_{r}) = \hat{\mathcal{P}}(C_{r}) = \sum_{\mathcal{X} \setminus C_{r}}\,\prod_{\phi}\phi
>$$

### Sum-Product Message Passing Algorithm for Clique Tree

>[!important] Algorithm
>The **Sum-Product (Upward) Message Passing Algorithm** for *Clique Tree* is described as 
>- *Require*: $\Phi$, the set of *factors*
>- *Require*: $T$, the **clique tree** over $\Phi$
>- *Require*: $\alpha$, the initial *assignment* of *factors to cliques*
>- *Require*: $C_{r}$, the *root clique*,
>- **Initialize** all the cliques:
>	- for each clique $C_{i}$:
>		- $$\psi_{i}(C_{i}) = \prod_{\alpha(\phi_{s}) = i}\phi_{s}.$$
>- While $C_{r}$ is not **ready** (i.e. not received *all* of messages):
>	- For each clique $C_{i}$ that is **ready**.
>		- Find the **upstream neighbor clique** $Pa(i)$
>		- Call **Sum-Product Message Passing** subprocedure and update message from $i$ to the upstream neighbor $j$ **sepset** $$\delta_{i \to Pa(i)}(S_{i, Pa(i)}) = \text{SP-Message}(i, Pa(i))$$
>- Update the **belief** $$\beta_{r} = \psi_{r}\,\cdot\prod_{k\in N(r)}\delta_{k\to r}$$ 
>- *Return*: $\beta_{r}$

>[!important] Algorithm
>The **SP-Message** subprocedure is described as
>- *Require*: $i$, the *sending* clique index
>- *Require*: $j$, the *receiving* clique index
>- *Multiplies** all **incoming messages** from its **other neighbors** with its *initial clique potential* $$\psi(C_{i}) = \psi_{i}\,\cdot\prod_{k\in (N(i) - j)}\delta_{k\to i}$$
>- *Sum out* all variables **except** those in the **sepset** between $C_{i}$ and $C_{j}$ $$\tau(S_{i,j}) = \sum_{C_{i} \setminus S_{i,j}}\psi(C_{i})$$
>- *Return* **message** $\tau(S_{i,j})$

^d4e300

- [[Topological Sorting]]

>[!info]
>In above algorithm, we assume that the *target marginal distribution* is over the **root clique**.
>
>- Changing query subset of variables requires us to *change the root clique* and to *rerun the entire algorithm*.
>- The algorithm is **sequential**, i.e. the computation of message is from leave to root. 

>[!info]
>By [[Sum-Product Variable Elimination]],  if a variable $X\in C_{i}$ and $X\not\in C_{j}$, then $X$ is **eliminated** after **SP-Message** process. 
>
>The corresponding *marginal information* of $X$ will be sent to $C_{j}$ through message $\delta_{i\to j}$.

- [[Gibbs Distribution]]

### Asynchronous Sum-Product Message Passing

>[!info]
>let us consider the task of computing the posterior distribution over every random variable in the network.

>[!info]
>In the following algorithm, we **do not choose root clique**. 
>
>As a consequence, the *message computation* and *belief update* are **in parallel** for each clique, which is **asynchronous**
>- The benefit is the output is the *marginal probability* for **all cliques** in one pass; instead of **only for root clique**.

>[!important] Definition
>Let $T$ be a clique tree. 
>
>We say that $C_{i}$ is **ready** to *transmit to a neighbor* $C_{j}$ if $C_{i}$ has messages from all of its neighbors *except from* $C_{j}$.
>
>$$
>C_{i} \text{ ready to }C_{j} \;\iff \; \delta_{k\to i} \text{ computed, }\;\;\forall k\in N(i) - j
>$$


>[!important] Algorithm
>The **(Asynchronous) Sum-Product Message Passing Algorithm** for **Clique Tree** is described as 
>- *Require*: $\Phi$, the set of *factors*
>- *Require*: $T$, the **clique tree** over $\Phi$
>- *Require*: $\alpha$, the initial *assignment* of *factors to cliques*
>- **Initialize** all the cliques:
>	- for each clique $C_{i}$:
>		- $$\psi_{i}(C_{i}) = \prod_{\alpha(\phi_{s}) = i}\phi_{s}.$$
>- While exists neighboring $i,j$ such that $C_{i}$ is **ready** to transmit to $C_{j}$.
>	- Call **Sum-Product Message Passing** subprocedure and update message from $i$ to the neighbor $j$ **sepset** $$\delta_{i \to j}(S_{i, j}) = \text{SP-Message}(i, j)$$
>- For each clique $i$:
>	- Update the **belief** $$\beta_{i} = \psi_{i}\,\cdot\prod_{k\in N(i)}\delta_{k\to i}$$ 
>- *Return*: *all beliefs* $\{ \beta_{i}, i\in V(T) \}$

^1e148a

>[!important] Definition
>The above asynchronous sum-product message passing algorithm is often called **the sum-product belief  propagation algorithm.**

>[!info]
>Note that it is **important** that $C_i$ compute the *message* to a neighboring clique $C_j$ based on its **initial potential** $\psi_{i}$ and **not its modified potential** $\beta_{i}$.
>- The latter already integrates information from $j$.

>[!info]
>There are in total $$2|E(T)|$$ *message passing computation* at each iterations, one for each direction in the graph.
>
>The belief update is **in parallel**.

## Explanation

>[!info]
>The idea of **message passing** is that it performs **sum-product variable elimination** over the **cliques**, starting from the **leaves** of the clique tree and **moving inward.**
>- Each clique $C_{i}$, except for the root, performs a *message passing computation* and sends a message to its **upstream neighbor**.

- [[Sum-Product Variable Elimination]]

>[!quote]
>The **main advantage** of the clique tree algorithm is that it computes the *posterior probability* of **all variables** in a graphical model using **only twice** the computation of the *upward pass* in the same tree.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 358

>[!important]
>this algorithm applies both to **Bayesian network** and **Markov network** *inference*. 
>- For a *Bayesian network* $\mathcal{B}$, if $\Phi$ consists of the **CPDs** in $\mathcal{B}$, *reduced* with some evidence e, then $$\beta_{r}(C_{r}) = \mathcal{P}_{\mathcal{B}}(C_{r}, e).$$
>- For a *Markov network* $\mathcal{H}$, if $\Phi$ consists of the **compatibility functions** defining the network, then $$\beta_{r}(C_{r}) =  \hat{\mathcal{P}}_{\Phi}(C_{r}).$$
>  
>In both cases, we can obtain the *probability* over the variables in $C_{r}$ as usual, by *normalizing the resulting factor* to sum to $1$.  

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network on Undirected Graph]]
- [[Local Probabilistic Models]]

>[!important]
>The above algorithm is a **tabular-based method**. 
>
>In tabular form, we need to maintain the following entities: 
>-  the *value* of *messages* $\delta_{i\to j}(s_{i,j})$ for all **assignments** of $s_{i,j} \in \text{Var}(S_{i,j})$ and for **every edge** $ij\in E(T)$ 
>- the *value* of *initial clique potentials* $\psi_{i}(c_{i})$ for all **assignment** $c_{i} \in \text{Var}(C_{i})$ for each clique $i\in V(T)$
>- the output *value* of *clique beliefs* $\beta_{i}(c_{i})$ for all **assignment** $c_{i} \in \text{Var}(C_{i})$ for each clique $i\in V(T)$
>
>There are in total 
>$$
> 2\,\sum_{ij \in E(T)}|\text{Var}(S_{i,j})| + 2\sum_{i\in V(T)}|\text{Var}(C_{i})|
>$$
>table entities.
>
>In other word, it is for graphical model of **discrete random variables.** For *continuous random variable*, the message $\delta_{i\to j}$ is a **function**.

>[!info]
>A **functional form** of message passing is based on the assumption that  $$\delta_{i\to j} \in \mathcal{F}_{\theta}$$ that is, the message function belongs to a *parametric family*
>
>The most common parametric family is the **exponential family**, e.g. the **Gaussian graphical model.**

- [[Parametric Models]]
- [[Exponential Family of Distributions]]
- [[Canonical Form of Gaussian Graphical Model]]

## Upward and Downward Pass

>[!important]
>The *message passing process* performed by the algorithm is equivalent to a much more systematic process that consists of an **upward pass** and a **downward pass**. 
>- In the **upward pass**, we first *pick a root* and send all messages *toward the root*. 
>	- When this process is complete, the **root has all messages.** 
>- After that, in the **downward pass**, the root can now **send** the appropriate message to all of its *children*.
>	- The algorithm continues *until* the **leaves** of the tree are reached, at which point *no more messages* need to be sent.


>[!info]
>The message passing algorithm is similar to the **reverse mode automatic differentiation**. 
>
>- In the automatic differentiation, the "*message*" is the **computed gradient** from the neighborhood in a **computational graph**. 
>- In the graphical model,  the "*message*" is the **marginal of factor** from the neighborhood in a **statistical dependency graph**. 

- [[Automatic Differentiation]]


## Dynamic Programming

>[!info]
>The message passing algorithm is a **dynamic programming** *implementation* of the sum-product variable elimination.

- [[Dynamic Programming Algorithms]]
- [[Sum-Product Variable Elimination]]

>[!important]
>The **Bellman equation** corresponding to the sum-product message passing algorithm is
>$$
>\begin{align*}
>\delta_{i\to j} &\propto \; \sum_{C_{i} \setminus S_{i,j}}\,\psi_{i}\,\cdot \left(\prod_{k\in (N(i) - j)}\delta_{k \to i}\right)
>\end{align*}
>$$


## Message Scheduling


>[!info]
>The asynchronous algorithm is equivalent to this systematic algorithm, except that the root is simply the first clique that happens to obtain messages from all of its neighbors. In an actual implementation, we might want to **schedule** this process more explicitly.


## Correctness

- [[Correctness of Belief Propagation for Clique Tree]]


## Invariant Measure of Sum Product Message Passing

- [[Clique Tree Calibration]]
- [[Clique Tree Invariant of Sum Product and Reparameterization of PGM]]


## Belief Update Algorithm

- [[Sum-Product Belief-Update Message Passing Algorithm for Clique Tree]]
- [[Belief Propagation and Belief Update Equivalence for Clique Tree]]

## Variational Inference Perspective and Fixed Point Algorithm

![[Bethe Variational Inference for Clique Tree#^9e261d]]


>[!quote]
>This theorem characterizes the **solution** of the *optimization problem* in terms of **fixed-point equations** that must hold when we find a **maximal** $\mathcal{Q}$. These fixed-point equations define the *relationships that must hold* between the different *parameters* involved in the optimization problem. Most importantly, equation (11.10) defines each **message** in terms of **other messages**, allowing an easy **iterative approach** to solving the *fixed point equations*. These same themes appear in all the approaches we will discuss later in this chapter.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 390

- [[Variational Inference for Clique Tree]]
- [[Bethe Variational Inference for Clique Tree]]
- [[Stationary Point of Bethe Variational Inference Problem]]



-----------
##  Recommended Notes and References




- [[Clique Tree and Graph and Running Intersection Property]]
- [[Tree Graph and Forest]]

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network on Undirected Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 348- 355, 963 - 966, 963 - 966
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 24
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 408
- [[Foundations of Computer Vision by Torralba]] pp 428 - 433
- [[Artificial Intelligence Modern Approach by Russell]] pp 555
