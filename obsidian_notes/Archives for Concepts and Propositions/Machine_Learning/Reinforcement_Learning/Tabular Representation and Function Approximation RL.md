---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
topics:
  - reinforcement_learning
name: Tabular Representation and Function Approximation RL
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: Tabular Representation and Function Approximation RL


>[!important]
> There are two groups of RL methods based on how the value function are represented and stored

>[!important]
>- **Tabular methods**: The value function is stored as a table, i.e. for each $x$, there is a value $v(x)$ (or $q(x,a)$ for each pair $(x,a)$ ) in the table. 
>	- The tabular representation has *good* **discriminization** but *no* **generalization**. 
>	- In other words, *value* for each *state* is stored and updated **independently**, so the **dimension** of the representation for the tabular value function is $|\mathcal{X}|$ for $v$ and $|\mathcal{X}| \times |\mathcal{A}|$ for $q$. 
>	- Also it cannot be applied to applications where the total set of states $|\mathcal{X}|$ is large. (The **curse of dimensionality**)

- [[Reinforcement Learning]]
- [[Value Function and Bellman Equation for MDP]]
- [[Bellman Optimality Equation for MDP]]
- [[Temporal Difference Learning]]


>[!important]
>- **Function approximation methods**: The value function is *parameterized*. 
>	- The function approximation allows us to represent the value function via its **low dimensional paramater** $d \ll |\mathcal{X}|$, which is *more efficient* in representation and storage, esp. when *state-space* $\mathcal{X}$ is very large. 
>	- On the other hand, the *value* for **all states** are *affected* by the change of parameter. 
>	- It will *reduce* the **discriminization** in order to *gain* **generalization**. 
>	- As its name suggests, the value function estimated via function approximation is **not exact** but approximation.
>

- [[Value Function Approximation as Supervised Learning]]

### Discriminization and Generalization

>[!important]
>In discussion above, we listed out two important concepts for value estimation:
> 
>-  **Generalization**, which means *updating* value of *one state* would *affect* the value of *other states*. That is, the change *generalizes* from that state to affect the values of many other states. Aggregate all states would easily achieve high generalization but with no discrimination. 
> 
>- **Discriminization**, which means the ability to make the value of *two states different*. If value of each states are represented *independently*, such as tabular methods, the discrimination is maximized but there is no generalization. 
> 
>A good value estimation method need to have good generalization and good discrimination. 


## Explanation






-----------
##  Recommended Notes and References


- [[Value Function Approximation as Supervised Learning]]
- [[Local Probabilistic Models]]


- [[Value Function and Bellman Equation for MDP]]
- [[Markov Decision Process]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 198
- [[An Introduction to Deep Reinforcement Learning by Francois-Lavet]]