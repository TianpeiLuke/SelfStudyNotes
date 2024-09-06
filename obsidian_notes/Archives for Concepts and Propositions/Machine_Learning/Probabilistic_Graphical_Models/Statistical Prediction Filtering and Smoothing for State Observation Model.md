---
tags:
  - concept
  - statistics/signal_processing
  - statistics/estimation
  - machine_learning/models
  - deep_learning/sequential_networks
  - probabilistic_graphical_models/sequential_models
keywords:
  - prediction_problem
  - smoothing_problem
  - filtering_problem
  - state_observation_model
topics:
  - statistics/estimation
  - probabilistic_graphical_model
  - statistics/signal_processing
  - dynamic_system
name: Statistical Prediction Filtering and Smoothing for State Observation Model
date of note: 2024-08-14
---

## Concept Definition

>[!important]
>**Name**: Statistical Prediction Filtering and Smoothing for State Observation Model

![[State-Observation Models#^dc6850]]


>[!important] Definition
>Consider the *state observation model* or *state space model (SSM)* where the joint distribution of a sequence o *states* and *observations* given inputs can be factorized as
>$$
>\mathcal{P}(O^{(1:T)}, X^{(1:T)}\;|\;U^{(1:T)}) = \left[ \mathcal{P}(X^{(1)}|U^{(1)})\,\prod_{t=2}^{T}\mathcal{P}\left(X^{(t)}\,|\,X^{(t-1)},\, U^{(t)}\right) \right]\,\left[ \prod_{t=1}^{T}\,\mathcal{P}\left(O^{(t)}\,|\,X^{(t)},\,U^{(t)} \right)\right]  
>$$
>
>Given the sequence of observations, and a known model, one of the main tasks with SSMs is to perform *posterior inference* about the *hidden states*;  this is also called **state estimation**.

- [[State-Observation Models]]
- [[State Space Models and Nonlinear Dynamic System]]
- [[Dynamic Bayesian Network]]

### Prediction Problem

>[!important] Definition
>The task of **(Bayesian) prediction** is to compute the conditional probability $$\mathcal{P}(X^{(t+s)}\,| O^{(1: t)})$$ where the task is to estimate the hidden state at *future time* $(t+s)$, given all *historical time* $<t$ and *present time* $t$ observations. 

- [[Hidden Markov Model Inference via Forward-Backward Algorithm]]
- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]

>[!info]
>By Markov property, the **prediction task** can be done by pushing the *current* **belief state** through *dynamic model*
>$$
>\mathcal{P}(X^{(t+s)}\,|\,O^{(1:t)}) = \sum_{X^{(t : t+s-1)}}\left\{ \mathcal{P}(X^{(t)}\,|\,O^{(1: t)})\,\left[\prod_{\tau=t+1}^{t+s}\mathcal{P}(X^{(\tau)}\,|\,X^{(\tau-1)})\right] \right\}
>$$

- [[Sum-Product Variable Elimination]]
- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Sum-Product Belief-Update Message Passing Algorithm for Clique Tree]]

>[!important] Definition
>The task of **observation prediction** is to predict the *future observations* given *past* and *current observations*
>$$
>\mathcal{P}(O^{(t+s)}\,|\,O^{(1:t)}) = \sum_{X^{(t+s)}}\mathcal{P}(O^{(t+s)}\,|\,X^{(t+s)})\,\mathcal{P}(X^{(t+s)}\,|\, O^{(1: t)})
>$$

### Filtering Problem

>[!important] Definition
>The task of **(Bayesian) filtering** is to compute the **belief state** $$\mathcal{P}(X^{(t)}\,|\, O^{(1: t)})$$
>where we want to estimate the hidden state at *current time* $t$, given all *historical time* $<t$ and *present time* $t$ observations.
>
>Filtering task is also called a **tracking** task. 


- [[Bayesian Filtering and Smoothing Equations for State Observation Models]]
- [[Kalman Filter Discrete-Time]]
- [[Kalman Filter Continuous-Time]]
- [[Particle Filter or Sampling-Importance-Resampling]]
- [[Sequential Importance Sampling]]

### Smoothing Problem

>[!important] Definition
>The task of **(Bayesian) smoothing** is to compute the conditional probability  $$\mathcal{P}(X^{(t)}\,|\, O^{(1: T)})$$
>where we want to estimate the hidden state at *current time* $t$, given all *historical time* $<t$ and *present time* $t$, and *future time* $>t$ observations. 
>

- [[Monte Carlo Control with Exploring Starts]]

>[!important] Definition
>The task of **fixed-lag smoothing** is to compute the conditional probability  $$\mathcal{P}(X^{(t-s)}\,|\, O^{(1: t)})$$
>where we want to estimate the hidden state at *past time* $(t-s)$ with a **lag** $s$, given all *historical time* $<t$ and *present time* $t$ observations. 
>

- [[Multi-Step SARSA Algorithm Off-Policy]]
- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]


![[filtering_smoothing_prediction.png]]

### Interpolation 

>[!important] Definition
>The task of **interpolation** is to estimate $$\mathcal{P}(O^{(t)}\,|\,O^{(1: t-1)},\, O^{(t+1 : T)})$$
>where the *current observations* at $t$  given *past* $<t$ and *future observations* $>t$.

- [[Self-Supervised Learning]]


## Explanation

>[!info]
>Compare **smoothing** with **prediction** and **filtering** , we see that given *future observations*, the *uncertainty* of estimating the hidden state *at present time* is greatly *reduced* since it is easier to explain in **hindsights**
>
>A **disadvantage** of the smoothing method is that we have to *wait until all the data has been observed* before we start performing inference, so it cannot be used for **online** or **realtime** problems.

- [[Hindsight Bias]]

>[!info]
>The **filtering task** is the **core** of *posterior inference task* for *state observation model*.

- [[Bayesian Filtering and Smoothing Equations for State Observation Models]]


-----------
##  Recommended Notes and References


- [[State-Observation Models]]
- [[State Space Models and Nonlinear Dynamic System]]
- [[Linear Dynamic System]]


- [[Hidden Markov Model]]
- [[Extended Kalman Filter]]
- [[Kalman Filter Discrete-Time]]
- [[Particle Filter or Sampling-Importance-Resampling]]
- [[Dynamic Bayesian Network]]


- [[Markov Decision Process]]
- [[Sequential Decision Process]]
- [[Statistical Estimation Problem]]
- [[Statistical Inference Problem]]
- [[Statistical Decision Problem]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 353 - 358
- [[Probabilistic Graphical Models by Koller]] pp 652 - 654