---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
keywords:
  - policy_gradient_optimization
topics:
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
name: Policy Gradient Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Policy Gradient Algorithm

![[Markov Decision Process#^f5dcdf]]

![[Markov Decision Process#^f0b818]]

![[Markov Decision Process#^c86b5a]]

![[Markov Decision Process#^a1e9de]]

>[!important] Definition
>Denote $\theta \in \mathbb{R}^{m}$, the **parameterized policy distribution** over $a \in \mathcal{A}(s)$ at time $t$ is $$\pi(a | s, \theta) := Pr\{A_t =a | S_{t}=s, \theta_t=\theta\}.$$ 
>
>The **goal** of **policy optimization** is to find policy $\pi$ that *maximizes* some *objective function*  $\mathcal{R}(\theta_t)$. 
>
>For instance, for continuing tasks with ergodic MDP, we choose **average rewards** $$\mathcal{R}(\theta_t) := r(\pi(a |s, \theta))$$
>where
>$$
> \begin{align}
> r(\pi(a | s, \theta)) &= \sum_{t=0}^{\infty} \mathbb{E}^{\pi}\left[ \,r(X_{t}, A_{t})  \right]\\[8pt]  \\
>&=\sum_{s}\mu_{\pi}(s)\sum_{a}\pi(a |s, \theta) \sum_{s', r}p(s', r| s, a)r. 
> \end{align}
>$$ 

^f0d871

- [[Markov Decision Process]]
- [[Returns and Goals of Reinforcement Learning]]
- [[Episodic and Continuing Task in Reinforcement Learning]]

### Policy Gradient Descent

>[!important] Definition
>The objective of **policy gradient optimization** is the *average rewards*
>$$\mathcal{R}(\theta_t) := r(\pi(a |s, \theta))$$
>where
>$$
> \begin{align}
> r(\pi(a | s, \theta)) &= \sum_{s}\mu_{\pi}(s)\sum_{a}\pi(a |s, \theta) \sum_{s', r}p(s', r| s, a)\;r. 
> \end{align}
>$$ 
>The **policy gradient method** optimizes the above objective using the *gradient acsent algorithm*
>$$
> \begin{align}
> \theta_{t+1} &\leftarrow \theta_t + \alpha \nabla_{\theta}\mathcal{R}(\theta_t). 
> \end{align}
>$$
>where, by the **policy gradient theorem**,
>$$
>\begin{align}
>\nabla_{\theta}\mathcal{R}(\theta) &=  \mathbb{E}_{ S \sim \mu_{\pi(\theta)} }\left[\,\mathbb{E}_{ A \sim  \pi(a\,|\,s, \theta)  }\left[\, \nabla_{\theta} \log \pi(A \,|\,S\,,\,\theta)\,q_{\pi}(S, A) \right] \right]
> \end{align}
>$$

^b0c7df

- [[Gradient Descent Algorithm]]
- [[Stochastic Gradient Descent Algorithm]]

### Policy Gradient Theorem

![[Policy Gradient Theorem#^672c0f]]

- [[Policy Gradient Theorem]]


## Explanation

>[!info]
>- All methods that follow the general schema we call **policy gradient methods**, whether or not they also learn an *approximate value function*. 
>- Methods that learn *approximations* to *both policy* and *value functions* are often called **actor-critic methods**, where
>	- '**actor**' is a reference to the *learned policy*, and 
>	- '**critic**' refers to the *learned value function*, usually a state-value function.
> 

- [[Actor-Critic Algorithm]]
- [[Actor-Critic Algorithm with Eligibility Traces]]
- [[Value Function and Bellman Equation for MDP]]




-----------
##  Recommended Notes and References


- [[Sequential Decision Process]]
- [[Statistical Decision Problem]]
- [[Valued-based and Policy-based Reinforcement Learning]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 324 - 326
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1147
