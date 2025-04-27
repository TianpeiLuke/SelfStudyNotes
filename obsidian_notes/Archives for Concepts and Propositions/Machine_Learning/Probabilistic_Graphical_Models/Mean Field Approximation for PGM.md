---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/representation
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/theory
  - PGM
  - mean_field_approximation
keywords:
  - mean_field_approximation
topics:
  - probabilistic_graphical_model
name: Mean Field Approximation for PGM
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Mean Field Approximation for PGM

![[Energy Functional for Probabilistic Graphical Model#^c01c98]]

- [[Energy Functional for Probabilistic Graphical Model]]

>[!important] Definition
>Let $P_{\Phi}$ be a *Bayesian network* or *Markov network* over $\mathcal{X}$ that *factorizes* according to $\mathcal{G}$, and $\Phi$ be a set of *factors* in $P$. The unnormalized distribution is 
>$$
> \tilde{P}_{\Phi}(X_{v}\,,\, v\in \mathcal{V}) = \prod_{\phi \in \Phi}\phi(X_{\phi})
>$$
>
>
>The **naive mean field algorithms** assume that the *variational distribution* $Q$ is within the class of distributions that are the *product of independent marginals*
>$$
>\mathcal{Q}_{\text{mean field}} := \left\{ Q \in \mathcal{M}(\mathcal{Z}): Q(X_{v}\,,\, v\in \mathcal{V}) = \prod_{v\in \mathcal{V}} Q(X_{v}) \right\} 
>$$
>
>The **energy functional** under the *mean field assumption* $Q\in \mathcal{Q}_{\text{mean field}}$ is given by
>$$
>\begin{align*}
>\mathcal{L}(Q, \Phi; \mathcal{X}) &= \mathbb{E}_{Q}\left[ \log \tilde{P}_{\Phi}  - \log Q  \right] \\[5pt]
>&= H(Q) + \mathbb{E}_{ Q }\left[  \log \tilde{P}_{\Phi}(X)\right]\\[5pt]
>&= \sum_{v\in \mathcal{V}}H_{Q}(X_{v}) + \sum_{\phi\in \Phi} \sum_{X_{\phi}\in \mathcal{X}_{\phi}} \left(\prod_{x_{i} \in \text{scope}(\phi)}Q(X_{i})\right)  \log \phi_{k}(X_{\phi})
>\end{align*}
>$$
>
>The **naive mean field algorithm** on $\mathcal{P}_{\Phi}$ solves the following optimization problem
>$$
>\begin{align*}
>  \max_{\{Q(X_{i})\}}\;& \mathcal{L}(Q, \Phi; \mathcal{X})\\[5pt]
>  \text{s.t. }\;&\, Q(X) = \prod_{v\in \mathcal{V}}Q(X_{v})\\[5pt]
>  &\, \sum_{X_{v}\in \mathcal{X}_{v}}Q(X_{v}) = 1,\quad \forall v\in \mathcal{V}
>\end{align*}
>$$
>- Instead of estimation the joint variational distribution $\mathcal{Q}$, the mean field algorithm estimates *each marginal distribution* independently.

^ddaaef

>[!info]
>The key characteristic of mean field approximation is that
>- We **do not approximate the objective function**, which is the case for 
>	- [[Loopy Belief Propagation Algorithm for Cluster Graph]] and 
>	- [[Sum-Product Expectation Propagation Algorithm]]
>- We approximate the **optimization space** $$Q \vDash \mathcal{G}  \implies Q \vDash \mathcal{G}_{0} = (\mathcal{V}, \emptyset).$$

- [[Structured Variational Approximation]]
- [[Maximum Entropy Learning for Approximate Inference in PGM]]
- [[Marginal Polytope and Local Consistent Polytope]]

### Fixed-Point Solution for Mean Field Problem

>[!important] Proposition
>The distribution $Q(X_{i})$ is a **local minimizer** of the **naive mean field** problem
>$$
>\begin{align*}
>  \max_{\{Q(X_{i})\}}\;& \mathcal{L}(Q, \Phi; \mathcal{X})\\[5pt]
>  \text{s.t. }\;&\, Q(X) = \prod_{v\in \mathcal{V}}Q(X_{v})\\[5pt]
>  &\, \sum_{X_{v}\in \mathcal{X}_{v}}Q(X_{v}) = 1,\quad \forall v\in \mathcal{V}
>\end{align*}
>$$
> **given**  $\{ Q(X_{j}),\; j\neq i \}$ **if and only if** $Q(X_{i})$ is of the form
> $$
> Q(x_{i}) = \frac{1}{Z_{i}} \exp \left\{ \sum_{\phi \in \Phi}\mathbb{E}_{ Q }\left[\log \phi | X_{i} = x_{i}\right] \right\}  
> $$
>where $Z_{i}$ is a *local normalizing constant* and $\mathbb{E}_{ Q }\left[\log \phi | X_{i} = x_{i}\right]$ is **conditional expectation** given $X_{i}=x_{i}$, $$\mathbb{E}_{ Q }\left[\log \phi | X_{i} = x_{i}\right] = \sum_{x_{\phi}}Q(x_{\phi}|x_{i})\,\log \phi(x_{\phi}).$$

- [[Fixed Point of Map]]


>[!important] Corollary
>In the **naive mean field approximation**,  the distribution $Q(X_{i})$ is **locally optimal** **only if** 
> $$
> Q(x_{i}) = \frac{1}{Z_{i}} \exp \left\{\mathbb{E}_{ X_{-i} \sim Q }\left[\log P_{\Phi}(x_{i} | X_{-i})\right] \right\}  
> $$
>where $Z_{i}$ is a *local normalizing constant*.


>[!important] Corollary
>In the **naive mean field approximation**,  the distribution $Q(X_{i})$ is **locally optimal** **only if** 
> $$
> Q(x_{i}) = \frac{1}{Z_{i}} \exp \left\{\sum_{\phi: X_{i}\in \text{scope}(\phi)}\mathbb{E}_{ (X_{\phi} \setminus \{ X_{i} \})  \sim Q }\left[\log \phi(X_{\phi}, x_{i})\right] \right\}  
> $$
>where $Z_{i}$ is a *normalizing constant*.

#### Proof of Theorem

>[!info]
>First, consider restriction of energy functional to terms only including $X_{i}$, 
>$$
>F_{i}(Q) := H_{Q}(X_{i}) + \sum_{\phi\in \Phi} \mathbb{E}_{ X_{\phi} \sim Q }\left[  \log \phi \right] 
>$$
>and the *Lagrangian* is defined as
>$$
>L_{i}(Q, \lambda) =   H_{Q}(X_{i}) + \sum_{\phi\in \Phi} \mathbb{E}_{ X_{\phi} \sim Q }\left[  \log \phi \right] + \lambda \left(\sum_{x_{i}}Q(x_{i}) - 1\right)
>$$
>where
>$$
>\mathbb{E}_{ X_{\phi} \sim Q }\left[  \log \phi \right] = \sum_{x_{i}}\sum_{x_{-i}}\left(\prod_{i}Q(x_{i})\right)\,\log \phi(x_{i}, x_{-i})
>$$
>
>Taking derivative with respect to $Q(x_{i})$ we have the *necessary condition* for optimal solution $Q(x_{i})$ is that
>$$
>\begin{align*}
> \frac{ \partial  }{ \partial Q(x_{i}) }L_{i} &= -\log Q(x_{i}) - 1 + \lambda +   \sum_{\phi\in \Phi}\sum_{x_{-i}}\left(\prod_{j\neq i}Q(x_{j})\right)\,\log \phi(x_{i}, x_{-i}) \\[5pt]
> &= -\log Q(x_{i}) - 1 + \lambda +  \sum_{\phi\in \Phi}\sum_{x_{-i}} \frac{\prod_{j} Q(x_{j})}{Q(x_{i})}\,\log \phi(x_{i}, x_{-i}) \\[5pt]
> &= -\log Q(x_{i}) - 1 + \lambda +  \sum_{\phi\in \Phi}\sum_{x_{-i}} \frac{Q(x_{i}, x_{-i})}{Q(x_{i})}\,\log \phi(x_{i}, x_{-i}) \\[5pt]
> &= -\log Q(x_{i}) - 1 + \lambda +  \sum_{\phi\in \Phi}\mathbb{E}_{ X \sim Q }\left[  \log \phi(X_{i}, X_{-i})\;|\;X_{i} = x_{i} \right] \\[5pt]
> & =0
>\end{align*}
>$$
>
>Thus $$\log Q(x_{i}) = \lambda - 1+ \sum_{\phi\in \Phi}\mathbb{E}_{ X \sim Q }\left[  \log \phi\;|\;x_{i} \right]$$ Taking exponents on both sides and renormalize, we can remove $\lambda$, which leads to the solution
>$$
>Q(x_{i}) = \frac{1}{Z_{i}} \exp \left\{ \sum_{\phi \in \Phi}\mathbb{E}_{ Q }\left[\log \phi | X_{i} = x_{i}\right] \right\} 
>$$

>[!info]
>To show that this condition is *sufficient*, we see that the objective function restricting on $X_{i}$
>$$
>F_{i}(Q) := H_{Q}(X_{i}) + \sum_{\phi\in \Phi} \mathbb{E}_{ X_{\phi} \sim Q }\left[  \log \phi \right] 
>$$
 >is **concave** in $Q(x_{i})$ since 
 >- the *entropy is concave* in $Q(X_{i})$ and 
 >- the second term $$\mathbb{E}_{ X_{\phi} \sim Q }\left[  \log \phi \right] = \sum_{x_{i}}\sum_{x_{-i}}Q(x_{i})\left(\prod_{j\neq i}Q(x_{j})\right)\,\log \phi(x_{i}, x_{-i})$$ is *linear* in $Q(x_{i})$ given all others $Q(x_{-i})$
>
>Thus the local optimization has a **unique solution**, which is of the form above. \[End of Proof\]

- [[Methods of Lagrangian Multipliers]]

#### Proof of Corollary

>[!info]
>Note that 
>$$
>\tilde{P}_{\Phi} = \prod_{\phi \in \Phi}\phi  \;\; \implies \;\; \log\tilde{P}_{\Phi} = \sum_{\phi \in \Phi}\log \phi
>$$
>So 
>$$
>\sum_{\phi\in \Phi} \mathbb{E}_{ X \sim Q }\left[  \log \phi \;|\;x_{i}\right] = \mathbb{E}_{ X_{\phi} \sim Q }\left[  \log \tilde{P}_{\Phi}(X_{i}, X_{-i})\;|\;x_{i} \right]
>$$
>Note that $Q$ is a *product measure*, so
>$$
>Q(X_{-i}|x_{i}) = Q(X_{-i})
>$$
>which means that
>$$
>\mathbb{E}_{ X \sim Q }\left[  \log \tilde{P}_{\Phi}(X_{i}, X_{-i})\;|\;x_{i} \right] =  \mathbb{E}_{ X_{-i} \sim Q }\left[  \log \tilde{P}_{\Phi}(x_{i}, X_{-i})\right]
>$$

>[!info]
>Note that $$\tilde{P}_{\Phi}(x_{i}, X_{-i}) = Z\,P_{\Phi}(x_{i}. X_{-i}) = Z\,P_{\Phi}(x_{i}|X_{-i})\,P_{\Phi}(X_{-i})$$
>
>We conclude that 
>$$
>\begin{align*}
> \sum_{\phi\in \Phi} \mathbb{E}_{ X \sim Q }\left[  \log \phi \;|\;x_{i}\right] &= \mathbb{E}_{ X_{-i} \sim Q }\left[  \tilde{P}_{\Phi}(x_{i}, X_{-i})\right] \\[5pt]
> &= \mathbb{E}_{ X_{-i} \sim Q }\left[\log P_{\Phi}(x_{i}|X_{-i})\right] + \mathbb{E}_{ X_{-i} \sim Q }\left[\log ZP_{\Phi}(X_{-i})\right]
>\end{align*}
>$$

>[!info]
>From above theorem,
>$$
>\begin{align*}
>Q(x_{i}) &= \frac{1}{Z_{i}} \exp \left\{ \sum_{\phi \in \Phi}\mathbb{E}_{ Q }\left[\log \phi | X_{i} = x_{i}\right] \right\} \\[5pt]
>&= \frac{1}{Z_{i}} \exp \left\{  \mathbb{E}_{ X_{-i} \sim Q }\left[\log P_{\Phi}(x_{i}|X_{-i})\right]\right\} \exp \left\{\mathbb{E}_{ X_{-i} \sim Q }\left[\log ZP_{\Phi}(X_{-i})\right] \right\} \\[5pt]
>\end{align*}
>$$
>where 
>$$\exp \left\{\mathbb{E}_{ X_{-i} \sim Q }\left[\log ZP_{\Phi}(X_{-i})\right] \right\}$$ is a *constant with respect to* $x_{i}$, so we can *absorb it into* $Z_{i}$.
>
>Thus
>$$
>Q(x_{i}) = \frac{1}{Z_{i}} \exp \left\{  \mathbb{E}_{ X_{-i} \sim Q }\left[\log P_{\Phi}(x_{i}|X_{-i})\right]\right\} 
>$$
>\[End of Proof\]

### Mean Field Approximation Algorithm

>[!important] Definition
>Consider the optimization problem
>$$
>\begin{align*}
>  \max_{\{Q(X_{i})\}}\;& \mathcal{L}(Q, \Phi; \mathcal{X})\\[5pt]
>  \text{s.t. }\;&\, Q(X) = \prod_{v\in \mathcal{V}}Q(X_{v})\\[5pt]
>  &\, \sum_{X_{v}\in \mathcal{X}_{v}}Q(X_{v}) = 1,\quad \forall v\in \mathcal{V}
>\end{align*}
>$$
>where $\mathcal{L}(Q, \Phi; \mathcal{X})$ is the *energy functional* for $Q$ and $\tilde{P}_{\Phi}$.
>
>The **Mean Field approximation algorithm** solves above problem using *coordinate ascent* as follow:
>- *Require*: Factors $\Phi := \{ \phi \}$ that defines the graphical model $P_{\Phi}$;
>- *Require*: *Initial Distribution*  $Q_{0}$
>- Initialize the list
>	- $$Q \leftarrow Q_{0}$$
>	- initialize the **list of unprocessed variables** $$\mathcal{U} \leftarrow \mathcal{X}$$
>- While $\mathcal{U} \neq \emptyset$:
>	- Choose $X_{i} \in \mathcal{U}$
>	- Store the *previous* marginal distribution assignments $$Q_{old}(X_{i}) \leftarrow Q(X_{i})$$
>	- For $x_{i}\in \mathcal{X}_{i}$:
>		- Update each **new assignment** of $Q(X_{i})$ $$Q(x_{i}) \leftarrow \exp \left\{\sum_{\phi: X_{i}\in \text{scope}(\phi)}\mathbb{E}_{ (X_{\phi} \setminus \{ X_{i} \})  \sim Q }\left[\log \phi(X_{\phi}, x_{i})\right] \right\} $$
>	- **Normalize** the *marginal distribution* $Q(X_{i})$
>	- If $Q_{old}(X_{i}) \neq Q(X_{i})$:
>		- Include all *other variables* in scopes of factors $\phi$ into the *unprocessed list* $$\mathcal{U} \leftarrow \mathcal{U} \;\cup\; \bigcup_{\phi: X_{i}\in \text{scope}(\phi)}\text{scope}(\phi)$$
>	- Mark $X_{i}$ as processed: $$\mathcal{U} \leftarrow \mathcal{U} \setminus \{ X_{i} \}.$$
>- Return the *variational distribution* $Q$.

- [[Block Coordinate Descent Algorithm]]

>[!info]
>This is a **coordinate ascent algorithm** which *increase the energy functional* at iteration.

>[!info]
>When a *marginal distributions* $Q(X_{i})$ is *updated*, all **other marginal distributions** whose variable that shared the same potential $\phi$ need to be updated since 
>$$
> Q(x_{j}) \leftarrow \exp \left\{\sum_{\phi: X_{i}, X_{j}\in \text{scope}(\phi)}\mathbb{E}_{ ((X_{\phi} \cup \{ X_{i} \} )\setminus \{ X_{j} \})  \sim Q }\left[\log \phi(X_{\phi}, X_{i}, x_{j})\right] \right\}  
> $$
> 
>Thus we need to revert all related variables back into the *unprocessed list*. 



## Explanation

>[!info]
>From above corollary, $Q(x_{i})$ is the **geometric average** of the **conditional probability** of $x_i$ *given all other variables* in the domain.
>- The **weight of average** is based on *probability assignment* of $Q$
>- In this sense, the *mean field approximation* requires that the **marginal of $X_i$ be “consistent” with the marginals of other variables**.
>  
>Note
>$$
>P_{\Phi}(x_{i}) = \sum_{x_{-i}}P_{\Phi}(x_{-i})\,P_{\Phi}(x_{i} | x_{-i}) = \mathbb{E}_{ X_{-i} \sim P_{\Phi} }\left[  P_{\Phi}(x_{i} | X_{-i}) \right]
>$$  
>- This is **arithmetic average**, whereas the *mean field approximation* is the **geometric average.**
>- Also this expectation is with respect to $P_{\Phi}$ while the *mean field* uses the approximation $Q$ 

### Why Mean Field

![[Structured Variational Approximation#^ea614b]]

![[Structured Variational Approximation#^3ca63f]]

![[Structured Variational Approximation#^4cc9e0]]

![[Structured Variational Approximation#^dc3a63]]

- [[Structured Variational Approximation]]


-----------
##  Recommended Notes and References


- [[Information Projection and Moment Projection]]

- [[Kullback-Leibler Divergence]]
- [[Cross-Entropy Loss Function]]
- [[Maximum Entropy Learning]]
- [[Maximum Entropy Learning of Clique Tree PGM]]

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network on Undirected Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 449 - 469
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 125 - 147
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
