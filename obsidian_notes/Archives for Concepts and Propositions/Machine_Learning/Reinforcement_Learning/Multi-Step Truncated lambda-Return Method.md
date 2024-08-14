---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - multi_step_truncated_lambda_return_method
  - truncated_lambda_return
topics:
  - reinforcement_learning/algorithm
name: Multi-Step Truncated lambda-Return Method
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: Multi-Step Truncated $\lambda$-Return Method

![[lambda-Return and Compound Update#^63443d]]

![[lambda-Return and Compound Update#^e0bff0]]


>[!important] Definition
>Define the **truncated $\lambda$-return** for time $t$, given data up to a *finite horizon* $h$
>$$
>\begin{align*}
>G_{t : h}^{\lambda} &:= \left(1- \lambda\right)\,\sum_{n=1}^{h- t -1}\lambda^{n-1}\,G_{t:t+n} + \lambda^{h-t-1}G_{t:h}, \quad 0 \le t < h \le T. 
>\end{align*}
>$$
>
>
>Whereas in the -return there is a *residual weight* given to the conventional return $G_{t}$, here it is given to the *longest available $n$-step return*, $G_{t:h}$.

- [[lambda-Return and Compound Update]]

![[truncated_td_lambda.png]]

### $n$-step-Truncated $\lambda$-Return Update

![[Semi-Gradient Temporal Difference#^5680d7]]


>[!important] Definition
>In **truncated temporal difference (TTD($\lambda$) )**, the target is the **truncated $\lambda$-return**.
>
>The **semi-gradient TTD($\lambda$) update** is 
>$$\begin{align*}
>w_{t+n} &= w_{t+n-1} + \alpha\,\left[ G_{t:t+n}^{\lambda}  - \hat{v}(X_{t}, w_{t+n-1}) \right]\;  \nabla_{w}\hat{v}(X_{t}, w_{t+n-1}), \quad 0 \le t < T.
>\end{align*}
>$$

- [[Semi-Gradient Temporal Difference]]

![[Equivalence of Forward View and Backward View for TD(lambda)#^afdf2a]]

>[!quote]
>Much as in *$n$-step TD methods*, *no updates* are made on the **first $n+1$ time steps** of each episode, and $n+1$ *additional updates* are made upon **termination**. Efficient implementation relies on the fact that the $k$-step $\lambda$-return can be written exactly as
>$$
> G_{t:t+n}^{\lambda} := \hat{v}(X_{t}, w_{t-1}) + \sum_{k=t}^{t+n-1}\left(\lambda\,\gamma\right)^{k-t}\,\delta_{k}'
>$$
>where 
>$$
>\delta_{t}' = R_{t+1} + \gamma\,\hat{v}\left(X_{t+1}, w_{t}\right) - \hat{v}(X_{t}, w_{t-1})
>$$

- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]

![[Equivalence of Forward View and Backward View for TD(lambda)#^b3c492]]

- [[Equivalence of Forward View and Backward View for TD(lambda)]]


### Semi-Gradient Truncated TD($\lambda$)  Algorithm

>[!important] Definition
>The **semi-gradient Truncated TD($\lambda$) or TTD($\lambda$)** algorithm is described as
>- *Require*: **target policy** $\pi$
>- *Require*: approximate value function $\hat{v}(\cdot; w): \mathcal{X} \to \mathbb{R}$ parameterized by $w\in \mathbb{R}^d$ and is *differentiable* in $w$. Set $\hat{v}(\text{terminal}; w) = 0$ for all $w$
>- *Require*: step size $\alpha \in (0,1]$, and  discount $\gamma \in (0,1)$
>- *Require*: decay $\gamma \in [0,1]$
>- *Require*: **truncation length** $n$
>- *Require*: a buffer for **most recent $n$ history** $(X_{t},R_{t}, \delta_{t}',  w_{t})$
>- *Initialize* and *store* $w_{s} = w\in \mathbb{R}^d$ for all $s\le n-1$ in buffer
>- For *episode* $k= 1 \,{,}\ldots{,}\,$
>	- *Initialize* and *store* $X_{0} \neq \text{terminal}$
>	- Initialize $z_{-1} = 0$
>	- For $t=0,\,1 \,{,}\ldots{,}\,T + n -1$
>		- If $t < T$:
>			- Take action $$A_{t} \sim \pi(\cdot\,|\,X_{t})$$
>			- Observe and *store* **next reward** $R_{t+1}$ and **next state** $X_{t+1}$
>			- Compute the **eligibility trace vector** $$z_{t} = \gamma\,\lambda\,z_{t-1} + \nabla \hat{v}(X_{t}, w_{t})$$
>			- Compute and *store* the **TD error** $$\delta_{t} = R_{t + 1} + \gamma\,\hat{v}\left(X_{t+1}, w_{t}\right) - \hat{v}(X_{t}, w_{t-1})$$
>				- Note that $w_{s} = w$ for first $n-1$ iterations $s\le n- 1$
>			- If $X_{t+1}$ is **terminal**
>				- $T = t+1$, i.e. break loop
>		- Update the **time** $\tau$ when the *weight is updated* $$\tau = t - n + 1.$$
>		- If $\tau \ge 0$
>			- Update and **store** **parameter** $w_{\tau+n} :=w_{t+1}$ as $$w_{\tau + n} = w_{\tau +n -1} + \alpha\,\delta_{\tau + n -1}\,z_{\tau + n -1}$$ 



- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]
- [[Semi-Gradient Temporal Difference]]
- [[Temporal Difference lambda Algorithm]]


## Explanation

>[!quote]
>In the **continuing case**, the $\lambda$-return is technically never known, as it depends on $n$-step returns for arbitrarily large $n$, and thus on *rewards arbitrarily far* in the *future*. However, the dependence becomes weaker for longer-delayed rewards, falling by for each step of *delay*. A natural approximation, then, would be to **truncate the sequence** after some number of steps. Our existing notion of n-step returns provides a natural way to do this in which the missing rewards are replaced with estimated values.
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 295





-----------
##  Recommended Notes and References



- [[lambda-Return and Compound Update]]
- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]

- [[Temporal Difference Learning]]
- [[Eligibility Traces]]
- [[Returns and Goals of Reinforcement Learning]]






- [[Prediction and Control Problems in Reinforcement Learning]]
- [[Value Function and Bellman Equation for MDP]]
- [[Monte Carlo and Applications]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 292 - 293