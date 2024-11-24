---
tags:
  - concept
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/inference
keywords:
  - maximum_a_posteriori_probability
  - hidden_markov_model
  - viterbi_algorithm
topics:
  - probabilistic_graphical_model
name: Hidden Markov Model MAP Inference via Viterbi Algorithm
date of note: 2024-09-01
---

## Concept Definition

>[!important]
>**Name**: Hidden Markov Model MAP Inference via Viterbi Algorithm

![[State-Observation Models#^dc6850]]

![[Hidden Markov Model#^f3f54e]]

- [[Hidden Markov Model]]


>[!important] Definition
>Our goal is to find the  **maximum a posteriori probability** (**MAP**) **estimate** of hidden states $X^{(1:T)}$ given observations $O^{(1:T)}$:
>$$
>\begin{align*}
> X^{(1:T), *} = \arg\max_{x^{(1:T)}} \mathcal{P}(x^{(1:T)} \;|\; O^{(1:T)} )
>\end{align*}
>$$
>
>We can decompose the log-conditional-probability as 
>$$
>\begin{align*}
> &\arg\max_{x^{(1:T)}} \mathcal{P}(x^{(1:T)} \;|\; O^{(1:T)} ) \\[5pt]
> &= \arg\max_{x^{(1:T)}} \log \mathcal{P}(x^{(1:T)} \;|\; O^{(1:T)} ) \\[5pt]
> &= \arg\max_{x^{(1:T)}} \log \pi_{1}(x^{(1)}) + \log \lambda_{1}(x^{(1)}) + \sum_{t=2}^{T}\left[ \log A(x^{(t-1)}, x^{(t)}) + \log \lambda_{t}(x^{(t)}) \right] 
>\end{align*}
>$$
>where 
>- $\pi_{1}(x^{(1)})$ is the *initial prior probability* for state:  $$\pi_{1}(x^{(1)}) = \mathcal{P}(X^{(1)} = x^{(1)})$$
>- $\lambda_{t}(x^{(t)})$ is the *local evidence* $$\lambda_{t}(x^{(t)}) := \mathcal{P}(O^{(t)}\;|\;X^{(t)} = x^{(t)})$$
>- $A(x^{(t-1)}, x^{(t)})$ is the *Markov transition matrix*  $$A(x^{(t-1)}, x^{(t)}) := \mathcal{P}(X^{(t)} = x^{(t)} \;|\;X^{(t-1)} = x^{(t-1)})$$

- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]
- [[Hidden Markov Model]]

### Viterbi Algorithm

>[!important] Definition
>The **Viterbi algorithm** perform exact MAP inference via dynamic programming. 
>
>It consists of two passes:
>- The **forwards pass** recursively computes the **message** $$\delta_{t}(j) := \max_{x^{(1: t-1)}}\mathcal{P}(x^{(1: t-1)}, X^{(t)} = j, O^{(1:t)} )$$ based on *local evidence* $\lambda_{t}$, and *transition matrix* $A(i,j)$
>	- The **key insight** is that the *most probable path to state* $j$ at time $t$ **must consist** of the *most probable path* to $i$ at time $t-1$ $$\delta_{t}(j) = \lambda_{t}(j)\left[ \max_{i}\,\delta_{t-1}(i)\,A_{i,j} \right] $$ This is the **Bellman equation**.
>	- We also keep track of the *most likely previous states* (*ancestor*) $$a_{t}(j) := \arg\max_{i}\delta_{t-1}(i)A_{i,j}$$
>- The **backwards pass** recursively retrieves the most likely previous state using a **traceback procedure** $$X^{(t), *} = a_{t+1}(X^{(t+1), *})$$

- [[Max-Product Variable Elimination]]
- [[Bellman Optimality Equation for MDP]]

![[viterbi_decoding.png]]

>[!quote]
>This is equivalent to computing a shortest path through the **trellis diagram** in Figure 9.5, where the nodes are possible states at each time step, and the node and edge weights are *log probabilities*. This can be computed in $O(T\,K^2)$ time.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 403


### Forwards Pass

>[!important] Definition
>The **forwards pass** for **Viterbi algorithm** is described as follows
>- *Require*: the *state transition matrix* $A = [A_{i,j}]$
>- *Require*: the *local evidence* $\lambda_{t}(i)$ for all $i\in \mathcal{X}$ and $t=1\,{,}\ldots{,}\,T$
>- *Require*: the initial state probability $\pi(i) = \mathcal{P}(X^{(1)}= i)$
>- *Initialize* the message $$\delta_{1}(j) = -\log\pi(j)\,- \log \lambda_{1}(j)$$
>- For $t=2 \,{,}\ldots{,}\,T$
>	- *Update* the **message** for all $j\in \mathcal{X}$ $$\delta_{t}(j) = -\log\lambda_{t}(j) + \min_{i}\,\left[\delta_{t-1}(i)  -\log A_{i,j} \right] $$
>	- Find the *most probable* **ancestor state** for each $j\in \mathcal{X}$ $$a_{t}(j) = \arg\min_{i} \left[\delta_{t-1}(i)  -\log A_{i,j} \right]$$
>		- That is, $a_{t}(j)$ stores the identity of the *previous state* on the **most probable path** to $X^{(t)} = j$.

- [[Softmax Function and Log-Sum-Exp Function]]

### Backwards Pass

>[!important] Definition
>The **backwards pass** for **Viterbi algorithm** is described as follows
>- *Require*: the *state transition matrix* $A = [A_{i,j}]$
>- *Require*: the *local evidence* $\lambda_{t}(i)$ for all $i\in \mathcal{X}$ and $t=1\,{,}\ldots{,}\,T$
>- *Require*: the max-margin **messages** $\delta_{t}(j)$ for each state and time
>- *Require*: the *trace* of **ancestor states** $a_{t}(j)$ on the most probable path to state $X^{(t)} =j$  
>- Find the optimal assignment at $T$ $$X^{(T), *} = \arg\max_{i}\,\delta_{T}(i)$$
>- For $t=T-1 \,{,}\ldots{,}\,1$
>	- **Traceback**:  Retrieve the *most probable previous state* given the optimal current assignment  $$X^{(t), *} = \arg\max_{i}\,a_{t+1}(X^{(t+1), *})$$


## Explanation

>[!important] 
>The **Viterbi algorithm** is a special case of the **max-product belief propagation algorithm** for HMM.
>
>This is a **dynamic programming algorithm**.

- [[Dynamic Programming Algorithms]]
- [[Max-Product Belief Propagation for Clique Tree]]

>[!important] Definition
>The **Viterbi algorithm** is also called the **Viterbi decoding** as finding the MAP estimate is the process of *decoding*.

>[!info]
>In contrast to the **Viterbi decoding**, an alternative method is the **greedy decoding** such as the **beam search.**

- [[Beam Search as Greedy Decoding]]

## Time and Space Complexity

>[!quote]
>The **time complexity** of **Viterbi** is clearly $O(K^2T)$ in general, and the **space complexity** is $O(KT)$, both the same as **forwards-backwards**. If the transition matrix has the form $$A_{i,j} \propto  \rho(x_{j} − x_{i}),$$ where $x_{i}$ is the *continuous vector* represented by state $i$ and $\rho(u)$ is some scalar cost function, such as Euclidean distance, we can implement Viterbi in *$O(T K)$ time*, by using the generalized distance transform to implement Equation.
>
>--[[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 405

- [[Hidden Markov Model Inference via Forward-Backward Algorithm]]



-----------
##  Recommended Notes and References


- [[State-Observation Models]]
- [[Hidden Markov Model]]
- [[Hidden Markov Model Inference via Forward-Backward Algorithm]]

- [[Maximum A Posteriori Probability Query of Graphical Model]]
- [[Max-Product Belief Propagation for Clique Tree]]


- [[Probabilistic Graphical Models by Koller]] pp 363
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 15 - 19
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 403 - 404
- [[Deep Learning Foundations and Concepts by Bishop]] pp 480
- [[Elements of Statistical Learning by Hastie]]
- [[Artificial Intelligence Modern Approach by Russell]]
- [[Speech and Language Processing by Jurafsky]] pp 373