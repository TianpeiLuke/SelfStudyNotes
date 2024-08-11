---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - multi_step_sarsa
  - monte_carlo
  - on_policy_learning
topics:
  - reinforcement_learning
name: Multi-Step SARSA Algorithm On-Policy
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: Multi-Step SARSA Algorithm On-Policy

>[!important] Definition
>The **$n$-step SARSA** is an extension of *SARSA*, which *switch states* for actions (state–action pairs) and then use an *$\epsilon$-greedy policy*.
>
>

- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[SARSA lambda Algorithm]]

### Multi-Step SARSA On-Policy Update

>[!info]
>We can redefine the **$n$-step returns** as update target in terms of *estimated action values* for $n\ge 1$, $t\in [0, T-n]$
>$$
>\begin{align*}
>G_{t:t+n} &:= R_{t+1} + \gamma R_{t+2} \,{+}\ldots{+}\, \gamma^{n-1}R_{t+n} + \gamma^{n}\,Q_{t+n-1}\left(X_{t+n}, A_{t+n}\right) 
\end{align*}
>$$
>and for $t > T-n$ $G_{t:t+n} = G_{t}.$

^af4858


>[!info]
>The natural update is then 
>$$
>\begin{align*}
>Q_{t+n}(X_{t}, A_{t}) &:= Q_{t+n-1}(X_{t}, A_{t}) + \alpha \left(G_{t: t+n} - Q_{t+n-1}(X_{t}, A_{t})\right) \\
>&= Q_{t+n-1}(X_{t}, A_{t}) + \alpha \left[ \sum_{s=1}^{n}\gamma^{s-1}\,R_{t+s}  + \gamma^{n}\,Q_{t+n-1}\left(X_{t+n}, A_{t+n}\right)  - Q_{t+n-1}(X_{t}, A_{t})\right] 
\end{align*}
>$$
>and the rest action-value pair $(x,a) \neq (X_{t}, A_{t})$,  $$Q_{t+n}(x, a) = Q_{t+n-1}(x, a).$$

^879238


### Multi-Step SARSA On-Policy Prediction

>[!important] Definition
>The **on-policy $n$-step SARSA** algorithm for estimating $Q \approx q_{*}$ or $q_{\pi}$ is described as below:
>- *Require*: an initialized $Q(x, a)$ for all $x\in \mathcal{X}$ and $a\in \mathcal{A}$
>- *Require*: an **$\epsilon$-greedy policy** $\pi$ with respect to $Q$, or a *fixed strategy* $\pi$
>- *Require*: step size $\alpha \in (0,1]$
>- *Require*: exploration parameter $\epsilon \in (0,1)$, discount $\gamma >0$
>- *Require*: history length $n$
>- *Require*: a buffer for **most recent $n$ history** $(X_{t}, A_{t}, R_{t})$
>- For *episode* $k= 1 \,{,}\ldots{,}\,$
>	- *Initialize* and *store* $X_{0} \neq \text{terminal}$
>	- Select and *store* $A_{0} \sim \pi(\cdot\,|\, X_{0})$
>	- For $t=0,\,1 \,{,}\ldots{,}\,T + n -1$
>		- If $t < T$:
>			- Take action $A_{t}$
>			- Observe and *store* **next reward** $R_{t+1}$ and **next state** $X_{t+1}$
>			- If $X_{t+1}$ is **terminal**
>				- $T = t+1$, i.e. break loop
>			- Else
>				- Select and *store* action $$A_{t+1} \sim \pi(\cdot\,|\,X_{t+1})$$
>		- Update the **stopping time** $\tau$ when the *estimate is updated* $$\tau = t - n + 1.$$
>		- If $\tau \ge 0$
>			- Update the **$n$-return** with *cumulative discounted rewards* $$G_{\tau} = \sum_{i = \tau+1}^{\min\left\{ \tau + n\,,\,T  \right\}}\gamma^{i - \tau + 1}\,R_{i}$$
>			- If $\tau + n < T$
>				- Update the **$n$-return** with additional estimate from $Q$ $$G_{\tau} \leftarrow G_{\tau} + \gamma^n\,Q_{\tau}(X_{\tau + n}, A_{\tau + n})$$
>			- Update **estimate of action-value** $Q$ as $$Q_{\tau+1}(X_{\tau}, A_{\tau}) = Q_{\tau}(X_{\tau}, A_{\tau}) + \alpha \left[ G_{\tau} - Q_{\tau}(X_{\tau}, A_{\tau}) \right]$$ 
>			- If $\pi$ is learned
>				- Update $\pi$ so that $\pi(\cdot\,|\,X_{\tau})$ is **$\epsilon$-greedy** with respect to $Q_{\tau}$

- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]
- [[Multi-Step SARSA Algorithm Off-Policy]]



## Explanation


>[!info]
>The backup diagrams for *$n$-step Sarsa* (shown in Figure 7.3), like those of *$n$-step TD* (Figure 7.1), are strings of **alternating states and actions**, except that the Sarsa ones all *start and end* with an *action* rather a state.

![[multi_step_temporal_difference.png]]

- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]

## Compare with SARSA(0)

![[SARSA Algorithm and On-Policy Temporal Difference Control#^cf105f]]

>[!important]
>We can see the update between $1$-step and $n$-step SARSA
>$$
>\begin{align*}
> Q_{t+1}(X_{t}, A_{t}) &:= Q_{t}(X_{t}, A_{t}) + \alpha \left(G_{t: t+1} - Q_{t}(X_{t}, A_{t})\right) &(\text{ $1$-step SARSA})\\[5pt]
> &= Q_{t}(X_{t}, A_{t}) + \alpha\left[ R_{t+1} + \gamma Q_{t}(X_{t+1}, A_{t+1})  - Q_{t}(X_{t}, A_{t}) \right] \\[5pt]
> Q_{t+n}(X_{t}, A_{t}) &:= Q_{t+n-1}(X_{t}, A_{t}) + \alpha \left(G_{t: t+n} - Q_{t+n-1}(X_{t}, A_{t})\right) &(\text{ $n$-step SARSA})\\[5pt]
> &= Q_{t+n-1}(X_{t}, A_{t}) + \alpha \left[ \sum_{s=1}^{n}\gamma^{s-1}\,R_{t+s}  + \gamma^{n}\,Q_{t+n-1}\left(X_{t+n}, A_{t+n}\right)  - Q_{t+n-1}(X_{t}, A_{t})\right] 
>\end{align*}
>$$





-----------
##  Recommended Notes and References

- [[Multi-Step SARSA Algorithm Off-Policy]]
- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]

- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Temporal Difference Learning]]


- [[On-Policy and Off-Policy Reinforcement Learning]]
- [[Prediction and Control Problems in Reinforcement Learning]]
- [[Value Function and Bellman Equation for MDP]]
- [[Monte Carlo and Applications]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 145 - 148