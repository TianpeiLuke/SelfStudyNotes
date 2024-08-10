---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - temporal_difference_learning
topics:
  - reinforcement_learning/algorithm
name: Temporal Difference Learning
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Temporal Difference Learning

### Online Update of Monte Carlo Estimate of Value Function

>[!info]
>Recall that in Monte Carlo Methods, the value function is estimated by sample episodes. We can write it into an **incremental update**. 
>
>Let $V(s)$ be the *(empirical) estimate* of *state-value* $v_{\pi}(s)$,  
>$$
> \begin{align*}
> v_{\pi}(s) &= \mathbb{E}_{ \pi }\left[  G_{t} \,|\, X_{t} = s \right]  \\[5pt]
> &\approx \widehat{\mathbb{E}}\left[  G_{t} \,|\, X_{t} = s \right]  := V_{N(s)}(s)  \\[5pt]
> &= \frac{1}{N(s)}\,\sum_{t=1}^{N(s)} G_{t} \\
> &= \frac{1}{N(s)}\left[ G_{N(s)} + (N(s)-1)\frac{\sum_{t=1}^{N(s)-1} G_{t}}{N(s)-1} \right]  \\[5pt]
> &= \frac{1}{N(s)-1}\sum_{t=1}^{N(s)-1} G_{t} + \frac{1}{N(s)}\left[ G_{N(s)} -  \frac{1}{N(s)-1}\sum_{t=1}^{N(s)-1} G_{t} \right]  \\[10pt]
> V_{N(s)}(s)&= V_{N(s)-1}(s) + \alpha_{N(s)}\left(G_{N(s)} -  V_{N(s)-1}(s)\right)
> \end{align*}
>$$  
>where $N(s) = |T(s)|$ and $T(s) = \{X_{t}=s\}_{t=1}^{\infty}$ or the *number of epsiodes* for **first-visit MC**. 

>[!important] Definition
>The above incremental update can be summarized as 
>$$
>\begin{align}
> V(X_{t}) &\leftarrow V(X_{t}) + \alpha_{t}\left(G_{t} - V(X_{t})\right) \\[5pt]
> \text{\textbf{new} estimate}&\leftarrow \text{\textbf{old} estimate} + \text{step\_size}\left(\text{\textbf{target}} - \text{\textbf{old} estimate}\right)\nonumber
> \end{align}
>$$  
>This formula defines the value function using two terms: 
>- the **old estimate**, and 
>- the **difference** between the **target** and the **old estimate**. 
>  
>We call this algorithm **constant-$\alpha$ Monte Carlo**. 

- [[Explore-Then-Commit Bandit Algorithm]]

### Temporal Difference Learning

>[!important] Definition
>The **Temporal-Difference (TD) learning** extends the formula in
>$$
>\begin{align}
> V(X_{t}) &\leftarrow V(X_{t}) + \alpha_{t}\left(G_{t} - V(X_{t})\right) \\[5pt]
> \text{\textbf{new} estimate}&\leftarrow \text{\textbf{old} estimate} + \text{step\_size}\left(\text{\textbf{target}} - \text{\textbf{old} estimate}\right)\nonumber
> \end{align}
>$$  
>  by 
>  - **replacing** the *returns* at $t$ with the **returns at $t+1$** and the **rewards**; 
>  $$G_{t} = R_{t+1}+ \gamma  G_{t+1}.$$ 
>  
> -  Then TD replaces the **estimate** of *return* at $t+1$, $G_{t+1}$, with the *value function* $V(X_{t+1})$ at $t+1$, i.e. $$\hat{G}_{t+1} = V(X_{t+1})$$ 
>   
> That is, the **TD update formula** is
> $$ 
> \begin{align}
> V(X_{t}) &\leftarrow V(X_{t}) + \alpha_{t}\left(G_{t} - V(X_{t})\right) \nonumber\\[5pt]
> &\approx V(X_{t}) + \alpha_{t}\left(R_{t+1} + \gamma V(X_{t+1})  - V(X_{t})\right). 
> \end{align}
>$$  
>
>This algorithm is called **one-step TD** or **TD(0)**. 
>
>  
>- The quantity $$R_{t+1} + \gamma V(X_{t+1})$$ is referred as the **target** (*instead of* $G_{t}$ for Monte Carlo methods.) and 
>- Define $$\delta_{t} := R_{t+1} + \gamma V(X_{t+1})  - V(X_{t})$$ as the **Temporal-Difference error** or, **TD error**.
>	- it represent the *difference* of the *estimated returns* between *current time* and *immediate next time.*

