---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - multi_step_temporal_difference_learning
  - temporal_difference_learning
topics:
  - reinforcement_learning/algorithm
name: Multi-Step Temporal Difference Learning
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: Multi-Step Temporal Difference Learning

### n-Step Return

>[!info]
>The **returns** can be estimated based on a history of rewards $(R_{s})_{s=t+1}^{T}$ using **Monte Carlo Method**
>$$
>\begin{align*}
>G_{t} &:= R_{t+1} + \gamma R_{t+2} \,{+}\ldots{+}\, \gamma^{T-t - 1}R_{T}  
\end{align*}
>$$

^de8997

- [[Monte Carlo and Applications]]

>[!info]
>On the other hand, the **$1$-step temporal difference update** on return $G_{t : t+1}$ is based on *estimated state-value function* $V_{t}$ on next state $X_{t+1}$
>$$
>G_{t: t+1} = R_{t+1} + \gamma\,V_{t}(X_{t+1})
>$$
>where
>$$
>\gamma V_{t}(X_{t+1}) \approx \gamma R_{t+2} \,{+}\ldots{+}\, \gamma^{T-t - 1}R_{T}  
>$$
>
>We can extends the above formula to *$2$-step*
>$$
>G_{t: t+2} = R_{t+1} + \gamma\,R_{t+2} + \gamma^2\,V_{t+1}(X_{t+2})
>$$
>where
>$$
>\gamma^2 V_{t+1}(X_{t+2}) \approx \gamma^2 R_{t+3} \,{+}\ldots{+}\, \gamma^{T-t - 1}R_{T}  
>$$


>[!important] Definition
>The **$n$-step return** is defined using a *sequence of observed state-reward process* $(X_{t}, R_{t+1} \,{,}\ldots{,}\,)$ of length $n$ and an *estimated value function*.
>
>In particular, **the $n$-step return** is defined as 
>$$
>\begin{align*}
> G_{t: t+n} := R_{t+1} + \gamma\,R_{t+2} \,{+}\ldots{+}\, \gamma^{n-1}\,R_{t+n} + \gamma^{n}\,V_{t+n-1}\left(X_{t+n}\right)
>\end{align*}
>$$
>for all $n,t$ such that $n \ge 1$ and $0 \le t< T-n.$
>
>For $t+n > T$, $G_{t: t+n} = G_{t}.$

^b19bc5

### Multi-Step Temporal Learning Update

>[!important] Definition
>A $n$-step return for $n > 1$ involve *future rewards* and *states* from $t+1$ to $t+n$, which is only available after $t+n$.
>
>A natural *state-value learning* algorithm using $n$-return is
>$$
>V_{t+n}(X_{t}) = V_{t+n-1}(X_{t}) + \alpha \left[ G_{t: t+n} - V_{t+n-1}(X_{t}) \right], \quad 0 \le t < T, 
>$$
>while 
>$$
>V_{t+n}(x) = V_{t+n-1}(x), \quad \forall x\neq X_{t}.
>$$
>
>The learning algorithm is called the **$n$-step temporal difference learning.**
>- Note that *no change* at all is made for the *first $n-1$ steps* of each episode. 
>- *Additional $n-1$ steps* are made at the end of each episode.
>- The **TD error** is $$\delta_{t} := G_{t: t+n} - V_{t+n-1}(X_{t}) .$$

### Multi-Step Temporal Learning for Prediction

>[!important] Definition
>The **on-policy $n$-step temporal learning** algorithm for estimating $V \approx v_{*}$ or $v_{\pi}$ is described as below:
>- *Require*: **target policy** $\pi$
>- *Require*: step size $\alpha \in (0,1]$
>- *Require*: discount $\gamma >0$
>- *Require*: history length $n$
>- *Require*: a buffer for **most recent $n$ history** $(X_{t}, R_{t})$
>- Initialize $V_{n-1}(x)$ for all $x\in \mathcal{X}$
>- For *episode* $k= 1 \,{,}\ldots{,}\,$
>	- *Initialize* and *store* $X_{0} \neq \text{terminal}$
>	- For $t=0,\,1 \,{,}\ldots{,}\,T + n -1$
>		- If $t < T$:
>			- Take action $$A_{t} \sim \pi(\cdot\,|\,X_{t})$$
>			- Observe and *store* **next reward** $R_{t+1}$ and **next state** $X_{t+1}$
>			- If $X_{t+1}$ is **terminal**
>				- $T = t+1$, i.e. break loop
>		- Update the **stopping time** $\tau$ when the *estimate is updated* $$\tau = t - n + 1.$$
>		- If $\tau \ge 0$
>			- Update the **$n$-return** with *cumulative discounted rewards* $$G_{\tau: \tau+n} = \sum_{i = \tau+1}^{\min\left\{ \tau + n\,,\,T  \right\}}\gamma^{i - \tau - 1}\,R_{i}$$
>			- If $\tau + n < T$
>				- Update the **$n$-return** with additional estimate from $Q$ $$G_{\tau: \tau+n} \leftarrow G_{\tau: \tau+n} + \gamma^n\,V_{\tau+n-1}(X_{\tau + n})$$
>			- Update **estimate of state-value** $V$ as $$V_{\tau+n}(X_{\tau}) = V_{\tau+n-1}(X_{\tau}) + \alpha \left[ G_{\tau: \tau+n} - V_{\tau+n-1}(X_{\tau}) \right]$$ 



## Explanation

>[!info]
>The **n-step return** is considered as an approximation of full return, *truncated after $n$ step*, and *corrected* for the remaining term by value function $V_{t+n-1}(X_{t+n}).$



## Between Temporal Difference and Monte Carlo

>[!quote]
>Consider estimating $v_{\pi}$ from *sample episodes* generated using $\pi$. **Monte Carlo methods** perform an update for each state based on the *entire sequence* of observed rewards from that state *until the end of the episode*. The update of **one-step TD methods**, on the other hand, is based on just the *one next reward*, *bootstrapping* from the value of the state one step later as a *proxy* for the remaining rewards. One kind of **intermediate method**, then, would perform an update based on an *intermediate number of rewards*: more than one, but less than all of them until termination.
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 142

![[multi-step_td.png]]

- [[Temporal Difference Learning]]
- [[Monte Carlo Prediction for Value Estimation]]

## Error Reduction Property of n-Returns


- [[Reinforcement Learning An Introduction by Sutton]] pp 144




-----------
##  Recommended Notes and References


- [[Multi-Step SARSA Algorithm On-Policy]]
- [[Multi-Step SARSA Algorithm Off-Policy]]
- [[Eligibility Traces]]

- [[Temporal Difference Learning]]




- [[Prediction and Control Problems in Reinforcement Learning]]
- [[Value Function and Bellman Equation for MDP]]
- [[Monte Carlo and Applications]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 142 - 145
- [[Distributional Reinforcement Learning by Bellemare]] pp 41, 109