---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/inference
keywords:
  - gaussian_graphical_model
  - sum_product
  - message_passing
topics:
  - probabilistic_graphical_model
name: Gaussian Belief Propagation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Gaussian Belief Propagation

>[!info]
>Recall the sum-product message passing for **belief propagation** and **belief update algorithm**.

>[!info]
>We can adapt these algorithms to apply to **linear Gaussian networks**, using **canonical forms** as our representation of factors.

- [[Canonical Form of Gaussian Graphical Model]]
- [[Sum-Product Belief-Update Message Passing Algorithm for Clique Tree]]
- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]


### Overview of Gaussian Belief Propagation

>[!info]
>The Gaussian belief propagation algorithm utilizes the information form, or canonical form, of the Gaussian distribution

![[Gaussian Graphical Model#^162c43]]

>[!important] 
>It is noted that the **minimal cluster graph** that satisfies the **family preserving property** would contain *cluster* for each edge $(ij)$ so that $K_{ij} \neq 0$.
>- we have *one node cluster* for each variable $X_{i}$
>- we have *one edge cluster* for each pair $(X_{i},X_{j})$ so that $K_{ij} \neq 0.$

- [[Cluster Graph and Family Preservation]]

>[!quote]
>We note that the parameterization of the cluster graph is **not uniquely defined**. In particular, a term of the form  $K_{i i}X_{i}^2$ can be *partitioned* **in infinitely many ways** among the node’s own cluster and among the edges that contain $X_{i}$. Each of these partitions defines a *different set of potentials* in the cluster graph, and hence will induce a different execution of belief propagation. We describe the algorithm in terms of the simplest partition, where each *diagonal term* $K_{i i}$ is assigned to the corresponding $X_{i}$ *cluster*, and the *off-diagonal terms* $K_{i j}$ are assigned to the $X_{i}$, $X_{j}$ *cluster*.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 613

#### Marginalization Operation

>[!quote]
>A more important problem that we must consider is that the **marginalization operation** may *not be well defined* for an arbitrary canonical form. In order to show the **correctness** of an inference algorithm, we must show that it executes a marginalization step **only on canonical forms** for which this operation is *well defined*.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 611

>[!important] Proposition
>Whenever **SP-Message** is called, within the **Sum-Product (Upward) Message Passing Algorithm** the **marginalization** operation is **well-defined**.



### Canonical Form for Message

![[Sum-Product Belief Propagation Algorithm for Clique Tree#^d4e300]]


>[!important]
>The **message** from $X_{i}$ to $X_{j}$ has the *form* 
>$$
>\delta_{i \to j}(x_{j}) = \exp \left(-\frac{1}{2}K_{i\to j}\,x_{j}^2 + h_{i\to j}x_{j} \right).
>$$

^d985d2

>[!important]
>We compute the **coefficients** in this expression via a **two-stage process**.
>- The **first step** corresponds to the **message** sent from the $X_{i}$ *cluster* to the $X_i$, $X_j$ *edge*; in this step, $X_{i}$ *aggregates* all of the information from its own local potential and the message sent from its other incident edges $$\begin{align*}\hat{K}_{i / j} &= K_{i i } + \sum_{k \in \{N(i) - j\}}K_{k\to i} \\[5pt] \hat{h}_{i / j} &= h_{i} + \sum_{k \in \{N(i) - j\}}h_{k\to i}\end{align*}$$
>- In the **second step**, the $X_i$, $X_j$ *edge* takes the message received from $X_{i}$, and send the appropriate message to $X_{j}.$ The form of message is computed via *marginalized Gaussian distribution*. It gives rise the following update equation $$\begin{align*}K_{i \to j} &= -K_{j i}K_{i / j}^{-1} \,K_{i j}   \\[5pt] h_{i / j} &= -K_{j i}K_{i / j}^{-1}\,h_{i / j}\end{align*}$$

^919312


>[!info]
>Note that the first step is to compute the **canonical form of join probability** 
>$$p(x_{i}, x_{j}) \propto \psi(x_{i}, x_{j}) =  \exp\left(-\frac{1}{2}\left\langle \hat{K}_{(ij)}\, x_{(ij)} \,,\,  x_{(ij)} \right\rangle + \left\langle  \hat{h}_{(ij)}\,,\, x_{(ij)} \right\rangle \right)$$
>where
>$$
>\begin{align*}
> \hat{K}_{(ij), (ij)} &= \left[\begin{array}{cc}
>\hat{K}_{i / j}  & K_{i j} \\
>K_{j i} & 0
>\end{array}\right] \\[5pt]
> \hat{h}_{(ij)}&= \left[\begin{array}{c}
> \hat{h}_{i / j} \\
> 0
>\end{array}\right].
>\end{align*}
>$$
>Then the second step is for **marginalization** of above joint distribution over $x_{i}$. The corresponding *canonical parameters* are
>$$
>\begin{align*}
> K' &= \hat{K}_{j j} - K_{j i}\hat{K}_{i / j}^{-1}K_{i j} = - K_{j i}\hat{K}_{i / j}^{-1}K_{i j}\\[5pt]
> h' &= h_{j} - K_{j i}\hat{K}_{i / j}^{-1}\hat{h}_{i / j} = - K_{j i}\hat{K}_{i / j}^{-1}\hat{h}_{i / j}
>\end{align*}
>$$

^967ffd

- [[KKT Matrix and KKT System for Optimization with Equality Constraints]]
### Gaussian Belief Propagation

>[!important] Algorithm
>The **Gaussian-SP-Message** subprocedure for Gaussian Belief Propagation is described as
>- *Require*: $i$, the *sending* node clique index
>- *Require*: $j$, the *receiving* node clique index
>- Compute the **message** from **node clique** $X_{i}$ to the **edge clique** $(X_{i}, X_{j})$  in *canonical form* $$\begin{align*}\psi(x_{i}, x_{j}) &\propto  \exp\left(-\frac{1}{2}\left\langle \hat{K}_{(ij)}\, x_{(ij)} \,,\,  x_{(ij)} \right\rangle + \left\langle  \hat{h}_{(ij)}\,,\, x_{(ij)} \right\rangle \right)\end{align*}$$ where $$\begin{align*}\hat{K}_{(ij)} &= \left[\begin{array}{cc}\hat{K}_{i / j}  & K_{i j} \\K_{j i} & 0\end{array}\right], \\[5pt]\hat{h}_{(ij)}&= \left[\begin{array}{c}\hat{h}_{i / j} \\0\end{array}\right], \\[5pt] x_{(ij)}&= \left[\begin{array}{c}x_{i} \\ x_{j}\end{array}\right].\end{align*}$$ 
>	- The **canonical parameters** $(\hat{K}_{i / j}\,,\, \hat{h}_{i / j})$ can be obtained by **aggregating** all *incoming messages* from its *other neighbors* with its *initial local node potential*. $$\begin{align*}\hat{K}_{i / j} &= K_{i i } + \sum_{k \in \{N(i) - j\}}K_{k\to i} \\[5pt] \hat{h}_{i / j} &= h_{i} + \sum_{k \in \{N(i) - j\}}h_{k\to i}\end{align*}$$
>- Compute **message** from the **edge clique** $(X_{i}, X_{j})$ to **node clique** $j$ via the **marginalization** of the *canonical form* $$\tau(x_{j}) = \int_{x_{i}}\psi(x_{i}, x_{j})d x_{i} \propto   \exp \left(-\frac{1}{2}K_{i\to j}\,x_{j}^2 + h_{i\to j}x_{j} \right)$$ where the **canonical parameters** are $$\begin{align*}K_{i \to j} &= -K_{j i}\hat{K}_{i / j}^{-1} \,K_{i j}   \\[5pt] h_{i \to j} &= -K_{j i}\hat{K}_{i / j}^{-1}\,\hat{h}_{i / j}\end{align*}$$
>- *Return* **canonical parameters** of **message** $\tau(x_{j})$ as $$(K_{i \to j}\,,\, h_{i / j}).$$

^f3c18b

- [[Canonical Form of Gaussian Graphical Model]]

>[!important] Algorithm
>The **Gaussian Belief Propgation Algorithm** is described as 
>- *Require*: $(K, h)$, the set of **canonical parameters** for Gaussian graphical model.
>- *Require*: a *cluster graph* $G$ that includes
>	- *a node cluster* for each variable and 
>	- *an edge cluster* for each $(ij)$ so that $K_{i,j} \neq 0$.
>- *Require*: an ordering $\preceq$ in $G$.
>- While exists neighboring $i,j$ such that $X_{i}$ is **ready** to transmit to $X_{j}$.
>	- Call **Gaussian-SP-Message** subprocedure and **update** *canonical parameter* of the *message* from $X_{i}$ to the neighbor $X_{j}$, i.e. $$(K_{i\to j}\,,\, h_{i\to j}) = \text{SP-Message}(i, j) $$
>- For each clique $i$:
>	- Update the **canonical parameters for the belief** $$\begin{align*}\hat{K}_{i} &= K_{i i } + \sum_{k \in N(i)}K_{k\to i} \\[5pt] \hat{h}_{i}&= h_{i} + \sum_{k \in N(i)}h_{k\to i}\end{align*}$$
>- *Return*: the set of *canonical parameters* for all *beliefs* $\{(\hat{K}_{i}, \hat{h}_{i}), i\in V(T) \}$ or the *beliefs* $\{ \beta_{i}, i\in V(T) \}$, where $$\beta_{i} =  \exp \left(-\frac{1}{2}\hat{K}_{i}x_{i}^2 + \hat{h}_{i}x_{i}\right).$$  

- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Sum-Product Expectation Propagation Algorithm]]

### Convergence and Correctness of BP Algorithm for GGM

>[!important] Proposition
>Let $(\hat{\mu}_{i}, \hat{\Sigma}_{i})$ be a set of **fixed points** of the **message passing process** defined in equation $$\begin{align*}\hat{K}_{i / j} &= K_{i i } + \sum_{k \in \{N(i) - j\}}K_{k\to i} \\[2pt] \hat{h}_{i / j} &= h_{i} + \sum_{k \in \{N(i) - j\}}h_{k\to i},\end{align*}$$ and equation $$\begin{align*}K_{i \to j} &= -K_{j i}\hat{K}_{i / j}^{-1} \,K_{i j}   \\[5pt] h_{i \to j} &= -K_{j i}\hat{K}_{i / j}^{-1}\,\hat{h}_{i / j}.\end{align*}$$ Then $$\hat{\mu}_{i} = \hat{K}_{i}^{-1}\,\hat{h}_{i}$$ is the **correct posterior mean** for the variable $X_{i}$ in the distribution $p$.

>[!quote]
>Thus, if the *BP message passing process* **converges**, the resulting beliefs encode the **correct mean** of the joint distribution. The *estimated variances* $$\hat{\sigma}^2_{i} = \hat{K}_{i}^{-1}$$ are generally *not correct*; rather, they are an **underestimate of the true variances**, so that the resulting *posteriors* are “**overconfident**.”
>
>-- [[Probabilistic Graphical Models by Koller]] pp 614

>[!quote]
>This correctness result is predicated on convergence. In general, this message passing process *may or may not converge*. Moreover, their convergence may depend on the *order* in which messages are sent. However, unlike the discrete case, one can provide a very *detailed characterization of the convergence properties* of this process, as well as *sufficient conditions* for convergence. In particular, one can show that the **pairwise normalizability condition**, as in definition 7.3, **suffices** to guarantee the **convergence** of the belief propagation algorithm for **any order of messages**. Recall that this condition guarantees that each edge can be associated with a *potential* that is a *normalized Gaussian distribution*.

>[!info]
>In practice, the **Gaussian belief propagation** algorithm **often converges** and provides an excellent alternative for reasoning in Gaussian distributions that are too large for exact techniques.

## Explanation

>[!quote]
>Care must be taken regarding the treatment of **evidence**. ... it is necessary to **reduce** *all the factors participating* in the inference process to a *scope* that **no longer contains** $Z$.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 611


>[!quote]
>It follows that we can **adapt** any of our *exact inference algorithms* to the case of linear Gaussian networks. The algorithms are essentially **unchanged**; only the **representation of factors** and the implementation of the basic factor operations are different. In particular, since all factor operations can be done in *polynomial time*, **inference in linear Gaussian networks** is **linear** in the **number of cliques**, and **at most cubic** in the **size of the largest clique**. By comparison, recall that the representation of *table factors* is, by itself, **exponential in the scope**, leading to the exponential complexity of inference in discrete networks.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 612



## Kalman Filter


>[!info]
>The posterior inference of **Kalman filter** can be seen as a special case of *Gaussian Belief Propagation* when operating on the **unfolded temporal network**.

- [[Kalman Filter Discrete-Time]]




-----------
##  Recommended Notes and References


- [[Sum-Product Belief-Update Message Passing Algorithm for Clique Tree]]
- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Canonical Form of Gaussian Graphical Model]]
- [[Gaussian Graphical Model]]
- [[Gaussian Bayesian Network]]

- [[Gaussian Random Vector]]
- [[Gaussian Process]]
- [[Gaussian Measure]]

- [[Probabilistic Graphical Models by Koller]] pp 247, 612 - 615
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 413
