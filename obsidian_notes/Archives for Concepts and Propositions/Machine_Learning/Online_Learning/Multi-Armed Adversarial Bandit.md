---
tags:
  - concept
  - machine_learning/algorithms
  - online_learning/algorithms
  - reinforcement_learning/bandit
keywords:
  - multi_arm_bandit
  - reinforcement_learning
  - adversarial_bandit
topics:
  - bandit_problem
  - reinforcement_learning
  - online_learning
name: Multi-Armed Adversarial Bandit
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Multi-Armed Adversarial Bandit

>[!info]
>The **multi-armed bandit problem** is seen as  a reinforcement learning problem with **nonassociative** setting, one that does *not* involve *learning to act* in more than one situation (only a **single state**). 

>[!important] 
>A **$k$-armed bandit problem** is stated as follows:  
>
>Consider the following learning problem. 
>- You are faced **repeatedly** with a **choice** among $k$ different options, or **actions**. 
>- After each choice you **receive** a numerical **reward** chosen from a *stationary probability distribution* that depends on the action you selected. 
>- Your objective is to **maximize** the **expected total reward** *over some time period*, for example, over 1000 action selections, or time steps.

>[!important] Definition
>Let $k > 1$ be the number of **arms**. $\mathscr{P}_{k-1}$ is the set of all *probability distributions* on a set of  $k$ sequences $[k]$
>
>A **$k$-armed adversarial bandit** is described as follow:
>- **Adversary** secretly chooses reward vectors $(x_{1} \,{,}\ldots{,}\,x_{T})$, where $x_{t} := (x_{t,1} \,{,}\ldots{,}\,x_{t, k})\in [0,1]^{k}$. 
>- For $t=1,\,2\,{,}\ldots{,}\,T$:
>	- *learner* selects a **distribution** $$P_{t} \in \mathscr{P}_{k-1}$$
>	- *learner* **samples** an **action** $$A_{t} \sim P_{t}$$
>	- *learner* observes **reward** $$X_{t} = x_{t, A_{t}} = \sum_{i=1}^{k}\,x_{t,i}\mathbb{1}\{A_{t} = i\}$$
>	  

>[!important] Definition
>A **policy** under the $k$-armed bandit setting is a function $$\pi: [k] \times [0,1] \to \mathscr{P}_{k-1}$$ where $\mathscr{P}_{k-1}$ is the set of all *probability distributions* on a set of  $k$ sequences $[k]$.
>
>- A policy $\pi$ maps *history sequence* to *distributions over actions*



>[!important] Definition
>The performance of a policy $\pi$ in *environment* $x = (x_{1} \,{,}\ldots{,}\,x_{T})$ is measured by the **expected regret**, which is the *expected loss* in *cumulative rewards* of the policy relative to the *best fixed action* in *hindsight*.
>
>$$
>R_{T}(\pi, x) :=  \max_{i\in [k]}\sum_{t=1}^{T}x_{t,i} - \mathbb{E}\left[  \sum_{t=1}^{T}x_{t, A_{t}} \right] = \max_{i\in [k]}\sum_{t=1}^{T}x_{t,i} - \mathbb{E}\left[  \sum_{t=1}^{T}\sum_{i=1}^{k}x_{t,i}\mathbb{1}\{A_{t} = i\} \right] 
>$$
>where the *expectation* is over the *randomness* of the learner's choice of action.
>
>The **worst-case regret** over all environments $x$ is defined as
>$$
>R_{T}(\pi) = \sup_{x\in [0,1]^{T \times k}}R_{T}(\pi, x)
>$$ 

- [[Regret for Online Learning]]

## Explanation

>[!important]
>Compared to *supervised learning* where the training samples are used to **instruct** by giving the correct actions, in **reinforcement learning**, training samples are used to **evaluate** the actions taken. 
>
>Purely **evaluative feedback** indicates how good the actions taken was, but not whether or not it was the best or worst action possible, and purely **instructive feedback**, on the other hand, indicates the *correct action* to take, independently of the action *actually taken*. 
>
>
>In their pure forms, these two kinds of feedback are quite distinct: 
>- **evaluative feedback** depends entirely on the action *taken*, 
>- whereas **instructive feedback** is *independent* of the action taken. 
>  
>In other words, 
>- *supervised learning* **enforce** each step to be as **instructed** 
>- whereas the *reinforcement learning* only cares if the **end goal** is *reached*, and does not care the process. 






-----------
##  Recommended Notes and References



- [[Regret for Online Learning]]
- [[No-Regret Learning]]
- [[Online Convex Optimization]]
- [[Online Learnability and Realizabililty Assumption]]


- [[Markov Decision Process]]
- [[Sequential Decision Process]]


- [[Reinforcement Learning An Introduction by Sutton]]
- [[Bandit Algorithms by Lattimore]] pp 127 - 129
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] 
