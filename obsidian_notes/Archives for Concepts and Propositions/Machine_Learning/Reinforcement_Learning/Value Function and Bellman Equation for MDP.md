---
tags:
  - concept
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
keywords:
  - value_function_reinforcement_learning
  - bellman_equation
  - dynamic_programming
topics:
  - reinforcement_learning
name: Value Function and Bellman Equation
date of note: 2024-07-13
---

## Concept Definition

>[!important]
>**Name**: Value Function and Bellman Equation

![[Markov Decision Process#^a1e9de]]

![[Markov Decision Process#^1d9419]]

![[Markov Decision Process#^67062c]]

>[!important] Definition
>Given 
>- a *Markov decision process* $$\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}\,,\, p_{t}(\cdot|x, a)\,,\, r_{t}(x, a)\},$$
>- and a *Markov policy* $\pi = (\delta_{1}, \delta_{2} \,{,}\ldots{,}\,)$ where each $\delta_{t}$ is *randomized Markov decision rule* $$\delta_{t}: x \mapsto q_{\delta_{t}(x)}(\cdot) \in \mathscr{P}_{\mathcal{A}},$$
>
>the **value function** or **state-value function** *for policy $\pi$*, denoted $v_{\pi}(x)$, is the *expected return* when starting in $x$, and following $\pi$ thereafter. 
>
>Specifically, 
>$$
>v_{\pi}(x) := \mathbb{E}^{ \pi }\left[  G_{t} \,|\,X_{t} = x \right] = \mathbb{E}^{ \pi }\left[ \sum_{k=0}^{\infty}\gamma^{k}\,R_{t+k+1} \,|\,X_{t} = x \right]
>$$
>where 
>- the *reward* at $t$ is denoted as $$R_{t} := r_{t}(X_{t}, A_{t}), \quad A_{t} \sim q_{\delta_{t}(x)}$$ 
>- $\gamma_{t} \in [0,1]$ is the **discount factor**
>- the *discounted return* at $t$ is computed as $$G_{t} = \sum_{k=0}^{\infty}\gamma^{k}\,R_{t+k+1} = R_{t+1} + \gamma\,R_{t+2} \,{+}\ldots\,$$
>- and the *expectation with respect to policy* $\pi$ and the corresponding joint probability distribution is  $$\mathcal{P}^{\pi}(x_{1}, a_{1}, x_{2}, a_{2} \,{,}\ldots{,}\,x_{T}) = \mathcal{P}_{1}(x_{1})\,q_{\delta_{t}(x_{1})}(a_{1})\,p_{1}(x_{2}|x_{1}\,,\,a_{1}) \,{}\ldots{}\,q_{\delta_{T-1}(x_{T-1})}(a_{T-1})\,p_{T-1}(x_{T}|x_{T-1}\,,\,a_{T-1})$$	

^e3c917

- [[Markov Decision Process]]
- [[Returns and Goals of Reinforcement Learning]]

>[!important] Defintion
>Given 
>- a *Markov decision process* $$\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}\,,\, p_{t}(\cdot|x, a)\,,\, r_{t}(x, a)\},$$
>- and a *Markov policy* $\pi = (\delta_{1}, \delta_{2} \,{,}\ldots{,}\,)$ where each $\delta_{t}$ is *randomized Markov decision rule* $$\delta_{t}: x \mapsto q_{\delta_{t}(x)}(\cdot) \in \mathscr{P}_{\mathcal{A}},$$
>
>the **action-value function** *for policy $\pi$*, denoted $q_{\pi}(x, a),$ is the *expected return* when starting from $x$, taking action $a$, and following $\pi$ thereafter. 
>
>Specifically, 
>$$
>q_{\pi}(x, a) := \mathbb{E}^{ \pi }\left[  G_{t} \,|\,X_{t} = x,\,A_{t} = a \right] = \mathbb{E}^{ \pi }\left[ \sum_{k=0}^{\infty}\gamma^{k}\,R_{t+k+1} \,|\,X_{t} = x, \,A_{t} = a \right].
>$$

^d40460

### Bellman Equation for State-Value Function 

>[!important] Definition
>Given 
>- a *Markov decision process* $$\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}\,,\, p_{t}(\cdot|x, a)\,,\, r_{t}(x, a)\},$$
>- and a *stationary Markov policy* $\pi = (\delta_{1}, \delta_{2} \,{,}\ldots{,}\,)$ where each $\delta_{t} = \delta$ is *randomized Markov decision rule* $$\delta: x \mapsto q_{\delta(x)}(\cdot) := \pi(\cdot | x) \in \mathscr{P}_{\mathcal{A}},$$
>- the *reward* at $t$ is denoted as $$R_{t+1} := r_{t}(X_{t}, A_{t}), \quad A_{t} \sim q_{\delta_{t}(x)}$$ 
>- $\gamma_{t} \in [0,1]$ is the *discount factor*,
>
>the *discounted return* can be decomposed in recursion $$G_{t} = R_{t+1} + \gamma\,G_{t+1}.$$
>
>Substituting the above recursion into the formula for *state-value function* $v_{\pi}$ under policy $\pi$
>$$
>\begin{align*}
> v_{\pi}(x) &= \mathbb{E}^{ \pi }\left[  G_{t} \,|\,X_{t} = x \right]\\
> &= \mathbb{E}^{ \pi }\left[  R_{t+1} + \gamma\,G_{t+1}\,|\,X_{t} = x \right] \\[5pt]
> &= \sum_{a \in \mathcal{A}}\pi(a | x) \sum_{u \in \mathcal{X}}\,p_{t}(u | x, a)\,\left[\,r_{t}(x, a) + \gamma\, \mathbb{E}^{\pi}\left[  G_{t+1} | X_{t+1} = u \right]\,  \right] \\[5pt]
> &= \sum_{a \in \mathcal{A}}\pi(a | x) \sum_{u \in \mathcal{X}}\,p_{t}(u | x, a)\,\left[r_{t}(x, a) + \gamma\,v_{\pi}(u)  \right]. 
>\end{align*}
>$$
>
>Assume that the MDP is *stationary*, i.e., the transition function $p(\cdot|x,a)$ and the reward function $r(x,a)$ are independent from time $t$,  then the equation
>$$
>v_{\pi}(x) = \sum_{a \in \mathcal{A}}\pi(a | x) \sum_{u \in \mathcal{X}}\,p(u | x, a)\,\left[r(x, a) + \gamma\,v_{\pi}(u)  \right], \quad \forall x \in \mathcal{X}
>$$
>is called the **Bellman equation** for **state-value function** $v_{\pi}$ *under policy* $\pi$.

