---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning
keywords:
  - epsilon_greedy_algorithm
  - multi_arm_bandit
  - reinforcement_learning
topics:
  - bandit_problem
  - reinforcement_learning
name: epsilon-Greedy Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: epsilon-Greedy Algorithm

![[Explore-Then-Commit Bandit Algorithm#^37b26f]]

![[Explore-Then-Commit Bandit Algorithm#^463d5d]]


>[!important] Definition
>The **$\epsilon$-Greedy** algorithm is a *randomized relative* of **ETC** algorithm, which is described as below:
>- *Require*: the parameter $\epsilon\in [0,1]$
>- *Require*: arms $\{ 1 \,{,}\ldots{,}\, k\}$
>- *Initialize* the list of rewards $\hat{\mu}_{i}(0)=0$ for $i=1\,{,}\ldots{,}\,k$
>- *Initialize* the number of play $T_{i}(0) = 0$.
>- For $t=1\,{,}\ldots{,}\,T$:
>	- If $t \le k$:
>		- Choose one new arm $A_{t} = t$
>	- Else:
>		- **Sample** a **random action** $A \sim \text{Uniform}\{ 1\,{,}\ldots{,}\, k\}$
>		- Choose **action (arm)**  $A_{t}$  according to the following rule $$A_{t} = \left\{ \begin{array}{cc} A & \text{ with probability }\epsilon\\ \arg\max_{i}\,\hat{\mu}_{i}(t-1) &\text{ with probability }1 - \epsilon \end{array} \right.$$
>	- Observe **reward** $X_{t}$
>	- Update the *number of times* that the arm $A_{t}$ is played as $$T_{i}(t)  = \left\{ \begin{array}{cc} T_{i}(t-1) + 1 & \text{ if } i = A_{t}\\ T_{i}(t-1)&\text{ if } i\neq A_{t}\end{array} \right.$$
>	- Update the **average reward** for all arms $i=1\,{,}\ldots{,}\,k$ $$\hat{\mu}_{i}(t)  = \left\{ \begin{array}{cc} \hat{\mu}_{i}(t-1) + \dfrac{1}{T_{i}(t)}\left(X_{t} - \hat{\mu}_{i}(t-1)\right) & \text{ if } i = A_{t}\\ \hat{\mu}_{i}(t-1) &\text{ if } i\neq A_{t}\end{array} \right.$$

- [[Explore-Then-Commit Bandit Algorithm]]



## Explanation





-----------
##  Recommended Notes and References


- [[Explore-Then-Commit Bandit Algorithm]]
- [[Multi-Armed Adversarial Bandit]]




- [[Reinforcement Learning An Introduction by Sutton]] pp 25 - 32
- [[Distributional Reinforcement Learning by Bellemare]] pp 303
- [[Bandit Algorithms by Lattimore]] pp 81
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1148
