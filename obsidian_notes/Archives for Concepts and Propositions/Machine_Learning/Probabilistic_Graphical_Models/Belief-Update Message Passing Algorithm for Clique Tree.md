---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/algorithm
keywords:
  - belief_update
  - probabilistic_graphical_model
  - dynamic_programming
topics:
  - probabilistic_graphical_model
name: Belief-Update Message Passing Algorithm for Clique Tree
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Belief-Update Message Passing Algorithm or *Lauritzen-Spiegelhalter algorithm* for Clique Tree


>[!info]
>In [[Sum-Product Message Passing Algorithm for Clique Tree]], the **clique belief** is updated via  $$\beta_{i} = \psi_{i}\,\cdot\prod_{k\in N(i)}\delta_{k\to i}$$ 
>As we discussed, this final potential is not used in computing the message to $C_j$: this potential *already incorporates the information* (message) passed **from** $C_{j}$; if we used it when computing the message **to** $C_{j}$, this information would be **double-counted.** 
>
>Thus, the message from $C_i$ to $C_j$ is computed in a way that **omits the information obtained from** $C_j$: 
>- we **multiply** the *initial potential* with **all** of the messages **except for** the message from $C_{i}$, and 
>- then **marginalize** over the *sepset*

>[!info]
>A different approach to computing the same expression is to 
>- **multiply in all of the messages**, and 
>- then **divide** the resulting factor by $\delta_{j\to i}$. 
>  
>To make this notion precise, we must define a factor-division operation:


### Factor Division

>[!important] Definition
>Let $\mathcal{X}$ and $\mathcal{Y}$ be *disjoint sets of variables*, and let $\phi_{1}(\mathcal{X}, \mathcal{Y})$, and $\phi_{2}(\mathcal{Y})$ be two factors.
>
>We define the **division** of $\phi_{1}$ over $\phi_{2}$ to be a *factor* $\psi$ of scope $\{ \mathcal{X}, \mathcal{Y} \}$ defined as follows
>$$
>\psi(\mathcal{X}, \mathcal{Y}) = \frac{\phi_{1}(\mathcal{X}, \mathcal{Y})}{\phi_{2}(\mathcal{Y})}
>$$
>where $0 / 0  := 0.$


### Belief Update Algorithm


>[!important] Algorithm
>The **Belief-Update Message Passing Algorithm** for **Clique Tree** is described as 
>- *Require*: $\Phi$, the set of *factors*
>- *Require*: $T$, the **clique tree** over $\Phi$
>- *Require*: $\alpha$, the initial *assignment* of *factors to cliques*
>- **Initialize** all the clique tree beliefs:
>	- for each clique $C_{i}$:
>		- initialize the **clique belief** $$\beta_{i} = \prod_{\alpha(\phi_{s}) = i}\phi_{s}.$$
>	- for each edge $ij\in E(T)$
>		- initialize the **sepset belief** $$\mu_{i,j} = 1$$
>- While exists an *uninformed* clique in $T$
>	- Select an edge $ij\in E(T)$
>	- Call **Belief-Update Message Passing** subprocedure to update *clique belief* $\beta_{j}$ in receiving clique and *sepset belief* $\mu_{i,j}$ $$\text{BU-Message}(i, j)$$
>- *Return*: *all clique beliefs* $\{ \beta_{i}, i\in V(T) \}$

>[!important] Algorithm
>The **BU-Message** subprocedure is described as
>- *Require*: $i$, the *sending* clique index
>- *Require*: $j$, the *receiving* clique index
>- *Marginalize* the clique over the **sepset** between $C_{i}$ and $C_{j}$ $$\sigma_{i\to j} = \sum_{C_{i} \setminus S_{i,j}}\beta_{i}$$
>- *Update* the **clique belief** using Bayes rule $$\beta_{j} \leftarrow \beta_{j} \cdot \frac{\sigma_{i\to j}}{\mu_{i,j}}$$
>- *Update* the **sepset belief** $$\mu_{i,j} = \sigma_{i\to j}$$ 

^73ff45

>[!info]
>The *message passing process* is as follows
>- Each *clique* $C_{i}$ **initializes** $\beta_{i}$ as $\psi_{i}$ and 
>- then **updates** it by **multiplying** with *message updates* received from its **neighbors**. 
>- Each **sepset** $S_{i,j}$ maintains $\mu_{i,j}$ as the previous *message passed along* the edge $(i\text{-}j)$,  **regardless of the direction**.
>	- This message is used to ensure that we *do not double-count*: Whenever a **new message** is passed along the edge, it is **divided by the old message**, *eliminating the previous message* from the update to the clique.
>	- Somewhat surprisingly, as we will show, the message passing operation is **correct** **regardless** of the clique that sent the *last message* on the edge.
>	- Intuitively, once the message is passed, its information is incorporated into **both cliques**; thus, *each* needs to *divide* by it when passing a message to the other.


>[!important] Definition
>- We can view this algorithm as *maintaining* a set of *belief* over the *cliques* in the tree.
>- The *message passing operation* takes the *beliefs* of *one clique* and uses them to *update the beliefs* of a *neighbor*. 
>  
>Thus, we call this algorithm **belief-update message passing**; it is also known as the **Lauritzen-Spiegelhalter algorithm**.

## Explanation

>[!important]
>The **belief update** formula
>$$
>\begin{align*}
>\delta_{i\to j} &= \frac{\sum_{C_{i} \setminus S_{i,j}}\beta_{i}}{\delta_{j\to i}} \\[8pt]
>&:= \frac{\sum_{C_{i} \setminus S_{i,j}}\psi_{i}\,\cdot\prod_{k\in N(i)}\delta_{k\to i}}{\delta_{j\to i}}
>\end{align*}
>$$
>follows the **Bayes formula** to compute the **inverse probability (posterior probability)**.
>
>This formula motivates the name "**Bayesian**" in the *Bayesian network*.

- [[Bayes Theorem]]
- [[Clique Tree Calibration]]



## Invariant Measure


![[Belief Propagation and Belief Update Equivalence for Clique Tree#^64f40c]]




-----------
##  Recommended Notes and References

- [[Belief Propagation and Belief Update Equivalence for Clique Tree]]
- [[Sum-Product Message Passing Algorithm for Clique Tree]]

- [[Clique Tree and Running Intersection Property]]

- [[Tree-Order Relation]]
- [[Root and Rooted Tree]]
- [[Tree Graph and Forest]]


- [[Probabilistic Graphical Models by Koller]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
