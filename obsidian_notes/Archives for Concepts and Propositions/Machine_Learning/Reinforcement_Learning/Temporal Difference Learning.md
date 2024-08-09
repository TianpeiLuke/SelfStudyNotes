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
> v_{\pi}(s) &= \mathbb{E}_{ \pi }\left[  G_{t} \,|\, S_{t} = s \right]  \\[5pt]
> &\approx \widehat{\mathbb{E}}\left[  G_{t} \,|\, S_{t} = s \right]  := V_{N(s)}(s)  \\[5pt]
> &= \frac{1}{N(s)}\,\sum_{t=1}^{N(s)} G_{t} \\
> &= \frac{1}{N(s)}\left[ G_{N(s)} + (N(s)-1)\frac{\sum_{t=1}^{N(s)-1} G_{t}}{N(s)-1} \right]  \\[5pt]
> &= \frac{1}{N(s)-1}\sum_{t=1}^{N(s)-1} G_{t} + \frac{1}{N(s)}\left[ G_{N(s)} -  \frac{1}{N(s)-1}\sum_{t=1}^{N(s)-1} G_{t} \right]  \\[10pt]
> V_{N(s)}(s)&= V_{N(s)-1}(s) + \alpha_{N(s)}\left(G_{N(s)} -  V_{N(s)-1}(s)\right)
> \end{align*}
>$$  
>where $N(s) = |T(s)|$ and $T(s) = \{S_{t}=s\}_{t=1}^{\infty}$ or the *number of epsiodes* for **first-visit MC**. 

>[!important] Definition
>The above incremental update can be summarized as 
>$$
>\begin{align}
> V(S_{t}) &\leftarrow V(S_{t}) + \alpha_{t}\left(G_{t} - V(S_{t})\right) \\[5pt]
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
> V(S_{t}) &\leftarrow V(S_{t}) + \alpha_{t}\left(G_{t} - V(S_{t})\right) \\[5pt]
> \text{\textbf{new} estimate}&\leftarrow \text{\textbf{old} estimate} + \text{step\_size}\left(\text{\textbf{target}} - \text{\textbf{old} estimate}\right)\nonumber
> \end{align}
>$$  
>  by 
>  - **replacing** the *returns* at $t$ with the **returns at $t+1$** and the **rewards**; 
>  $$G_{t} = R_{t+1}+ \gamma  G_{t+1}.$$ 
>  
> -  Then TD replaces the **estimate** of *return* at $t+1$, $G_{t+1}$, with the *value function* $V(S_{t+1})$ at $t+1$, i.e. $$\hat{G}_{t+1} = V(S_{t+1})$$ 
>   
> That is, the **TD update formula** is
> $$ 
> \begin{align}
> V(S_{t}) &\leftarrow V(S_{t}) + \alpha_{t}\left(G_{t} - V(S_{t})\right) \nonumber\\[5pt]
> &\approx V(S_{t}) + \alpha_{t}\left(R_{t+1} + \gamma V(S_{t+1})  - V(S_{t})\right). 
> \end{align}
>$$  
>
>This algorithm is called **one-step TD** or **TD(0)**. 
>
>  
>- The quantity $$R_{t+1} + \gamma V(S_{t+1})$$ is referred as the **target** (*instead of* $G_{t}$ for Monte Carlo methods.) and 
>- Define $$\delta_{t} := R_{t+1} + \gamma V(S_{t+1})  - V(S_{t})$$ as the **Temporal-Difference error** or, **TD error**. 

^a52316

- [[Sarsa Algorithm and On-Policy Temporal Difference Control]]
- [[Expected Sarsa Algorithm]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]


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
>The approximation of target $$G_{t} \approx R_{t+1} + \gamma V(S_{t+1})$$ is the **key** for TD learning. 
>
>It comes from **Bellman equation** combining with **Monte Carlo estimation**:
>$$
> \begin{align}
> v_{\pi}(s) &= \mathbb{E}_{ \pi }\left[  G_{t} \,|\, S_{t} = s \right] \approx \widehat{\mathbb{E}}\left[  G_{t} \,|\, S_{t} = s \right] \nonumber\\[5pt]
> &=  \mathbb{E}_{ \pi }\left[ R_{t+1}+ \gamma G_{t+1} | S_{t} = s \right]  \nonumber\\[5pt]
> &=\mathbb{E}_{ \pi }\left[R_{t+1}  + \gamma\,v_{\pi}(S_{t+1}) | S_{t} = s\right], \text{ (Bellman equation)} \nonumber\\[5pt]
> &\approx \widehat{\mathbb{E}}\left[ R_{t+1}  + \gamma\,v_{\pi}(S_{t+1}) | S_{t} = s\right],, \text{ (Monte Carlo estimate)} \nonumber\\[5pt]
> \text{thus }G_{t}&\approx R_{t+1}+  \gamma v_{\pi}(S_{t+1})\nonumber\\[5pt]
> &\approx R_{t+1}+  \gamma  V(S_{t+1}).
> \end{align}
>$$ 
>The last *approximation* is to replace $v_{\pi}$ with its *estimate* $V$. 

- [[Value Function and Bellman Equation for MDP]]

>[!important]
>Whereas **Monte Carlo methods** must wait until the **end of the episode** to determine the *increment* to $V(S_t)$ (only then is $G_t$ known), **TD methods** need to wait only until the **next time step**. 
>  

- [[Dynamic Programming for MDP]]
- [[Monte Carlo and Applications]]


>[!important]
>Let us compare **TD learning**  to **Dynamic Programming (DP)** and **Monte Carlo (MC)**. Because TD($0$) bases its update in part on an existing estimate, we say that it is a **bootstrapping method**, like DP. 
>
>Check the value function and Bellman equation as 
>$$
> \begin{align}
> \text{DP: }v_{\pi}(s) &=  \mathbb{E}_{ \pi }\left[  R_{t+1}  + \gamma\,v_{\pi}(S_{t+1}) | S_{t} = s \right] \ \\[5pt]
> \text{MC: }v_{\pi}(s) &=  \mathbb{E}_{ \pi }\left[  G_{t} | S_{t} = s \right] 
> \end{align}
>$$  
>- **DP** estimate uses an estimate of the **Bellman equation** as target.
>	- Although the *expectation* can be computed exactly, the value at state $S_{t+1}$ is an *estimate* since we do not know $S_{t+1}$ at time $t$. 
>- The **MC** uses an estimate as *target*. 
>	- The **Monte Carlo target** is an *estimate* because the *expected value* is not known; 
>	- a *sample return* is used in place of the *real expected return*. 
>- The **TD target** is an estimate for *both reasons*: 
>	- it *samples the expected values*  and 
>	- it uses the *current estimate* $V$ instead of the *true* $v_{\pi}$. 
>
>Thus, *TD methods* **combine** the **sampling** of Monte Carlo with the **bootstrapping** of DP.






-----------
##  Recommended Notes and References

- [[Approximate Dynamic Programming for MDP]]


- [[Eligibility Traces]]
- [[Sarsa Algorithm and On-Policy Temporal Difference Control]]
- [[Expected Sarsa Algorithm]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]

- [[Monte Carlo and Applications]]

- [[Reinforcement Learning An Introduction by Sutton]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1137, 1140 - 1142
- [[Foundations of Machine Learning by Mohri]] pp 330 - 335