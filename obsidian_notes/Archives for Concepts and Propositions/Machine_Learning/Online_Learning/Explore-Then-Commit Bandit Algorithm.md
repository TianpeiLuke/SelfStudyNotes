---
tags:
  - concept
  - reinforcement_learning/bandit
  - online_learning/algorithms
keywords:
  - multi_arm_bandit
  - explore_then_commit_bandit
topics:
  - online_learning
  - bandit_problem
  - reinforcement_learning
name: Explore-Then-Commit Bandit Algorithm
date of note: 2024-08-07
---

## Concept Definition

>[!important]
>**Name**: Explore-Then-Commit Bandit Algorithm

>[!important]
>In **Explore-Then-Commit (ETC)** algorithm, the learner *explores* by playing each arm *a fixed number of times* and then *exploits* by *committing* to the arm that appeared *best* during exploration.

>[!important] Definition
>Let $(X_{1} \,{,}\ldots{,}\,X_{t})$ be all historical rewards received after round $t$.
>
>Define the **average rewards** received from arm $i$ *after round* $t$ as
>$$
>\hat{\mu}_{i}(t) := \frac{1}{T_{i}(t)} \sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}\,X_{s} 
>$$
>where $T_{i}(t)$ is the **number of times** *action* $i$ has been played *after round *$t$,
>$$
>T_{i}(t) = \sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}
>$$

^37b26f

>[!info]
>We can derive an **online update** for the average reward
>$$
>\begin{align*}
> \hat{\mu}_{i}(t) &=  \frac{\sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}\,X_{s} }{\sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}} \\[5pt]
> &= \frac{\sum_{s=1}^{t-1}\mathbb{1}\left\{ A_{s} = i \right\}}{\sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}} \frac{\sum_{s=1}^{t-1}\mathbb{1}\left\{ A_{s} = i \right\}\,X_{s} }{\sum_{s=1}^{t-1}\mathbb{1}\left\{ A_{s} = i \right\}} + \frac{\mathbb{1}\left\{ A_{t} = i \right\}\,X_{t} }{\sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}} \\[5pt]
> &= \frac{\sum_{s=1}^{t-1}\mathbb{1}\left\{ A_{s} = i \right\}}{\sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}}\, \hat{\mu}_{i}(t-1) + \frac{\mathbb{1}\left\{ A_{t} = i \right\}\,X_{t} }{\sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}} \\[5pt]
> &= \left(1 - \frac{\mathbb{1}\left\{ A_{t} = i \right\}}{\sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}}\right)\,\hat{\mu}_{i}(t-1) + \frac{\mathbb{1}\left\{ A_{t} = i \right\}\,X_{t} }{\sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}} \\[5pt]
> &= \hat{\mu}_{i}(t-1) + \alpha_{t,i}\left(X_{t} - \hat{\mu}_{i}(t-1)\right)
>\end{align*}
>$$
>where 
>$$
>\alpha_{t,i} := \frac{\mathbb{1}\left\{ A_{t} = i \right\}}{\sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}} \in [0,1]
>$$
>
>Thus we just need to update the *average reward* for **the action taken**. 
>
>For instance, if $A_{t} = i$, then 
>- for all $j\neq i$, $$\hat{\mu}_{j}(t) = \hat{\mu}_{j}(t-1)$$
>- for $i$, $$\hat{\mu}_{i}(t) = \hat{\mu}_{i}(t-1) + \frac{1}{T_{i}(t)}\left(X_{t} - \hat{\mu}_{i}(t-1)\right)$$

^30b29b


>[!important] Definition
>The **Explore-Then-Commit (ETC)** algorithm is described as below:
>- *Require*: the parameter $m$
>- *Require*: arms $\{ 1 \,{,}\ldots{,}\, k\}$
>- *Initialize* the list of rewards $\hat{\mu}_{i}(0)=0$ for $i=1\,{,}\ldots{,}\,k$
>- For $t=1\,{,}\ldots{,}\,T$:
>	- Choose **action (arm)** $A_{t}$ as $$A_{t} = \left\{ \begin{array}{cc} (t{\mod k}) + 1 & \text{ if }t \le m\,k\\ \arg\max_{i}\,\hat{\mu}_{i}(mk) &\text{ if }t > m\,k \end{array} \right.$$
>	- Observe **reward** $X_{t}$
>	- Update the *number of times* that the arm $A_{t}$ is played as $$T_{i}(t)  = \left\{ \begin{array}{cc} T_{i}(t-1) + 1 & \text{ if } i = A_{t}\\ T_{i}(t-1)&\text{ if } i\neq A_{t}\end{array} \right.$$
>	- Update the **average reward** for all arms $i=1\,{,}\ldots{,}\,k$ $$\hat{\mu}_{i}(t)  = \left\{ \begin{array}{cc} \hat{\mu}_{i}(t-1) + \dfrac{1}{T_{i}(t)}\left(X_{t} - \hat{\mu}_{i}(t-1)\right) & \text{ if } i = A_{t}\\ \hat{\mu}_{i}(t-1) &\text{ if } i\neq A_{t}\end{array} \right.$$

^463d5d

- [[Multi-Armed Adversarial Bandit]]
- [[epsilon-Greedy Algorithm]]

## Explanation

>[!info]
>Some other names for this algorithm is **forced sampling**, **explore-first**, **explore-then-exploit**. 

![[Multi-Armed Adversarial Bandit#^d92056]]

>[!important]
>The **online update** of *cumulative reward*
>$$
>\hat{\mu}_{i}(t) = \hat{\mu}_{i}(t-1) + \alpha_{t,i}\left(X_{t} - \hat{\mu}_{i}(t-1)\right)
>$$
>has the format of 
>$$
>\text{new estimate } = \text{ old estimate } + \text{ stepsize} \times \left(\text{ target } - \text{ old estimate}\right) 
>$$

- [[Temporal Difference Learning]]
- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]



-----------
##  Recommended Notes and References


- [[Returns and Goals of Reinforcement Learning]]
- [[Upper Confidence Bound Algorithm]]
- [[Multi-Armed Adversarial Bandit]]
- [[Exploration and Exploitation Tradeoff]]


- [[Bandit Algorithms by Lattimore]] pp 75
- [[Reinforcement Learning An Introduction by Sutton]]