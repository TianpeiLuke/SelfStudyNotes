---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/sequential_models
  - machine_learning/dynamic_system
keywords:
  - dynamic_bayesian_network
topics:
  - machine_learning_models
  - machine_learning_theory
  - probabilistic_graphical_model
  - dynamic_system
name: Dynamic Bayesian Network
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Dynamic Bayesian Network

>[!important] Definition
>A **2-time-slice Bayesian network (2-TBN)** for a process over $\mathcal{X}$ is a conditional Bayesian network over $X'$ given $X_{I}$ where $X_{I} \subseteq \mathcal{X}$ is a set of **interface variables**.
>- In a conditional Bayesian network, only the variables $X'$ have *parents* or CPDs.
>- The interface variables $X_{I}$ are those variables whose *values* at time $t$ have a *direct effect* on the variables at *time* $t + 1$.
>  
>The **2-TBN** represents the conditional distribution
>$$
>\mathcal{P}(X' | X_{I}) = \prod_{i=1}^{n}\mathcal{P}\left( X_{i}' | X_{Pa(i)}' \right)
>$$

- [[Markov Chain and Markov Process]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[Stochastic Process]]
- [[Autoregressive Models]]

>[!important] Definition
>In a *2-TBN*, there are two types of edges
>- **inter-time-slice edges**: that points from time slice $t$ to time slice $t+1$
>	- The edges like $X_{i}^{(t)} \to X_{i}^{(t+1)}$ are called the **persistence edges**; 
>		- they represent the tendency of the variable $X_{i}$ (for example, sensor failure) to *persist over time* with high probability.
>		- A variable $X_{i}$ in a persistence edge is called a **persistent variable**.
>- **intra-time-slice edges**: connecting variables in the *same time slice*. 



>[!important] Definition
>A **dynamic Bayesian network (DBN)** is a pair $\left\langle \mathcal{B}_{0}, \mathcal{B}_{\rightarrow} \right\rangle$, where 
>- $\mathcal{B}_{0}$ is a *Bayesian network* over $X^{(0)}$, representing the *initial distribution* over states, and 
>- $\mathcal{B}_{\rightarrow}$ is a *2-TBN* for the process. 
>  
>For any desired time span $T \ge 0$, the distribution over $X^{(0:T)}$ is defined as a **unrolled Bayesian network**, where, for any $i = 1 \,{,}\ldots{,}\, n:$ 
>- the *structure* and *CPDs* of $X_{i}^{(0)}$  are the *same* as those for $X_{i}$ in $\mathcal{B}_{0}$, 
>- the *structure* and *CPD* of  $X_{i}^{(t)}$ for $t > 0$ are the *same* as those for $X_{i}^{'}$ in $\mathcal{B}_{\rightarrow}$. 
>  
>Thus, we can view a **DBN** as a compact representation from which we can generate an *infinite* set of Bayesian networks (one for every $T > 0$). 

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Local Probabilistic Models]]


## Explanation

>[!info]
>A **2-TBN** represents a **template factor**, which will be instantiated  multiple times within the model, for multiple variables $X_{i}^{(t)}$ and their parents.

- [[Local Probabilistic Models]]

>[!info]
>A *2-TBN* defines the conditional distribution 
>$$
>\mathcal{P}(X^{(t+1)} \,|\, X^{(t)}), \quad t = 0,\,1,\,{,}\ldots{,}\,
>$$

- [[Markov Transition Kernel and Transition Function]]

## Hidden Markov Model

![[dbn_hmm.png]]


- [[Hidden Markov Model]]

## Prediction, Filtering, Smoothing Tasks

- [[Statistical Prediction Filtering and Smoothing for State Observation Model]]



-----------
##  Recommended Notes and References


- [[Kalman Filter Continuous-Time]]
- [[Extended Kalman Filter]]
- [[State-Observation Models]]
- [[Linear Dynamic System]]


- [[Hidden Markov Model]]
- [[Sequential Importance Sampling]]


- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[Gaussian Bayesian Network]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 202 - 204
- [[Artificial Intelligence Modern Approach by Russell]]