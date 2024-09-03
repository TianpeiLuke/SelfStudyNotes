---
tags:
  - concept
  - machine_learning/models
keywords:
  - state_observation_model
topics:
  - machine_learning_models
name: State-Observation Models
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: State-Observation Models

>[!important] Definition
>Let $(X^{(t)}), (O^{(t)})_{t=1\,{,}\ldots{,}\,}$ be two discrete-time stochastic process, where 
>- $X^{(t)} \in \mathcal{X}$ is the *state* of *dynamic system* at time $t$.
>- and $O^{(t)} \in \mathcal{O}$ is the *observation* at time $t$.
>  
>A **state space model**  utilize two conditional independence assumptions:
>- **Markov assumption for state process**:  *future state* is independent from *past states*  given the *current state* $$(X^{(t+1)} \perp  X^{(0:t-1)} \,|\, X^{(t)} )$$
>- **Markov assumption for observation**: the *current observation* is independent from both *future* and *past states* given the *current state* $$(O^{(t)} \perp  \{X^{(0:t-1)},\, X^{(t+1:\infty)} \} \,|\, X^{(t)} )$$
>  
>A  **state space model** consists of two components
>- the **transition model** or **dynamic model** $$\mathcal{P}(X^{(t+1)} | X^{(t)})$$
>- the **observation model** or **measurement model** $$\mathcal{P}(O^{(t)} | X^{(t)})$$

^dc6850

>[!info]
>From the perspective of **DBNs**, this type of model corresponds to a **2-TBN** structure where the observation variables $O'$ are all *leaves*, and have *parents only* in $X'$.


## Explanation

>[!quote]
>An alternative way of thinking about a temporal process is as a **state-observation model**. In a states-observation model, we view the system as *evolving* naturally *on its own*, with our observations of it occurring in a *separate process*. This view **separates** out the **system dynamics** from our **observation model**, allowing us to consider each of them separately. It is particularly useful when our observations are obtained from a (usually noisy) sensor, so that it makes sense to model separately the dynamics of the system and our ability to sense it.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 207

## Partially Observed Markov Model

>[!important]
>A state-observation model is a **partially observed Markov model**.

- [[Markov Decision Process]]

## State Space Model

- [[Linear Dynamic System]]
- [[State Space Models and Nonlinear Dynamic System]]
- [[Statistical Prediction Smoothing and Filtering for State Observation Model]]

## Sampling

- [[Sequential Importance Sampling]]
- [[Particle Filter or Sampling-Importance-Resampling]]



-----------
##  Recommended Notes and References


- [[Extended Kalman Filter]]
- [[Kalman Filter Discrete-Time]]
- [[Sequential Importance Sampling]]
- [[Particle Filter or Sampling-Importance-Resampling]]


- [[Dynamic Bayesian Network]]
- [[Markov Chain Monte Carlo Methods]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Probabilistic Graphical Models by Koller]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 357
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]