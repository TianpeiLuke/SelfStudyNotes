---
tags:
  - concept
  - reinforcement_learning/bandit
  - online_learning/algorithms
keywords:
  - upper_confidence_bound_algorithm
  - optimism_under_uncertainty
topics:
  - online_learning
  - bandit_problem
  - reinforcement_learning
name: Upper Confidence Bound Algorithm
date of note: 2024-08-07
---

## Concept Definition

>[!important]
>**Name**: Upper Confidence Bound (UCB) Algorithm

![[Principle of Optimism under Uncertainty#^9b8645]]

>[!important]
>For *bandits*, the *optimism principle* means using the data observed so far to assign to each arm a value, called the **upper confidence bound** that with high probability is an *overestimate* of the unknown *mean*.

>[!important] Definition
>Let $(X_{t})_{t=1}^{n}$ be a sequence of **independent $1$-subgaussian random variables** with mean $\mu$. Denote the *sample mean* as $$\hat{\mu} = \frac{1}{n}\sum_{t=1}^{n}X_{t}.$$ By Hoeffding's inequality, $$\mathcal{P}\left\{ \mu \ge \hat{\mu} + \sqrt{ \frac{2\log(1 / \delta) }{n} } \right\} \le \delta. $$

- [[Sub-Gaussian Random Variable]]
- [[Sub-Gaussian Norm]]
- [[Hoeffding Inequality]]

### UCB for Sub-Gaussian Rewards

![[Explore-Then-Commit Bandit Algorithm#^37b26f]]

>[!important] Definition
>Let the *rewards* $(X_{t})_{t=1}^{n}$ be a sequence of **independent $1$-subgaussian random variables**. 
>
>- Denote $T_{i}(t)$ be the **number of times** *action (arm)* $i$ has been played *after round* $t$, $$T_{i}(t) = \sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}$$
>- The *empirical mean of rewards* from arm $i$ *after round $t$* is $$\hat{\mu}_{i}(t) := \frac{1}{T_{i}(t)} \sum_{s=1}^{t}\mathbb{1}\left\{ A_{s} = i \right\}\,X_{s}$$
>- Then a reasonable **upper confidence bound** for the *unknown mean* $\mu_{i}$ of the $i$-th arm *after round $t$* is 
>  $$
>  \begin{align*}
>  \text{UCB}_{i}(t, \delta) &= \left\{\begin{array}{lc}\hat{\mu}_{i}(t)+ \sqrt{ \dfrac{2\log(1 / \delta) }{T_{i}(t)} } & \text{ if }T_{i}(t) > 0\\ \infty & \text{ if } T_{i}(t) = 0 \end{array}
>  \right.
>  \end{align*}
> $$

^20418e

>[!info]
>Note that compared to the fixed number of sample $n$ in the *Hoeffding bound*, in the **UCB**, the denominator $T_{i}(t)$ is a *random variable*.

>[!quote]
>the intuition remains that $\delta$ is *approximately* an **upper bound** on the **probability** of the event that the **above quantity** is an *underestimate of the true mean*.
>
>-- [[Bandit Algorithms by Lattimore]] pp 85

### UCB Algorithm

![[Explore-Then-Commit Bandit Algorithm#^463d5d]]


>[!important] Definition
>The **Upper Confidence Bound (UCB($\delta$))** algorithm is described as follows:
>- *Require*: the parameter $m$
>- *Require*: arms $\{ 1 \,{,}\ldots{,}\, k\}$
>- *Require*: approximation error bound $\delta >0$
>- *Initialize* the list of rewards $\hat{\mu}_{i}(0)=0$ and $T_{i}(0) = 0$ for $i=1\,{,}\ldots{,}\,k$
>- *Compute* the initial upper confidence $\text{UCB}_{i}(0, \delta) = \infty$ 
>- For $t=1\,{,}\ldots{,}\,T$:
>	- Choose **action (arm)** $A_{t}$ that *maximize* *the upper confidence bound* $$A_{t} = \arg\max_{i}\,\text{UCB}_{i}(t-1, \delta)$$ 
>		- Break ties by *randomly select an action*.
>	- Observe **reward** $X_{t}$
>	- Update the *number of times* that the arm $A_{t}$ is played as $$T_{i}(t)  = \left\{ \begin{array}{cc} T_{i}(t-1) + 1 & \text{ if } i = A_{t}\\ T_{i}(t-1)&\text{ if } i\neq A_{t}\end{array} \right.$$
>	- Update the **average reward** for all arms $i=1\,{,}\ldots{,}\,k$ $$\hat{\mu}_{i}(t)  = \left\{ \begin{array}{cc} \hat{\mu}_{i}(t-1) + \dfrac{1}{T_{i}(t)}\left(X_{t} - \hat{\mu}_{i}(t-1)\right) & \text{ if } i = A_{t}\\ \hat{\mu}_{i}(t-1) &\text{ if } i\neq A_{t}\end{array} \right.$$
>	- Compute the **upper confidence bound** for all arms $i=1\,{,}\ldots{,}\,k$ 
>	  $$\begin{align*}\text{UCB}_{i}(t, \delta) &= \left\{\begin{array}{lc}\hat{\mu}_{i}(t)+ \sqrt{ \dfrac{2\log(1 / \delta) }{T_{i}(t)} } & \text{ if }T_{i}(t) > 0\\ \infty & \text{ if } T_{i}(t) = 0 \end{array}\right.\end{align*}$$

- [[Explore-Then-Commit Bandit Algorithm]]

>[!important] Definition
>The value inside the argmax is called the **index** of arm $i$. 
>- Generally speaking, an **index algorithm** chooses the arm in each round that *maximises some value* (the index), which usually only depends on the *current time* step and the *samples* from that arm. 
>- In the case of **UCB**, the index is the sum of the empirical mean of rewards experienced so far and the **exploration bonus**, which is also known as the **confidence width**.

- [[Confidence Interval]]


## Explanation

>[!quote]
>The intuitive reason why this leads to *sublinear regret* is simple. Assuming the upper confidence bound assigned to the optimal arm is indeed an *overestimate*, then another arm can only be played if its upper confidence bound is *larger* than that of the *optimal arm*, which in turn is larger than the *mean of the optimal arm*. And yet this *cannot happen too often* because the additional data provided by playing a suboptimal arm means that the upper confidence bound for this arm will *eventually fall* below that of the optimal arm.
>
>-- [[Bandit Algorithms by Lattimore]] pp 85

>[!quote]
>Besides the slightly vague **‘optimism guarantees optimality or learning’** intuition we gave before, it is worth exploring other intuitions for the choice of index. At a very basic level, an algorithm should explore arms *more often* if they are (a) **promising** because $\hat{\mu}(t-1)$ is large or (b) **not well explored** because $T_{i}(t-1)$ is small. As one can plainly see, the definition in Eq. (7.2) exhibits this behaviour. This explanation is not completely satisfying, however, because it does not explain *why* the form of the functions is just so.
>
>-- [[Bandit Algorithms by Lattimore]] pp 85

## Regret Analysis






-----------
##  Recommended Notes and References


- [[Principle of Optimism under Uncertainty]]
- [[KL-Upper Confidence Bound Algorithm]]
- [[Upper Confidence Bound Algorithm Asymptotic Optimality]]
- [[Upper Confidence Bound Algorithm Minmax Optimality]]

- [[Returns and Goals of Reinforcement Learning]]
- [[Explore-Then-Commit Bandit Algorithm]]
- [[Multi-Armed Adversarial Bandit]]



- [[Bandit Algorithms by Lattimore]] pp 84 - 96
- [[Reinforcement Learning An Introduction by Sutton]] pp 35