^a52316

- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Expected SARSA Algorithm]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]

### TD(0) Algorithm

>[!important] Definition
>The **tabular-based TD(0) algorithm** is described as below:
>- *Require*: policy $\pi$
>- *Require*: step size $\alpha >0$
>- *Initialize* **table for state-value function** $V_{0}(x)$ for all $x\in \mathcal{X}$. 
>	- Note that the **terminal state** $V_{0}(x_{\text{terminal}}) = 0$
>- For **episode** $k=1,\,2\,{,}\ldots{,}\,$:
>	- Initialize state $X_{0}$
>	- For step $t=0,\,1\,{,}\ldots{,}\,T$:
>		- Generate a **sample action** according to *policy* $\pi$ and *current state* $$A_{t} \sim \pi(\cdot| X_{t})$$
>		- Take action $A_{t}$
>		- Observe **reward** $R_{t}$ and **next state** $X_{t+1}$
>		- **Temporal difference update**: $$V_{t+1}(X_{t}) = V_{t}(X_{t}) + \alpha \left\{ R_{t} + \gamma\,V_{t}(X_{t+1}) - V_{t}(X_{t}) \right\} $$





## Explanation


>[!important] 
>**Temporal-Difference (TD) Learning** is a *combination* of *Monte Carlo* ideas and *dynamic programming (DP)* ideas. 
>- Like **Monte Carlo methods**, TD methods can *learn* directly from raw experience *without a model* of the  *environment’s dynamics*. 
>- Like **DP**, TD methods *update estimates* based in part on other learned estimates, without waiting for a final outcome (they **bootstrap**). 
>
>The relationship between **TD**, **DP**, and **Monte Carlo methods** is a recurring theme in the theory of reinforcement learning. 

- [[Dynamic Programming for MDP]]
- [[Monte Carlo and Applications]]
- [[Sequential Importance Sampling]]
- [[Bootstrap Method]]

>[!info]
> Note that TD, DP, and **Monte Carlo control** all use the same **Generalized Policy Iteration (GPI)** methods to improve policy. The differences in the methods are primarily differences in their approaches to the **prediction** problem.

- [[Policy Iteration Algorithm]]

>[!info]
> Another thing to note is that all of methods we discussed above is **Tabular method**, since we do not assume any functional form for the value function but just record it into a table. 

>[!info]
>The temporal difference learning in this section is a special case of **multi-step TD** or **TD($\lambda$)**. 

- [[Eligibility Traces]]

### Temporal Difference Learning, Monte Carlo Method and Dynamic Programming


>[!important]
>The approximation of target $$G_{t} \approx R_{t+1} + \gamma V(X_{t+1})$$ is the **key** for TD learning. 
>
>It comes from **Bellman equation** combining with **Monte Carlo estimation**:
>$$
> \begin{align}
> v_{\pi}(s) &= \mathbb{E}_{ \pi }\left[  G_{t} \,|\, X_{t} = s \right] \approx \widehat{\mathbb{E}}\left[  G_{t} \,|\, X_{t} = s \right] \nonumber\\[5pt]
> &=  \mathbb{E}_{ \pi }\left[ R_{t+1}+ \gamma G_{t+1} | X_{t} = s \right]  \nonumber\\[5pt]
> &=\mathbb{E}_{ \pi }\left[R_{t+1}  + \gamma\,v_{\pi}(X_{t+1}) | X_{t} = s\right], \text{ (Bellman equation)} \nonumber\\[5pt]
> &\approx \widehat{\mathbb{E}}\left[ R_{t+1}  + \gamma\,v_{\pi}(X_{t+1}) | X_{t} = s\right],, \text{ (Monte Carlo estimate)} \nonumber\\[5pt]
> \text{thus }G_{t}&\approx R_{t+1}+  \gamma v_{\pi}(X_{t+1})\nonumber\\[5pt]
> &\approx R_{t+1}+  \gamma  V(X_{t+1}).
> \end{align}
>$$ 
>The last *approximation* is to replace $v_{\pi}$ with its *estimate* $V$. 

- [[Value Function and Bellman Equation for MDP]]

>[!important]
>Whereas **Monte Carlo methods** must wait until the **end of the episode** to determine the *increment* to $V(X_t)$ (only then is $G_t$ known), **TD methods** need to wait only until the **next time step**. 
>  

