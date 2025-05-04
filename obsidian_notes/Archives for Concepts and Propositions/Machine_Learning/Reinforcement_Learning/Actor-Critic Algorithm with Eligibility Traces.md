---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning
  - actor_critic_algorithm
  - actor_critic_eligibility_algorithm
  - reinforcement_learning/algorithm
keywords:
  - actor_critic_algorithm
  - actor_critic_eligibility_algorithm
topics:
  - reinforcement_learning/algorithm
name: Actor-Critic Algorithm with Eligibility Traces
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Actor-Critic Algorithm with Eligibility Traces

>[!important] Definition
>Consider the problem of *maximizing the value* for *episodic task* $$\max_{\pi}\;v(x; \pi) := \max_{\pi}\mathbb{E}^{ \pi }\left[ \sum_{k=0}^{\infty}\gamma^{k}\,R_{t+k+1} \,|\,X_{t} = x \right]$$
>where
>-  $\pi$ is the **stochastic policy** *parameterized* by $\theta$ $$\pi(a\,|\,x;\, \theta)$$
>- Let $v(x; \pi)$ be **state-value function** *parameterized* by $w$ $$\hat{v}(x; w)$$ which approximates $v(x; \pi)$ under the regression setting.

### Actor-Critic Algorithm with Eligibility Traces

>[!important] Definition
>For *episodic task*, the **Actor-Critic with Eligibility Trace algorithm** maximizes the expected returns as follows:
>- *Require*: a *differentiable parameterized policy function* $\pi(a\,|\,x;\, \theta)$
>- *Require*: a *differentiable parameterized value function* $\hat{v}(x; w)$
>- *Require*: reward discount factor $\gamma\in (0,1)$
>- *Require*: trace decay parameter $\lambda \in [0, 1]$
>- *Require*: step size $\alpha_{\theta}$ and $\alpha_{w}$
>- Initialize $\theta^{(0)}$ and $w^{(0)}$
>- Initialize eligibility traces for actor and critic: $e_{\theta}^{(0)} = 0$ and $e_{w}^{(0)} = 0$
>- For **episode** $k=1\,{,}\ldots{,}\,$
>	- Sample an Initial State $X_{0}$
>	- Initialize factor $\beta \leftarrow 1$
>	- Reset eligibility traces: $e_{\theta} \leftarrow 0$ and $e_{w} \leftarrow 0$
>	- For $t=1\,{,}\ldots{,}\,$ until $X_{t}$ is **terminal state**:
>		- *Sample* **action** according to the **policy** $$A_{t} \sim \pi(\cdot|\,X_{t-1};\, \theta)$$
>		- Take the action
>		- *Receive* **reward** from *environment* and *Observe* **next state** $$R_{t}, \; X_{t}$$
>		- Compute the **Temporal Difference error (TD error)** $\delta_{t}$ as $$\delta_{t} = R_{t} + \gamma\hat{v}(X_{t}; w) - \hat{v}(X_{t-1}; w) $$
>			- If $X_{t}$ is the *terminal state* then set $$\hat{v}(X_{t}; w) = 0\, \quad \forall w$$
>		- **Critic**: Update the **eligibility trace** for the value function $$e_{w} \leftarrow \gamma \lambda e_{w} + \nabla_{w}\,\hat{v}(X_{t-1}; \,w)$$
>		- **Critic**: Update the **value function parameter** via *gradient descent* $$w \leftarrow w + \alpha_{w}\;\delta_{t}\;e_{w}$$
>		- **Actor**: Update the **eligibility trace** for the policy $$e_{\theta} \leftarrow \gamma \lambda e_{\theta} + \beta \nabla_{\theta}\,\log \pi(A_{t}\;|\;X_{t-1}\,;\, \theta)$$
>		- **Actor**: Update the **policy parameter** via *gradient descent* with stepsize $\alpha_{\theta}$ $$\theta \leftarrow \theta + \alpha_{\theta}\;\delta_{t}\;e_{\theta}$$
>		- Reduce the step size for learning of policy parameters $$\beta \leftarrow \beta\,\gamma$$
>- *Return*
>	- **Actor** returns the **optimal policy** $$\pi(a\,|\,x, \theta^{*})$$
>	- **Critic** returns the **optimal state-value estimation** $$\hat{v}(x; w^{*})$$

- [[Eligibility Traces]]
- [[Actor-Critic Algorithm]]
- [[SARSA lambda Algorithm]]

## Explanation

>[!important] *Remarks*:  
>- Traces provide *exponentially decaying memory* of past gradients; 
>	- larger $\lambda$ means *longer credit assignment*.  
>- Many implementations maintain *separate* $\lambda$ values or *reset rules* for actor and critic traces; 
>	- the version above resets both at episode start for clarity.  
>- With $\lambda = 0$ the algorithm reduces to the standard one‑step Actor–Critic.  




-----------
##  Recommended Notes and References



- [[lambda-Return and Compound Update]]
- [[Multi-Step Truncated lambda-Return Method]]
- [[Temporal Difference lambda Algorithm]]
- [[Policy Gradient Algorithm]]
- [[Markov Decision Process]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 331 - 334
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1148
