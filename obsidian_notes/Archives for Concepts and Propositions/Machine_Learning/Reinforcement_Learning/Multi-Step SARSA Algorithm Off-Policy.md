---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
  - multi_step_sarasa_algorithm
keywords:
  - multi_step_sarsa
  - off_policy_learning
  - importance_sampling
topics:
  - reinforcement_learning/algorithm
name: Multi-Step SARSA Algorithm Off-Policy
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: Multi-Step SARSA Algorithm Off-Policy

![[Multi-Step SARSA Algorithm On-Policy#^af4858]]

![[Multi-Step SARSA Algorithm On-Policy#^879238]]

### Multi-Step SARSA Off-Policy Update

>[!important]
>Given the target policy $\pi$ and behavior policy $b$, we need account for their difference via **importance sampling**.
>
>In particular, the **off-policy update** for action-value can be *weighted* by additional *multiplicative factor* $\rho_{t: t+n-1}$
>$$
>\begin{align*}
>Q_{t+n}(X_{t}, A_{t}) &:= Q_{t+n-1}(X_{t}, A_{t}) + \alpha\;\rho_{t+1: t+n} \left(G_{t: t+n} - Q_{t+n-1}(X_{t}, A_{t})\right) \\
>&= Q_{t+n-1}(X_{t}, A_{t}) + \alpha\;\rho_{t+1 : t+n}  \left[ \sum_{s=1}^{n}\gamma^{s-1}\,R_{t+s}  + \gamma^{n}\,Q_{t+n-1}\left(X_{t+n}, A_{t+n}\right)  - Q_{t+n-1}(X_{t}, A_{t})\right] 
\end{align*}
>$$
>where the *multiplicative factor* $\rho_{t: t+n-1}$ is called the **importance sampling ratio** which is the **probability ratio under two policies** of taking the $n$-actions from $A_{t}$ to $A_{t+n}$ 
>$$
>\rho_{t : h} = \prod_{j=t}^{\min\{ h, T-1 \}}\frac{\pi(A_{j}\,|\,X_{j})}{b(A_{j}\,|\,X_{j})}
>$$

- [[Importance Sampling]]

>[!quote]
>Note that the importance sampling ratio here starts and ends **one step later** than for n-step TD (7.9). This is because here we are *updating a state–action pair*. We do not have to care how likely we were to *select the action*; now that we have selected it we want to learn fully from what happens, with importance sampling only for *subsequent actions*.
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 171

### Multi-Step SARSA Off-Policy Prediction

>[!important] Definition
>The **off-policy $n$-step SARSA** algorithm for estimating $Q \approx q_{*}$ or $q_{\pi}$ is described as below:
>- *Require*: an explorative **behavior policy** $b$ such that $b(a|x) >0$ for all $x\in \mathcal{X}$ and $a\in \mathcal{A}$
>- *Require*: an initialized $Q(x, a)$ for all $x\in \mathcal{X}$ and $a\in \mathcal{A}$
>- *Require*: an **greedy target policy** $\pi$ with respect to $Q$, or a *fixed strategy* $\pi$
>- *Require*: step size $\alpha \in (0,1]$
>- *Require*: exploration parameter $\epsilon \in (0,1)$, discount $\gamma >0$
>- *Require*: history length $n$
>- *Require*: a buffer for **most recent $n$ history** $(X_{t}, A_{t}, R_{t})$
>- For *episode* $k= 1 \,{,}\ldots{,}\,$
>	- *Initialize* and *store* $X_{0} \neq \text{terminal}$
>	- Select and *store* $A_{0} \sim b(\cdot\,|\, X_{0})$
>	- For $t=0,\,1 \,{,}\ldots{,}\,T + n -1$
>		- If $t < T$:
>			- Take action $A_{t}$
>			- Observe and *store* **next reward** $R_{t+1}$ and **next state** $X_{t+1}$
>			- If $X_{t+1}$ is **terminal**
>				- $T = t+1$, i.e. break loop
>			- Else
>				- Select and *store* action $$A_{t+1} \sim b(\cdot\,|\,X_{t+1})$$
>		- Update the **stopping time** $\tau$ when the *estimate is updated* $$\tau = t - n + 1.$$
>		- If $\tau \ge 0$
>			- Compute **importance sampling ratio (importance weight)** $$\rho_{\tau} =  \prod_{j=\tau + 1}^{\min\{ \tau + n -1\,,\, T-1 \}}\frac{\pi(A_{j}\,|\,X_{j})}{b(A_{j}\,|\,X_{j})}$$
>			- Update the **$n$-return** with *cumulative discounted rewards* $$G_{\tau} = \sum_{i = \tau+1}^{\min\left\{ \tau + n\,,\,T  \right\}}\gamma^{i - \tau + 1}\,R_{i}$$
>			- If $\tau + n < T$
>				- Update the **$n$-return** with additional estimate from $Q$ $$G_{\tau} \leftarrow G_{\tau} + \gamma^n\,Q_{\tau}(X_{\tau + n}, A_{\tau + n})$$
>			- Update **estimate of action-value** $Q$ as $$Q_{\tau+1}(X_{\tau}, A_{\tau}) = Q_{\tau}(X_{\tau}, A_{\tau}) + \alpha\,\rho_{\tau}\; \left[ G_{\tau} - Q_{\tau}(X_{\tau}, A_{\tau}) \right]$$ 
>			- If $\pi$ is learned
>				- Update $\pi$ so that $\pi(\cdot\,|\,X_{\tau})$ is **greedy** with respect to $Q_{\tau}$

### Mermaid Diagram




## Explanation


>[!info]
>Recall that in **off-policy Monte Carlo prediction**, there are two policies
>- **target policy** $\pi$, which corresponds to the *estimated value function* $V_{\pi}$ or $Q_{\pi}$
>- **behavior policy** $b$, which controls the iteration of the algorithm 
>  
>Often, $\pi$ is the **greedy policy** for the current *action-value function estimate*, and $b$ is a more **exploratory policy**, perhaps *$\epsilon$-greedy*.

- [[Off-Policy Monte Carlo Prediction with Importance Sampling]]



-----------
##  Recommended Notes and References

- [[Multi-Step SARSA Algorithm On-Policy]]
- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]
- [[Temporal Difference Learning]]

- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Importance Sampling]]
- [[Sequential Importance Sampling]]


- [[On-Policy and Off-Policy Reinforcement Learning]]
- [[Prediction and Control Problems in Reinforcement Learning]]
- [[Value Function and Bellman Equation for MDP]]
- [[Monte Carlo and Applications]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 148 - 150