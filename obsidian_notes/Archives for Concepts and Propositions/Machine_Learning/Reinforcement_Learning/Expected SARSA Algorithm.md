---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - expected_sarsa_algorithm
  - temporal_difference_learning
topics:
  - reinforcement_learning/algorithm
name: Expected Sarsa Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Expected Sarsa Algorithm

>[!info]
>One of the early breakthroughs in reinforcement learning was the development of an off-policy TD control algorithm known as **Q-learning**.
>
>Instead of Bellman equation for $q$, we now consider the *Bellman optimality equation* for $q_{*}$

![[Value Function and Bellman Equation for MDP#^f9fda7]]

![[SARSA Algorithm and On-Policy Temporal Difference Control#^cf105f]]

### Expected SARSA Update

>[!important] Definition
>**Expected Sarsa** has the **update** rule as 
>$$
> \begin{align}
> Q(X_{t}, A_{t}) &\leftarrow Q(X_{t}, A_{t}) + \alpha_{t}\left[ R_{t+1} + \gamma\sum_{a'}\pi(a'|\,X_{t+1})\,Q(X_{t+1}, a')  - Q(X_{t}, A_{t}) \right] .
> \end{align}
>$$ 
>- The **TD error** is defined as $$\delta_{t} :=  R_{t+1} + \gamma\sum_{a'}\pi(a'|\,X_{t+1})\,Q(X_{t+1}, a')  - Q(X_{t}, A_{t}) $$

- [[Value Function and Bellman Equation for MDP]]
- [[SARSA Algorithm and On-Policy Temporal Difference Control]]

### Expected SARSA Algorithm for Off-Policy Control

>[!important] Definition
>The **expected SARSA algorithm** is described in the following.
>
>- *Require*: action space $\mathcal{A}(x)$
>- *Require*: step size $\alpha_{t} >0$ for $t=1\,{,}\ldots{,}\,$
>- *Require*: reward *discount factor* $\gamma >0$
>- *Require*: $\epsilon >0$ controls the exploration. 
>- *Initialize* **table for action-value function** $Q_{0}(x, a)$ for all $x\in \mathcal{X}$ and $a\in \mathcal{A}$. 
>	- Note that the **terminal state** $Q_{0}(x_{\text{terminal}}, a) = 0$ for all $a\in \mathcal{A}$
>- For **episode** $k=1,\,2\,{,}\ldots{,}\,$:
>	- Initialize state $X_{0}$
>	- For step $t=0,\,1\,{,}\ldots{,}\,T$:
>		- *Randomly generate* an action $A \sim \text{Uniform}(\mathcal{A}(X_{t}))$
>		- Choose **action** $A_{t}$ given $Q_{t}$ and **current state** $X_{t}$ according to the **$\epsilon$-greedy policy** $\pi$ $$A_{t} = \left\{ \begin{array}{cc} A & \text{ with probability }\epsilon\\ \arg\max_{a\in \mathcal{A}(X_{t})}\,Q_{t}(X_{t}, a) &\text{ with probability }1 - \epsilon \end{array} \right.$$
>		- Observe **reward** $R_{t+1}$ and **next state** $X_{t+1}$
>		- Estimate the **expected value** of $Q_{t}(X_{t+1}, a)$ given $X_{t+1}$ according to $\pi$ via *Monte Carlo methods* 
>			- Sample $m$ action according to the **$\epsilon$-greedy policy** $\pi$,  $$A^{(i)} = \left\{ \begin{array}{cc} \text{Unfiorm}(\mathcal{A}(X_{t+1})) & \text{ with probability }\epsilon\\ \arg\max_{a\in \mathcal{A}(X_{t+1})}\,Q_{t}(X_{t+1}, a) &\text{ with probability }1 - \epsilon \end{array} \right. \; i=1\,{,}\ldots{,}\,m$$ 
>			- Compute the sample mean $$\widehat{\mathbb{E}}_{\pi}\left[ Q_{t}(X_{t+1}, A) \right] = \frac{1}{m}\sum_{i=1}^{m}Q_{t}(X_{t+1}, A^{(i)}).$$
>		- **Expected SARSA update** $$Q_{t+1}(X_{t}, A_{t}) = Q_{t}(X_{t}, A_{t}) + \alpha_{t}\left[ R_{t+1} + \gamma \widehat{\mathbb{E}}_{\pi}\left[ Q_{t}(X_{t+1}, A) \right]  - Q_{t}(X_{t}, A_{t}) \right] $$


## Explanation

>[!important]
>**Expected Sarsa** is an algorithm derived from the *same Bellman equation* as the **Sarsa**. 
>
>However, instead of sample the next action $A_{t+1}$, we can directly **computed the exact expected** value since we know policy $\pi(a'|\cdot), \forall\,a'$. 
>
>Compare to **Q-learning**, we can replace the **maximization** with the **expectation**. 

- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]

>[!important] 
>Expected Sarsa is an **off-policy control** since the *update* does not depend on the *behavior policy* that generates the new action since the expectation is computed for *all* actions. 

- [[On-Policy and Off-Policy Reinforcement Learning]]
- [[Prediction and Control Problems in Reinforcement Learning]]

>[!info]
>Given the next state, $S_{t+1}$, this algorithm moves **deterministically** in the same direction as Sarsa moves in *expectation*.
>
>**Expected Sarsa** is more *complex computationally* than Sarsa but, in return, it **eliminates the variance** due to the random selection of $A_{t+1}$. 
>
>Given the same amount of experience we might expect it to perform slightly better than Sarsa, and indeed it generally does. By evaluating *all actions* instead of the *maximal action*, the expected Sarsa would choose actions more safely to *avoid potential high loss* when choosing the optimal action deterministically. 








-----------
##  Recommended Notes and References

- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]
- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Temporal Difference Learning]]



- [[Bellman Optimality Equation for MDP]]
- [[Value Function and Bellman Equation for MDP]]
- [[Markov Decision Process]]



- [[Reinforcement Learning An Introduction by Sutton]] pp 133

