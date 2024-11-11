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
name: Double Q Network or DQN
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Double Q Network or DQN

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
>where the **target** consists of the next reward and the optimal value of Q-network
>$$
>U_{t} := R_{t+1} + \gamma\, \max_{a' \in \mathcal{A}(X_{t+1})}\,\hat{q}\left(X_{t+1}, a'; w_{t}\right)
>$$

- [[Artificial Neural Network and Deep Learning]]
- [[Semi-Gradient Temporal Difference]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]
- [[Value Function Approximation as Supervised Learning]]


>[!info]
>At each iteration $t$, the state $x'$ can be provided as an **input** to the *Q-network* and a different output is given for *each of the possible actions* $a\in \mathcal{A}(x)$. 
>
>This provides an efficient structure that has the advantage of obtaining the *computation of* $$ \max_{a' \in \mathcal{A}(X_{t+1})}\,\hat{q}\left(x', a'; w_{t}\right)$$ in a **single forward pass** in the neural network for a given $x'$.

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

### Replay Memory

>[!important] Definition
>In an online setting, the **replay memory**  keeps *all information* for the *last* $N_{replay}\in \mathbb{N}$ time steps, where the experience is collected by following an *$\epsilon$-greedy policy*. 
>$$A_{t} = \left\{ \begin{array}{cc} \text{ random action} & \text{ with probability }\epsilon\\ \arg\max_{a}\,\hat{q}(X_{t}, a; w_{t}) &\text{ with probability }1 - \epsilon \end{array} \right.$$
>
>The updates are then made on a set of tuples $$(X_{t}, A_{t}, R_{t+1}, X_{t+1}),$$ called **mini-batch**, selected *randomly* within the *replay memory*.

- [[epsilon-Greedy Algorithm]]

### DQN Algorithm

![[dqn_architecture.png]]

### Double DQN

>[!info]
>The *max operation* in **Q-learning** 
>$$
>U_{t} := R_{t+1} + \gamma\, \max_{a' \in \mathcal{A}(X_{t+1})}\,\hat{q}\left(X_{t+1}, a'; w_{t}\right)
>$$
>uses the same values both to **select** and to **evaluate** an action.
>
>This makes it more likely to select **overestimated values** in case of inaccuracies or noise, resulting in overoptimistic value estimates.
>- The DQN algorithm induces an **upward bias**.

>[!important]
>The **double estimator method** uses two estimates for each variable, which allows for the *selection* of an estimator and its *value* to be *uncoupled*.
>- this allows for the removal of the positive bias in estimating the action values.

>[!important] Definition
>In **Double DQN** or **DDQN**, the *target* is replaced by
>$$
>U_{t} := R_{t+1} + \gamma\, \hat{q}\left(X_{t+1},\; \arg\max_{a' \in \mathcal{A}(X_{t+1})}\,\hat{q}(X_{t+1}, a'; w_{t});\; \bar{w}_{t}\right)
>$$




## Explanation

>[!quote]
>- When *updating the weights*, one also **changes the target**. Due to the *generalization and extrapolation* abilities of neural networks, this approach can build **large errors** at different places in the state-action space
>  
>-- [[An Introduction to Deep Reinforcement Learning by Francois-Lavet]] pp 245  

>[!quote]
>- Instead of update the weight $w_{t}$ every iteration, the *weight in target network* is *updated every* $C\in \mathbb{N}$ iterations.
>- The idea of *target networks* can be seen as an **instantiation of fitted Q-learning**, where each period between **target network** *updates* corresponds to a **single fitted Q-iteration**.
>  
>-- [[An Introduction to Deep Reinforcement Learning by Francois-Lavet]] pp 245    

>[!quote]
>In addition to the **target Q-network** and the **replay memory**, DQN uses other important heuristics. To keep the target values in a reasonable scale and to ensure proper learning in practice, **rewards are clipped** between $-1$ and $+1$. Clipping the rewards *limits the scale of the error derivatives* and makes it easier to use the same learning rate across multiple games (however, it introduces a bias). In games where the player has multiple lives, one trick is also to **associate a terminal state** to the *loss of a life* such that the agent avoids these terminal states (in a terminal state the discount factor is set to 0).
>
>-- [[An Introduction to Deep Reinforcement Learning by Francois-Lavet]] pp 246








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
- [[Artificial Neural Network and Deep Learning]]



- [[Deep Learning by Goodfellow]]
- [[Reinforcement Learning An Introduction by Sutton]] pp 236
- [[Distributional Reinforcement Learning by Bellemare]] pp 294 - 297
- [[An Introduction to Deep Reinforcement Learning by Francois-Lavet]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1143 - 1144
