---
tags:
  - concept
  - machine_learning/theory
  - reinforcement_learning/theory
  - statistics/decision_theory
  - math/stochastic_process
keywords:
  - returns_reinforcement_learning
  - reward_reinforcement_learning
topics:
  - machine_learning_theory
  - reinforcement_learning
name: Markov Decision Process
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Returns and Reward in Reinforcement Learning

![[Markov Decision Process#^f5dcdf]]

![[Markov Decision Process#^a1e9de]]

>[!quote]
>In reinforcement learning, the purpose or **goal** of the **agent** is formalized in terms of a special signal, called the **reward**, passing from the environment to the agent. Informally, the agent’s goal is to **maximize the total amount of reward** it receives. We can clearly state this informal idea as the **reward hypothesis**:
>>[!info]
>>That all of what we mean by goals and purposes can be well thought of as the **maximization** of the **expected value** of the **cumulative sum** of a received *scalar signal* called **reward**.
>>
>- [[Reinforcement Learning An Introduction by Sutton]] pp 53

### Returns

>[!important] Definition
> The **return** is defined as the *cumulative rewards* in *the long run*/ *in future*. In general, we seek to **maximize the expected return**, where the **return**, denoted $G_t$, is defined as some specific function of the *reward sequence*.
> 
> In particular, given the **Markov decision process** $(T, \mathcal{X},\mathcal{A}, p_{t}(\cdot|x, a), r_{t}(x,a) )$,  and the history process $H_{t} = (X_{1}, A_{1}, \,{,}\ldots{,}\,A_{t-1}, X_{t})$, denote the reward at epoch $t\in T$ as $$R_{t} = r_{t}(X_{t}, A_{t})$$
> 
> Then the **return** $G_{t}$ is defined as the cumulative sum of future reward $\tau > t$
>$$  
> \begin{align*}
> G_{t} &= \sum_{\tau > t}R_{\tau}.
> \end{align*}
>$$
>


### Episodes and Episodic Tasks

>[!important] Definition
> In applications, where a final state at $T$ can be *observed* and after that, the enviroment and agents will be *reset* to inital state,  the *agent-environment interaction* breaks naturally into *subsequences*, which we call **episodes**. 
> 
> Examples include games such as chess, maze et al. 


>[!important] Definition
> Each episode ends in a special state called the **terminal state**, followed by a reset to a standard starting state or to a sample from a standard distribution of starting states. 


> [!important] Definition
> Tasks with episodes of this kind are called **episodic tasks**. 
> 
> In episodic tasks we sometimes need to distinguish the set of all **nonterminal states**, denoted $\mathcal{S}$, from the set of all states plus the **terminal state**, denoted $\mathcal{S}+$. 
> 
> The **time of termination**, $T$, is a random variable that normally varies from episode to episode. For episodic tasks,  the return is *finite* $$G_{t} = \sum_{t}^{T}R_{\tau}.$$

### Continuing Tasks

>[!important] Definition
> On the other hand, in many cases the agent–environment interaction *does not break* naturally into identifiable episodes, but goes on *continually without limit*. 
> 
> For example, this would be the natural way to formulate an on-going process-control task, or an application to a robot with a long life span. 
> 
> We call these **continuing tasks**. 

>[!important] Definition
> The return for continuing task can be *infinite*. 
> 
> So, in order to compute finite expectation of returns, we usually apply **discounts** $\gamma$ for *future rewards* based on the time passing. The **discounted return** is formulated as below
> $$
> \begin{align}
> G_{t} &= \sum_{\tau > t}\gamma^{\tau}R_{\tau} < \infty \nonumber\\
> &= R_{t+1} + \gamma\,G_{t+1}, 
> \end{align}
>$$  
>where $\gamma \in [0,1]$. 
>
>The **discount rate** $\gamma$ determines the *present* value of *future rewards*. 
>- Then $\gamma =0$, $G_{t} = R_{t+1}$, i.e. the **short-sighted returns**. 
>- If $\gamma \rightarrow 1$, we have the **far-sighted returns**, where the return objective takes future rewards into account more strongly. 

### Returns 

>[!important] Definition
> We can combine the notion of returns for episodic and continuing task as follows:
>$$ 
> \begin{align}
> G_{t}&= \sum_{\tau = t+1}^{T}\gamma^{\tau-t-1}R_{\tau}.  \\
> &=R_{t+1} + \gamma\,G_{t+1}  \nonumber
> \end{align}
>$$  
>Note that we can allow $T=\infty$ or $\gamma=1$ but not both. 
>
>To convert an episodic task into continuing task, we can define an **absorbing state** that *transitions only to to itself* and generates *zero rewards*. 

- [[Markov Decision Process]]



## Explanation

>[!info]
> The use of a **reward signal** to formalize the idea of a **goal** is one of the **most distinctive features** of **reinforcement learning**. Note that the reward signal is *not* the place to *impart* to the agent *prior knowledge* about *how* to achieve what we want it to do. If the winning is the goal, then *achieving subgoals* are not considered as rewards, since the agents may stop when achieving the subgoal. 
> 
> In many real-world examples, however, the reward hypothesis may not hold. For instance, if the goal is to achieve the best outcome under worst case situations, then simply maximizing the rewards may not yield the good solution. Similar case such as *risk-sensitive/avert examples* also requires us to find solution that may not be the best in terms of cumulative rewards but avoids the worst situations.  Also, sometimes, if the goal is very *far away*, and solving *sub-problems* may still make sense to achieve the end results, 



-----------
##  Recommended Notes and References

- [[Bellman Optimality Equation for MDP]]
- [[Temporal Difference Learning]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]

- [[Markov Decision Process]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 53