- [[Dynamic Programming for MDP]]
- [[Monte Carlo and Applications]]


>[!info]
>Let us compare **TD learning**  to **Dynamic Programming (DP)** and **Monte Carlo (MC)**. Because TD($0$) bases its update in part on an existing estimate, we say that it is a **bootstrapping method**, like DP. 
>
>Check the value function and Bellman equation as 
>$$
> \begin{align}
> \text{DP: }v_{\pi}(s) &=  \mathbb{E}_{ \pi }\left[  R_{t+1}  + \gamma\,v_{\pi}(X_{t+1}) | X_{t} = s \right] \ \\[5pt]
> \text{MC: }v_{\pi}(s) &=  \mathbb{E}_{ \pi }\left[  G_{t} | X_{t} = s \right] 
> \end{align}
>$$  
>- **DP** estimate uses an estimate of the **Bellman equation** as target.
>	- Although the *expectation* can be computed exactly, the value at state $X_{t+1}$ is an *estimate* since we do not know $X_{t+1}$ at time $t$. 
>- The **MC** uses an estimate as *target*. 
>	- The **Monte Carlo target** is an *estimate* because the *expected value* is not known; 
>	- a *sample return* is used in place of the *real expected return*. 
>- The **TD target** is an estimate for *both reasons*: 
>	- it *samples the expected values*  and 
>	- it uses the *current estimate* $V$ instead of the *true* $v_{\pi}$. 
>
>Thus, *TD methods* **combine** the **sampling** of Monte Carlo with the **bootstrapping** of DP.

>[!important]
>The advantages of temporal difference method **TD(0)** over **dynamic programming** and **Monte Carlo methods** can be summarized as below:
>- Both Monte Carlo, TD(0) are **sample-based learning** algorithm. They do not require *complete* knowledge of *dynamics* $p$.  DP, however, requires a **model**. 
> 
>- TD($0$) learning naturally is an **online learning algorithm**, which *updates the value* estimate at end of each time step. 
>	- On the other hand, Monte Carlo algorithm only updates at the **end of episode** so that it can observe the return value. 
>	- Because of this, TD($0$) updates information based on *observed rewards* **faster** than MC. 
>	- MC is very **slow** esp. when one episode is long. Some Monte Carlo methods must ignore or discount episodes on which experimental actions are taken, which can greatly slow learning.
> 
>- TD(0) learning also has **convergence guarantee**. 
>	- For any fixed policy $\pi$, TD($0$) has been proved to **converge** to $v_{\pi}$, **in the mean** for a constant step-size parameter if it is sufficiently small, and **with probability $1$** if the step-size parameter decreases according to the usual stochastic approximation conditions. 
>	- In that sense, both TD and Monte Carlo methods converge *asymptotically* to the correct predictions. 
> 
>- Both DP and TD(0) use **bootstrapping**. They **learn a guess from a guess**, i.e. they update the value estimate of a state based on value estimate of its successor state plus the rewards after it. 
>	- In other words, This helps to **reduce the variance** of estimate compared to MC methods. 
>



### Compare with Supervised Learning

>[!info]
>We can also compare with **unsupervised learning** and **supervised learning**:
>- Like MC and DP, TD prediction has a **target**. On the other hand, all of these methods are *unsupervised* since *no human label is needed*. Just need to wait for the target observation. 
>	- In that sense, it is more **scalable**, and **model-free**. 
>	- TD learning is a method for **learning to predict**. 
>	- In particular, it learns a prediction based on **another, later, learned prediction**. 
>	- **TD error** is the difference between two predictions $R_{t+1} + \gamma V(S_{t+1})$ and $V(S_{t})$. In this sense, it is very similar to **supervised learning**. 
>	- Like *back-propagation* the error in supervised learning, TD learning also **predict the value backwards** from the terminal state. 
> 
>- TD learning is relevent only when we consider **multi-step prediction**.  
>- The thing predicted (the *discounted cumulative rewards* conditional on some behavior) is **multi-step** in the future. This is very different from supervised learning, which makes a one-step prediction only. 
> 




### Advantages of TP Prediction







-----------
##  Recommended Notes and References


- [[Dynamic Programming for MDP]]


- [[Eligibility Traces]]
- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Expected SARSA Algorithm]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]

- [[Monte Carlo and Applications]]

- [[Reinforcement Learning An Introduction by Sutton]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1137, 1140 - 1142
- [[Foundations of Machine Learning by Mohri]] pp 330 - 335