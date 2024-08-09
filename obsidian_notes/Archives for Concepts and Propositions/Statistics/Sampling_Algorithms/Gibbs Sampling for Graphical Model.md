---
tags:
  - concept
  - statistics/monte_carlo_simulation
keywords:
  - gibbs_sampling
  - probabilistic_graphical_model
topics:
  - statistics/monte_carlo
  - probabilistic_graphical_model
name: Gibbs Sampling for Graphical Model
date of note: 2024-07-04
---

## Concept Definition

>[!important]
>**Name**: Gibbs Sampling for Graphical Model

![[Gibbs Sampling#^655bf6]]

- [[Gibbs Sampling]]
- [[Local Probabilistic Models]]


>[!important] Definition
>Consider the task of sampling for **Markov Network** $(p, \mathcal{H})$
>$$
> p(x_{1} \,{,}\ldots{,}\,x_{d}) = \frac{1}{Z}\prod_{i=1}^{k}\phi(D_{i})
>$$
>where $\phi_{D_{i}}$ is the factor corresponding to a clique $D_{i}$ in $\mathcal{H}$ and $p$ factorizes according to a *clique graph* $\mathcal{H}$.
>
>By [[Markov Blanket and Local Markov Independence]], we have the **local Markov property**
>$$\mathcal{I}_{\ell}(\mathcal{H}) := \left\{ \left(X \perp \mathcal{X} - \{ X,\, \text{MB}_{\mathcal{H}}(X) \}\;|\;\text{MB}_{\mathcal{H}}(X)\right):\; X \in \mathcal{X} \right\}.$$
>
>Therefore, at each iteration $t$ of Gibbs sampling, we just need to use coordinates in a **Markov Blanket** $j\in \text{MB}_{\mathcal{H}}(i)$ in order to sample $X_{i}$. That is
>$$
>X_{i}^{(t)} \sim p\left( x_{i}\,\Big|\, \left\{  X_{j}^{(t-1)},\;\; \forall j\in \text{MB}_{\mathcal{H}}(i)\right\} \right)
>$$


- [[Gibbs Distribution]]
- [[Markov Blanket and Local Markov Independence]]
- [[Hammersley-Clifford Theorem]]
- [[Markov Network on Undirected Graph]]

>[!important] Definition
>Consider the task of sampling for **Bayesian Network** $(p, \mathcal{G})$, and 
>$$
> p(x_{1} \,{,}\ldots{,}\,x_{d}) = \prod_{i=1}^{d}p(x_{i} \,|\,x_{Pa(i)})
>$$
>where $Pa(i)$ is the parent variables in $\mathcal{G}$ and $p$ factorizes according to $\mathcal{G}$.
>
>By [[D-Separation in Bayesian Network]], we have the **local Markov property**
>$$
>\mathcal{I}_{\ell}(\mathcal{G}):= \{ \left( X_{i} \perp X_{\text{NonDescendant}_{G}(i)} \,\lvert\,X_{Pa(i)}\right)\quad \forall i\in \mathcal{V}. \}. 
>$$
>
>Therefore, at each iteration $t$ of Gibbs sampling, we just need to use coordinates in a **Parent nodes** $j\in Pa(i)$ in order to sample $X_{i}$. That is
>$$
>X_{i}^{(t)} \sim p\left( x_{i}\,\Big|\, X_{Pa(i)}^{(t-1)} \right)
>$$






## Explanation


>[!important]
>Gibbs sampling naturally fit the structure of **probabilistic graphical model** since 
>- it only requires **local probabilistic models** or **factors** to generate each coordinate sample.
>- Also, the *order relation* in graph structure (esp. in Bayesian network) provides a direction for **scanning** in Gibbs sampling.






-----------
##  Recommended Notes and References


- [[Gibbs Sampling]]

- [[Metropolis-Hastings Algorithm]]
- [[Markov Chain and Markov Process]]
- [[Block Coordinate Descent Algorithm]]

- [[Markov Chain Monte Carlo Methods]]

- [[Gibbs Distribution]]


- [[All of Statistics A Concise Course by Wasserman]] pp 411 - 415
- [[Monte Carlo Statistical Methods by Robert]]
- [[Monte Carlo Strategies in Scientific Computing by Liu]] pp 129 - 151

- [[Probabilistic Graphical Models by Koller]] pp 506, 512
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 477 - 537
- [[Deep Learning by Goodfellow]] pp 590
- [[Deep Learning Foundations and Concepts by Bishop]] pp 429