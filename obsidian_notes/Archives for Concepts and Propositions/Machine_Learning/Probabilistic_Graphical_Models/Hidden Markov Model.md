---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/sequential_models
keywords:
  - hidden_markov_model
topics:
  - probabilistic_graphical_model
  - machine_learning_models
name: Hidden Markov Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Hidden Markov Model

![[State-Observation Models#^dc6850]]

- [[State-Observation Models]]

>[!important] Definition
>A **hidden Markov model (HMM)** is the simplest example of a *state-observation model* where the hidden states form a *chain graph* and each observation variable at $t$ is connected to current state only.
>- In HMM, it is assumed that the *current observation* is independent from *past observations* given the current state: $$\left(O^{(t)} \perp \left\{ O^{0:t-1}, O^{t+1:T}\right\}\,|\, X^{(t)}\right)$$
>
>The *joint distribution* of **HMM** can be factorized as
>$$
>\mathcal{P}\left(O^{(1:T)},\, X^{(1:T)}\right) = \left[ \mathcal{P}(X^{(1)})\,\prod_{t=2}^{T}\mathcal{P}\left(X^{(t)}\,|\,X^{(t-1)}\right) \right]\,\left[ \prod_{t=1}^{T}\,\mathcal{P}(O^{(t)} \,|\,X^{(t)}) \right]  
>$$

^f3f54e

- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]
- [[Autoregressive Models]]


![[hmm.png]]

## Explanation

>[!quote]
>While an HMM is a special case of a simple **DBN**, it is often used to encode structure that is left implicit in the DBN representation. Specifically, the transition model $P (S' | S)$ in an HMM is often assumed to be *sparse*, with many of the possible transitions having zero probability. In such cases, HMMs are often represented using a *different graphical notation* (the **finite state machine**), which visualizes this sparse transition model. In this representation, the HMM transition model is encoded using a *directed (generally cyclic) graph*, whose nodes represent the *different states of the system*, that is, the values in $Val(S)$.

- [[Dynamic Bayesian Network]]

![[finite_state_machine.png]]

>[!info]
>In practice, we only consider **discrete-time** **discrete-state** *Markov chain* for state process.

- [[Markov Chain and Markov Process]]


## Posterior Inference and Forward-Backward Algorithm

- [[Hidden Markov Model Inference via Forward-Backward Algorithm]]

## Maximum A Posteriori Inference and Viterbi Decoding

- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]



-----------
##  Recommended Notes and References


- [[State-Observation Models]]
- [[State Space Models and Nonlinear Dynamic System]]
- [[Linear Dynamic System]]
- [[Sequential Decision Process]]
- [[Dynamic Bayesian Network]]
- [[Markov Chain and Markov Process]]
- [[Sum-Product Variable Elimination]]
- [[Statistical Prediction Filtering and Smoothing for State Observation Model]]

- [[Recurrent Neural Network]]
- [[Conditional Random Field]]


- [[Probabilistic Graphical Models by Koller]] pp 651 - 655
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 15 - 19
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 396, 987 - 993
- [[Deep Learning Foundations and Concepts by Bishop]] pp 480
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 102
- [[Elements of Statistical Learning by Hastie]]
- [[Artificial Intelligence Modern Approach by Russell]]
- [[Speech and Language Processing by Jurafsky]] pp 370 - 373