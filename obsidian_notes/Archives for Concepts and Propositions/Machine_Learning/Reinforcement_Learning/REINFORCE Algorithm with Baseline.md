---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
keywords:
  - reinforce_algorithm
  - policy_gradient_method
  - reinforce_algorithm_baseline
topics:
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
name: REINFORCE Algorithm with Baseline
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: REINFORCE Algorithm with Baseline

![[REINFORCE Algorithm for Monte Carlo Policy Gradient#^25c7fb]]

![[Policy Gradient Theorem#^672c0f]]


>[!info]
>The policy gradient theorem can be generalized to include arbitrary **baseline** $b(x)$
>$$
> \begin{align*}
>  \nabla_{\theta}\mathcal{R}(\theta) &\propto \sum_{x}\mu_{\pi(\theta)}(x)\;\sum_{a}\,\nabla_{\theta}\,\pi(a\,|\,x, \theta)\;\left(q_{\pi}(x, a) - b(x)\right) 
> \end{align*}
>$$  
>The equation holds since $$b(x)\sum_{a}\nabla_{\theta}\,\pi(a\,|\,x, \theta) = 0.$$ 

>[!important] Definition
>Let  $\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}\,,\, p_{t}(\cdot|x, a)\,,\, r_{t}(x, a)\}$ be a *Markov decision process* and $v_{\pi}(x)$ is the *state-value function* under policy $\pi_{\theta}$, which is parameterized by $\theta$.
>
>- Define the **loss function** as $$\mathcal{R}(\theta) := v(x_{0}; \pi_{\theta})$$ which is the the *true value* under $\pi_{\theta}$.
>- Define the **baseline function** of state $b(x)$ that satisfies that $$\mathbb{E}_{X\sim\mu_{\pi(\theta)}}\left[  b(X)\sum_{a}\nabla_{\theta}\,\pi(a\,|\,X, \theta) \right] = 0,\;\text{ or }\; b(x)\sum_{a}\nabla_{\theta}\,\pi(a\,|\,x, \theta) = 0,\quad \forall x\in \mathcal{X}$$
>
>The **REINFORCE-with-baseline** update is given by 
>$$
> \begin{align}
> \theta_{t+1} &\leftarrow  \theta_{t} + \alpha \;(G_{t}-b(X_t))\;\nabla_{\theta}\log \pi(A_{t}\,|\,X_{t},\, \theta), 
> \end{align}
>$$  
>where 
>- $G_{t}$ is the *sample returns* $$G_{t} := \sum_{\tau > t}\gamma^{\tau}R_{\tau}$$ under the policy $\pi$ following the sequence $$(X_{t}, A_{t}, R_{t+1}, X_{t+1}, A_{t+1}, \ldots)$$ in an episode.  
>- In general, the baseline leaves the *expected value* of the update *unchanged*, but the **variance** will be *reduced significantly*. 
>- A natural choice of *baseline function* is the **approximate value function** $$b(X_{t}) := \hat{v}(X_t, w_t),$$ whose function parameter is updated using Monte Carlo prediction. That is,
>$$
> \begin{align}
> \theta_{t+1} &\leftarrow  \theta_{t} + \alpha \;(G_{t}-\hat{v}(X_t, w_t))\;\nabla_{\theta}\log \pi(A_{t}\,|\,X_{t},\, \theta), 
> \end{align}
>$$  

^d725e6

- [[Policy Gradient Theorem]]
- [[Policy Gradient Algorithm]]
- [[REINFORCE Algorithm for Monte Carlo Policy Gradient]]
- [[Tabular Representation and Function Approximation RL]]
- [[Episodic Semi-Gradient SARSA]]
- [[Monte Carlo Prediction for Value Estimation]]

### Algorithm

>[!important] Definition
>The **REINFORCE with Baseline algorithm** for *episodic task*  is described as follows:
>- *Require*: parameterized policy function $\pi(a|x, \theta)$
>- *Require*: parameterized value function estimate $\hat{v}(x; w)$
>- *Require*: step size $\alpha_{\theta} >0$ and $\alpha_{w} >0$
>- *Require*: reward discount factor $\gamma\in (0,1)$
>- Initialize $\theta^{(0)}$ and $w^{(0)}$
>- For **episode** $k=1\,{,}\ldots{,}\,$
>	- Generate an **entire episode** following **policy** $\pi(\cdot|\cdot, \theta)$ i.e. $$\left(X_{0}, A_{0}, R_{1}, X_{1}\,{,}\ldots{,}\,X_{T-1}, A_{T-1}, R_{T}\right)$$
>	- For $t=0\,{,}\ldots{,}\,T-1$
>		- Accumulate **expected sample returns** via **Monte Carlo estimator** $$G_{t} = \sum_{s=t+1}^{T}\gamma^{s-t-1}\,R_{s}$$
>		- Compute the corrected return by subtracting with **baseline** $$\delta_{t} = G_{t}  - \hat{v}(X_{t}; w)$$
>		- Update the **value function parameter** via gradient ascent 
>		  $$
>		 w \leftarrow w + \alpha_{w}\;\delta_{t}\;\nabla_{w}\hat{v}(X_{t}, w) 
>		 $$
>		- Update the **policy parameter** via *Monte Carlo estimator* 
>		  $$\theta \leftarrow \theta + \alpha_{\theta}\,\gamma^{t}\,\delta_{t}\,\nabla \log \pi(A_{t}\,|\,X_{t};\; \theta)$$


## Explanation

>[!info]
>Note that although the **REINFORCE-with-baseline** method learns 
>- both a **policy** $$\pi(a|x,\; \theta)$$ 
>- and a **state-value function**, 
>
>we do not consider it to be an **actor–critic method** because its *state-value function* is used only as a **baseline**, not as a **critic**. 
>- That is, it is **not** used for **bootstrapping** that updates the *value estimate* for a state from the estimated values of subsequent states. 
>- This is a *useful distinction*, for only through **bootstrapping** do we introduce **bias** and an **asymptotic dependence** on the quality of the function approximation. 

- [[Actor-Critic Algorithm]]
- [[Advantage Actor Critic or A2C and A3C Algorithm]]


-----------
##  Recommended Notes and References



- [[Monte Carlo and Applications]]
- [[Importance Sampling]]




- [[Reinforcement Learning An Introduction by Sutton]] pp 330
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 265, 1137, 1148