^8c1d01

>[!important]
>We can represent the Bellman equation for $v_{\pi}$ using the *four argument transition function*
>$$
>v_{\pi}(x) = \sum_{a \in \mathcal{A}}\pi(a | x) \sum_{u \in \mathcal{X}}\sum_{r \in \mathcal{R}}\,p(u, r | x, a)\,\left[\,r + \gamma\,v_{\pi}(u)  \right], \quad \forall x \in \mathcal{X}
>$$

^7cf44e

- [[Reinforcement Learning An Introduction by Sutton]] pp 58

### Bellman Equation for Action-Value Function 

>[!important] Definition
>Given 
>- a *Markov decision process* $$\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}\,,\, p_{t}(\cdot|x, a)\,,\, r_{t}(x, a)\},$$
>- and a *stationary Markov policy* $\pi = (\delta_{1}, \delta_{2} \,{,}\ldots{,}\,)$ where each $\delta_{t} = \delta$ is *randomized Markov decision rule* $$\delta: x \mapsto q_{\delta(x)}(\cdot) := \pi(\cdot | x) \in \mathscr{P}_{\mathcal{A}},$$
>- the *reward* at $t$ is denoted as $$R_{t+1} := r_{t}(X_{t}, A_{t}), \quad A_{t} \sim q_{\delta_{t}(x)}$$ 
>- $\gamma_{t} \in [0,1]$ is the *discount factor*,
>
>the *discounted return* can be decomposed in recursion $$G_{t} = R_{t+1} + \gamma\,G_{t+1}.$$
>
>Substituting the above recursion into the formula for *action-value function* $q_{\pi}$ under policy $\pi$
>$$
>\begin{align*}
> q_{\pi}(x, a) &:= \mathbb{E}^{ \pi }\left[  G_{t} \,|\,X_{t} = x,\,A_{t} = a \right] \\
> &= \mathbb{E}^{ \pi }\left[  R_{t+1} + \gamma\,G_{t+1}\,|\,X_{t} = x,\,A_{t} = a \right] \\[5pt]
> &=  \sum_{a' \in \mathcal{A}}\pi(a' | u) \sum_{u \in \mathcal{X}}\,p_{t}(u | x, a)\,\left[\,r_{t}(x, a) + \gamma\, \mathbb{E}^{\pi}\left[  G_{t+1} | X_{t+1} = u,\, A_{t+1} = a' \right]\,  \right] \\[5pt]
> &= \sum_{u \in \mathcal{X}}\,p_{t}(u | x, a)\,\left[\,r_{t}(x, a) + \gamma\,\sum_{a' \in \mathcal{A}}\pi(a' | u)\, q_{\pi}(u, a')  \right]. 
>\end{align*}
>$$
>
>Assume that the MDP is *stationary*, i.e., the transition function $p(\cdot|x,a)$ and the reward function $r(x,a)$ are independent from time $t$,  then the equation
>$$
> q_{\pi}(x, a) =  \sum_{u \in \mathcal{X}}\,p(u | x, a)\,\left[\,r(x, a) + \gamma\,\sum_{a' \in \mathcal{A}}\pi(a' | u)\,q_{\pi}(u, a')  \right], \quad \forall x \in \mathcal{X}, \; a \in \mathcal{A}
>$$
>is called the **Bellman equation** for **action-value function** $q_{\pi}$ *under policy* $\pi$.

^f9fda7

>[!important]
>We can represent the Bellman equation for $q_{\pi}$ using the *four argument transition function*
>$$
>q_{\pi}(x, a) = \sum_{u \in \mathcal{X}}\sum_{r \in \mathcal{R}}\,p(u, r | x, a)\,\left[\,r + \gamma\,\sum_{a' \in \mathcal{A}}\pi(a' | u)\, q_{\pi}(u, a')  \right], \quad \forall x \in \mathcal{X}, \, a\in \mathcal{A}
>$$


## Explanation

>[!important]
>For **discrete-state** $\mathcal{X}$ MDP,  
>- the Bellman equation for $v_{\pi}$ is a **system of $|\mathcal{X}|$ equations.**
>- the Bellman equation for $q_{\pi}$ is a **system of $|\mathcal{X}| \times|\mathcal{A}|$ equations.**
>
>For continuous state $\mathcal{X}$, the Bellman equation describes the **functional relationship** between $v_{\pi}$ and a *linear functional* $I_{\pi, p, r}(v_{\pi})$


>[!important]
>The most common notation for **Bellman equation** is the *3-argument notation*
>$$
>\begin{align*}
>v_{\pi}(x) &= \sum_{a \in \mathcal{A}}\pi(a | x) \sum_{u \in \mathcal{X}}\,p(u | x, a)\,\left[r(x, a) + \gamma\,v_{\pi}(u)  \right], \quad \forall x \in \mathcal{X} \\[8pt]
>q_{\pi}(x, a) &=  \sum_{u \in \mathcal{X}}\,p(u | x, a)\,\left[\,r(x, a) + \gamma\,\sum_{a' \in \mathcal{A}}\pi(a' | u)\,q_{\pi}(u, a')  \right], \quad \forall x \in \mathcal{X}, \; a \in \mathcal{A}
>\end{align*}
>$$



-----------
##  Recommended Notes and References


- [[Markov Decision Process]]
- [[Returns and Goals of Reinforcement Learning]]
- [[Bellman Optimality Equation for MDP]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 58
- [[Distributional Reinforcement Learning by Bellemare]] pp 26 - 27, 57, 78, 237
- [[Markov Decision Processes by Puterman]] pp 26
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1121
