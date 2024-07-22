---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/theory
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/inference
keywords:
  - variational_inference
  - probabilistic_graphical_model
  - clique_tree
topics:
  - probabilistic_graphical_model
name: Variational Inference for Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Solution of Bethe Variational Inference

![[Maximum Entropy Learning of Clique Tree PGM#^f81f88]]

![[Bethe Variational Inference for Clique Tree#^9e261d]]


- [[Bethe Variational Inference for Clique Tree]]
- [[Bethe Entropy Approximation and Factorized Energy Functional]]
- [[Variational Inference for Clique Tree and Cluster Graph]]
- [[Maximum Entropy Learning of Clique Tree PGM]]

>[!important] Definition
>Define 
>- $\lambda_{i}$ as the *dual variable* corresponding to the *normalization constraint* $$\sum_{c_{i}}\beta_{i}(c_{i}) = 1,\;\; \forall i \in V(T),$$ 
>- and $\lambda_{i\to j}(s_{i,j})$ as the *dual variable* corresponding to the *local consistency constraint* $$ \mu_{i,j}(s_{i,j}) = \sum_{c_{i} \setminus s_{i,j}}\beta_{i}(c_{i}),\;\; \forall ij\in E(T), \forall s_{i,j}\in \text{Val}(S_{i,j})$$
>
>The **Lagrangian function** corresponding to the **Bethe variational inference** is 
>$$
>\begin{align*}
>L( (\beta, \mu),  \lambda) &:= \hat{\mathcal{L}}(\mathcal{Q}_{\beta,\mu}, \Phi; \mathcal{X}) - \sum_{i\in V(T)}\lambda_{i}\left(\sum_{c_{i}}\beta_{i}(c_{i}) - 1\right) \\[5pt]
>&\quad- \sum_{ij\in E(T)}\sum_{s_{i,j}}\lambda_{j\to i}(s_{i,j})\left[ \sum_{C_{i} \setminus S_{i,j}}\beta_{i}(c_{i}) -  \mu_{i,j}(s_{i,j})\right] \\[15pt]
>& = \sum_{i\in V(T)}\mathbb{E}_{\beta_{i}}\left[\log \psi(C_{i})\right] + \sum_{i\in V(T)}H_{i}(\beta_{i}) - \sum_{ij \in E(T)}H_{i,j}(\mu_{i,j}) \\[5pt]
>& \quad - \sum_{i\in V(T)}\lambda_{i}\left(\sum_{c_{i}}\beta_{i}(c_{i}) - 1\right)  \\[5pt]
>& \quad - \sum_{i\in V(T)}\sum_{j\in N(i)}\sum_{s_{i,j}}\lambda_{j\to i}(s_{i,j})\left[ \sum_{c_{i} \setminus s_{i,j}}\beta_{i}(c_{i}) -  \mu_{i,j}(s_{i,j})\right] 
>\end{align*}
>$$

- [[Methods of Lagrangian Multipliers]]

### Stationary Point of Variational Inference Problem

>[!info]
>According to the [[Karush-Kuhn-Tucker Optimality Condition]], the **stationary point** of Bethe variational inference problem satisfies the following **equations**
>$$
>\begin{align*}
> \frac{ \partial L }{ \partial \beta_{i}(c_{i}) } &= 0, \quad \forall i\in V(T),\, c_{i}\in \text{Var}(C_{i})\\
> \frac{ \partial L }{ \partial \mu_{i,j}(s_{i,j}) } &= 0, \quad \forall ij\in E(T),\, s_{i,j}\in \text{Var}(S_{i,j})\\[5pt]
> \mu_{i,j}(s_{i,j}) - \sum_{c_{i} \setminus s_{i,j}}\beta_{i}(c_{i}) &=0,\;\; \forall ij\in E(T), \forall s_{i,j}\in \text{Val}(S_{i,j}) \\ 
>  \sum_{c_{i}}\beta_{i}(c_{i}) - 1&=0,\;\; \forall i \in V(T).\\
> &\lambda_{i} \in \mathbb{R} \\
> &\lambda_{i\to j}(s_{i,j}) \in \mathbb{R} \\
>\end{align*}
>$$

>[!info]
>Solving the *LHS* of first two equations 
>$$
>\begin{align*}
>  \frac{ \partial L }{ \partial \beta_{i}(c_{i}) } &= \log \psi_{i}(c_{i}) - \log \beta_{i}(c_{i}) - 1 - \lambda_{i} - \sum_{j\in N(i)}\lambda_{j\to i}(s_{i,j}) \\[5pt]
>  \frac{ \partial L }{ \partial \mu_{i,j}(s_{i,j}) }&= \log \mu_{i,j}(s_{i,j}) + 1 + \lambda_{i \to j}(s_{i,j}) + \lambda_{j \to i}(s_{i,j})
>\end{align*}
>$$

>[!info]
>Rearranging the first two equations based on the LHS form, we have
>$$
>\begin{align*}
> \beta_{i}(c_{i})  &= \exp\left(-1 - \lambda_{i}\right) \; \psi_{i}(c_{i})\; \prod_{j\in N(i)}\exp\left(-\lambda_{j\to i}(s_{i,j})\right) \\[5pt]
> \mu_{i,j}(s_{i,j}) &= \exp\left(-1\right)\; \exp\left(-\lambda_{i\to j}(s_{i,j})\right)\;\exp \left(-\lambda_{j\to i}(s_{i,j})\right)
>\end{align*}
>$$

>[!important] 
>Define the **message** $\delta_{i\to j}$ in terms of **Lagrangian multipliers** $\lambda_{i\to j}$ as
>$$
>\delta_{i\to j}(s_{i,j}) = \exp \left(-\lambda_{i\to j}(s_{i,j}) - \frac{1}{2}\right)
>$$

>[!info]
>Substituting the message definition into the first two equations, we have
>$$
>\begin{align*}
> \beta_{i}(c_{i})  &= \exp\left\{ -1 - \lambda_{i} + \frac{1}{2}|N(i)|\right\} \; \psi_{i}(c_{i})\; \prod_{j\in N(i)}\delta_{j\to i}(s_{i,j})  \\[5pt]
> \mu_{i,j}(s_{i,j}) &= \delta_{i\to j}(s_{i,j}) \, \delta_{j\to i}(s_{i,j}) 
>\end{align*}
>$$

>[!info]
>Combining above with equality constraints in equation 3,4, we have 
>$$
>\begin{align*}
> \delta_{i\to j}(s_{i,j}) &= \frac{\mu_{i,j}(s_{i,j})}{\delta_{j\to i}(s_{i,j})}\\[5pt]
> &=  \frac{\sum_{c_{i} \setminus s_{i,j}}\beta_{i}(c_{i})}{\delta_{j\to i}(s_{i,j})}\\[5pt]
> &=  \exp\left\{ -1 - \lambda_{i} + \frac{1}{2}|N(i)|\right\} \; \psi_{i}(c_{i})\; \frac{\prod_{j\in N(i)}\delta_{j\to i}(s_{i,j})}{\delta_{j\to i}(s_{i,j})} \\[5pt]
> &= \exp\left\{ -1 - \lambda_{i} + \frac{1}{2}|N(i)|\right\} \; \psi_{i}(c_{i})\; \prod_{k\in (N(i) - j)}\delta_{k\to i}(s_{i,k})
>\end{align*}
>$$
>Note that $\exp\left\{ -1 - \lambda_{i} + \frac{1}{2}|N(i)|\right\} = c$ is a *constant*. By solving the normalization constraint equation $$\sum_{c_{i}}\beta_{i}(c_{i})  = 1$$ we can determine the constant as well as $\lambda_{i}$ as $$\lambda_{i} = \frac{1}{2}\left(|N(i)| - 1\right).$$

>[!important] Theorem
>Let $T$ be a clique tree.
>
>A set of beliefs $(\beta, \mu)$ is a **stationary point** of the **Bethe variational inference problem** *if and only if* there exists a set of *factors* $$\left\{ \delta_{i\to j}(S_{i,j})\;\; \forall ij \in E(T)\right\}$$ such that 
>$$
>\begin{align*}
>\delta_{i\to j} &\propto \; \sum_{C_{i} \setminus S_{i,j}}\,\psi_{i}\,\cdot \left(\prod_{k\in (N(i) - j)}\delta_{k \to i}\right)
>\end{align*}
>$$
>and moreover, we have that 
>$$
>\begin{align*}
>\beta_{i}  &\propto\; \psi_{i}\; \cdot \prod_{j\in N(i)}\delta_{j\to i} \\[5pt]
>\mu_{i,j} &= \delta_{i\to j} \, \delta_{j\to i}
>\end{align*}
>$$


>[!quote]
>This theorem characterizes the **solution** of the *optimization problem* in terms of **fixed-point equations** that must hold when we find a **maximal** $\mathcal{Q}$. These fixed-point equations define the *relationships that must hold* between the different *parameters* involved in the optimization problem. Most importantly, equation (11.10) defines each **message** in terms of **other messages**, allowing an easy **iterative approach** to solving the *fixed point equations*. These same themes appear in all the approaches we will discuss later in this chapter.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 390

- [[Fixed Point of Map]]
- [[Contraction Map Principle]]
- [[Sum-Product Message Passing Algorithm for Clique Tree]]
- [[Belief-Update Message Passing Algorithm for Clique Tree]]


## Explanation

>[!quote]
>We can now prove that the **stationary points** of this constrained optimization function — the points at which the gradient is orthogonal to all the constraints — can be characterized by a set of **fixed-point equations**. As we show, these equations turn out to be the update equations in the **sum-product belief-propagation procedure**.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 388

>[!quote]
>The **connection** between the **sum-product algorithm** and the **Bethe variational principle** has a number of important consequences. **First**, it provides a **principled basis** for applying the *sum-product algorithm* for **graphs with cycles**, namely as a particular type of *iterative method* for attempting to satisfy *Lagrangian conditions*. It should be noted, however, that this connection between sum-product and the Bethe problem in itself provides **no guarantees on the convergence** of the sum-product updates on graphs with cycles. ..... However, with the exception of **trees** and other *special cases* \[110, 167, 188\], the *Bethe variational problem* is usually a **nonconvex problem**, in that $H_{\text{Bethe}}$ fails to be *concave*. As a consequence, there are frequently *local optima*, so that even when using a convergent algorithm, there are no guarantees that it will find the global optimum.
>...
>Another important consequence of the Bethe/sum-product connection is in suggesting a *number of avenues* for **improving** upon the ordinary sum-product algorithm, via **progressively better approximations** to the *entropy function* and *outer bounds* on the *marginal polytope*.
>
>-- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 87






-----------
##  Recommended Notes and References


- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]


- [[Variational Inference for Clique Tree and Cluster Graph]]
- [[Maximum Entropy Learning of Clique Tree PGM]]
- [[Evidence Lower Bound]]
- [[Variational Inference vs EM Algorithm]]



- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network Distribution to Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 388 - 390
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 82 - 86

