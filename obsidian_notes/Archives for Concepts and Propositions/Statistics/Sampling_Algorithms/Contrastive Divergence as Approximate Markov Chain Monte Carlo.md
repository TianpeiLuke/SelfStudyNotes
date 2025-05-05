---
tags:
  - concept
  - statistics/monte_carlo_simulation
  - deep_learning/models
  - deep_learning/algorithms
  - contrastive_divergence
  - RBM
keywords:
  - contrastive_divergence
  - RBM
topics:
  - monte_carlo
  - markov_chain_monte_carlo
name: Contrastive Divergence as Approximate Markov Chain Monte Carlo
date of note: 2024-09-08
---

## Concept Definition

>[!important]
>**Name**:  Contrastive Divergence as Approximate Markov Chain Monte Carlo

![[Gibbs Measure and Energy-based Model#^c81bcd]]

- [[Gibbs Measure and Energy-based Model]]
- [[Markov Chain Monte Carlo Methods]]


### Contrastive Divergence for RBM

>[!important] Definition
>A common learning algorithm for RBMs is **Contrastive Divergence (CD)**. 
>- The **CD-$k$ algorithm** approximates the gradient of the log-likelihood.
>
>For CD-1:
>
>- *Require*: Training data $V = \{v^{(1)}, v^{(2)}, \ldots, v^{(N)}\}$
>- *Require*: Number of hidden units $m$
>- *Require*: Learning rate $\alpha$
>- *Initialize*: Weights $W^{(0)}$, visible biases $a^{(0)}$, and hidden biases $b^{(0)}$ (e.g., with small random values)
>- For each iteration:
>	- For each data point $v$ in the training data:
>		- **Forward Pass:** 
>			- Compute the *probabilities* of the *hidden units* $$P(h|v; \theta^{(t)})$$
>			- *Sample a hidden vector* $h^{(0)}$ from this distribution.
>		- **Reconstruction:** 
>			- Compute the probabilities of the *visible units* $$P(v'|h^{(0)}; \theta^{(t)})$$
>			- Sample a *reconstructed visible vector* $v'$ from this distribution.
>		- **Backward Pass:** 
>			- Compute the probabilities of the hidden units $$P(h'|v'; \theta^{(t)}).$$
>		- **Update Parameters:**
>			- $\Delta W = \alpha (v h^{(0)T} - v' h'^T)$
>			- $\Delta a = \alpha (v - v')$
>			- $\Delta b = \alpha (h^{(0)} - h')$
>		- Update the parameters:
>			- $W^{(t+1)} = W^{(t)} + \Delta W$
>			- $a^{(t+1)} = a^{(t)} + \Delta a$
>			- $b^{(t+1)} = b^{(t)} + \Delta b$
>- *Return*: Learned parameters $W^*$, $a^*$, $b^*$ that define the probability distribution.

- [[Restricted Boltzmann Machine or RBM]]

## Explanation




## Langevin MCMC

- [[Langevin Dynamics and Langevin Sampling]]



-----------
##  Recommended Notes and References


- [[Gibbs Sampling]]



- [[Artificial Neural Network and Deep Learning]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 
- [[Deep Learning by Goodfellow]] pp 601 - 606
- [[Deep Learning Foundations and Concepts by Bishop]] pp 455