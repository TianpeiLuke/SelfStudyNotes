---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - eligibility_traces
topics:
  - reinforcement_learning
name: Eligibility Traces
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Eligibility Traces

>[!important] Definition
>The **eligibility traces** provides a mechanism of 
>- a **short-term memory** vector $z_{t}\in \mathbb{R}^d$ that parallels
>- the *long-term weight* vector $w_{t}\in \mathbb{R}^d$

- [[Gradient Monte Carlo Method for Value Function Approximation]]
- [[Semi-Gradient Temporal Difference]]

>[!info]
>The rough **idea** is that when a *component* of $w_{t}$ participates in *producing an estimated value*, then the corresponding component of $z_t$ is *bumped up* and then begins to *fade away*. 
>
>**Learning** will then occur in that component of $w_t$ if a **nonzero TD error** occurs **before** the *trace falls back to zero*. 
>- The **trace-decay parameter** $\gamma \in [0, 1]$ determines the *rate* at which the trace falls.


## Forward View and Backward View

>[!important] Definition
>Many algorithms are most naturally formulated and understood as an **update** of a state’s value based on *events* that **follow that state** *over multiple* **future time steps**.
>
>Such formulations, based on *looking forward* from the updated state, are called **forward views**.

- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]
- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]
- [[Multi-Step SARSA Algorithm On-Policy]]

![[forward_view.png]]


>[!info]
>Forward views are always somewhat complex to implement because the update depends on later things that are not available at the time.

>[!important] Definition
>it is often possible to achieve nearly the same updates—and sometimes exactly the same updates—with an algorithm that uses the *current TD error*, *looking backward* to *recently visited states* using an **eligibility trace**. 
>
>These alternate ways of looking at and implementing learning algorithms are called **backward views**.

![[backward_view.png]]


## Explanation

>[!quote]
>**Eligibility traces** are one of the basic mechanisms of reinforcement learning. For example, in the popular **TD$(\lambda)$ algorithm**, the refers to the use of an eligibility trace. Almost any temporal-difference (TD) method, such as *$Q$-learning* or *Sarsa*, can be combined with eligibility traces to obtain a more general method that may learn more *efficiently*.
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 287

- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]

>[!info]
>The idea of eligibility traces is to add a **short-term memory** on the *previous visited state-action pairs*.
>- The memory **decay exponentially** over time;
>- The trace keep track of **all state-action pairs**
>	- the *visited* state-action pair increments in the trace
>	- the *unvisited* state-action pair *decay* by factor $\lambda$.


### Between TD and Monte Carlo

>[!quote]
>**Eligibility traces** *unify* and *generalize* **TD** and **Monte Carlo methods**. When TD methods are augmented with eligibility traces, they produce a family of methods spanning a spectrum that has *Monte Carlo methods* at one end ($\lambda = 1$) and *one-step TD methods* at the other ($\lambda = 0$). ... Eligibility traces also provide a way of implementing **Monte Carlo methods online** and on continuing problems *without episodes*.
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 287

- [[Temporal Difference Learning]]
- [[Monte Carlo Prediction for Value Estimation]]
- [[Off-Policy Monte Carlo Prediction with Importance Sampling]]

### Compare to multi-step TD

>[!quote]
>Of course, we have already seen one way of unifying TD and Monte Carlo methods: the **$n$-step TD methods** of Chapter 7. What **eligibility traces** offer beyond these is an elegant **algorithmic mechanism** with significant *computational advantages*.
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 287

- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]
- [[Multi-Step SARSA Algorithm On-Policy]]
- [[Multi-Step SARSA Algorithm Off-Policy]]

>[!quote]
>The primary **computational advantage** of *eligibility traces* over *n-step methods* is that only **a single trace vector** is required rather than a store of the *last n feature vectors*.
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 287







-----------
##  Recommended Notes and References


- [[lambda-Return and Compound Update]]
- [[Temporal Difference lambda Algorithm]]
- [[Multi-Step Truncated lambda-Return Method]]


- [[Temporal Difference Learning]]
- [[Markov Decision Process]]
- [[Prediction and Control Problems in Reinforcement Learning]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 287 
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1149 - 1150
- [[Foundations of Machine Learning by Mohri]]