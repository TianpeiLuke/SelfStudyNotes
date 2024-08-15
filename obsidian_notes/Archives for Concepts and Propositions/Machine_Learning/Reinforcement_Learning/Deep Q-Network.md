---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/algorithm
keywords:
  - q_learning
  - double_q_learning
topics:
  - reinforcement_learning/algorithm
name: Double Q Learning Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Double Q Learning Algorithm

![[Q Learning Algorithm and Off-Policy Temporal Difference Control#^d64bd3]]

![[Value Function Approximation as Supervised Learning#^edee92]]

>[!important] Definition
>In **deep Q-Network (DQN)**, the action-value function $Q$ is approximated by *deep neural network*, i.e.
>$$
>Q(x, a) \approx  \hat{q}(x, a; w) \quad \forall (x, a) \in \mathcal{X} \times \mathcal{A}
>$$
>which is learned by minimizing the *squared error* for *each step* $t$
>$$
>\mathcal{L}_{DQN} := \lVert U_{t} - \hat{q}(x, a; w_{t}) \rVert^2 
>$$
>where the *semi-gradient Q-Learning* **target** is
>$$
>U_{t} := R_{t+1} + \gamma\, \max_{a' \in \mathcal{A}(X_{t+1})}\,\hat{q}\left(X_{t+1}, a'; w_{t}\right)
>$$

- [[Semi-Gradient Temporal Difference]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]
- [[Value Function Approximation as Supervised Learning]]

### DQN Update

![[Semi-Gradient Temporal Difference#^5680d7]]

>[!important] Definition
>At each step $t$, the **deep Q-network (DQN) update** is the *semi-gradient update*
>$$\begin{align*}
>w_{t+1} &= w_{t} + \alpha\,\left[ U_{t}  - \hat{q}(X_{t}, A_{t}; w_{t}) \right]\;  \nabla_{w}\hat{q}(X_{t}, A_{t}; w_{t})\\[5pt]
>&=  w_{t} + \alpha\,\left[ R_{t+1} + \gamma\, \max_{a' \in \mathcal{A}(X_{t+1})}\,\hat{q}\left(X_{t+1}, a'; w_{t}\right) - \hat{q}(X_{t}, A_{t}; w_{t}) \right]\;  \nabla_{w}\hat{q}(X_{t}, A_{t}; w_{t})
>\end{align*}
>$$
>- A **target network** is the function $\hat{q}\left(X_{t+1}, a'; w_{t}\right)$ in the *learning target* $$U_{t} := R_{t+1} + \gamma\, \max_{a' \in \mathcal{A}(X_{t+1})}\,\hat{q}\left(X_{t+1}, a'; w_{t}\right)$$
>- A **fitted network** is the model $\hat{q}(x, a; w_{t})$ that *minimize the squared error* with respect to a *target network* $$\mathcal{L}_{DQN} := \lVert U_{t} - \hat{q}(x, a; w_{t}) \rVert_{2}^2 $$
>


## Explanation

>[!important]
>- When *updating the weights*, one also **changes the target**. Due to the *generalization and extrapolation* abilities of neural networks, this approach can build **large errors** at different places in the state-action space
>- Instead of update the weight $w_{t}$ every iteration, the weight is *updated every* $n\in \mathbb{N}$ iterations.






-----------
##  Recommended Notes and References



- [[Double Q Learning Algorithm]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]
- [[Temporal Difference Learning]]
- [[Residual Neural Network]]
- [[Convolutional Neural Network]]


- [[Bellman Optimality Equation for MDP]]
- [[Value Function and Bellman Equation for MDP]]
- [[Markov Decision Process]]




- [[Deep Learning by Goodfellow]]
- [[Reinforcement Learning An Introduction by Sutton]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1143 - 1144
