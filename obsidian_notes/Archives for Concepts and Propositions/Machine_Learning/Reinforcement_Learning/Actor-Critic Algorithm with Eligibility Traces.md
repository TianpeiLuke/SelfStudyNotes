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

### Actor-Critic Algorithm with Eligibility Traces

>[!important] Definition  
>The **Actor–Critic ($\lambda$)** algorithm augments one‑step Actor–Critic with **eligibility traces** so that both actor and critic receive multi‑step credit assignment.  
>- Setting $\lambda = 0$ gives the original one‑step update; $$\lambda \to 1$$ approaches *Monte‑Carlo returns*.  
>
>- *Require*  
>	- *differentiable policy* $\pi(a\mid x;\theta)$  
>	- *differentiable value estimator* $\hat v(x;w)$ 
>	- *discount* $\gamma\in(0,1)$ 
>	- *trace‑decay* $\lambda\in[0,1]$  
>	- learning‑rates $\alpha_\theta,\;\alpha_w$  
>
>- *Initialise*  
>	- parameters $\theta^{(0)},\, w^{(0)}$  
>	- traces $$\mathbf e^{\theta} \gets \mathbf 0,\; \mathbf e^{w} \gets \mathbf 0$$  
>
>- **For each episode**  
>	- Sample start state $X_0$; 
>	- Set $$t \gets 0.$$  
>	- **Loop until terminal** state:  
>		- **Action**: $$A_t \sim \pi(\cdot \mid X_t;\theta)$$  
>		- **Environment step**
>			- observe reward $R_t$ and next state $X_{t+1}$ 
>		- **TD error**  $$\delta_t \;=\; R_t + \gamma \hat v(X_{t+1};w)\;-\;\hat v(X_t;w) ,$$  
>			- using $\hat v(X_{t+1};w)=0$ if $X_{t+1}$ is *terminal*.  
>		- **Update traces**  
>			- $$\mathbf e^{w} \;\gets\; \gamma\lambda\,\mathbf e^{w}      + \nabla_{w}\hat v(X_t;w)$$  
>			- $$\mathbf e^{\theta} \;\gets\; \gamma\lambda\,\mathbf e^{\theta} + \nabla_{\theta}\log\pi(A_t\mid X_t;\theta)$$  
>		- **Critic update**  $$w \;\gets\; w + \alpha_w\,\delta_t\,\mathbf e^{w}$$  
>		- **Actor update**  $$\theta \;\gets\; \theta + \alpha_\theta\,\delta_t\,\mathbf e^{\theta}$$  
>		- Increment $$t \gets t+1.$$  
>
>- *Return* after convergence  
>	- **Actor**: policy $$\pi(\,\cdot\mid x;\,\theta^{*})$$  
>	- **Critic**: value function $$\hat v(x;\,w^{*})$$  

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
