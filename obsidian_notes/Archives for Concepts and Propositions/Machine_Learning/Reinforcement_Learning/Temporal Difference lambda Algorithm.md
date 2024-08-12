---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - temporal_difference_lambda_learning
  - eligibility_traces
topics:
  - reinforcement_learning/algorithm
name: Temporal Difference lambda Algorithm
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: TD($\lambda$) Algorithm

![[lambda-Return and Compound Update#^63443d]]

- [[lambda-Return and Compound Update]]

## Eligibility Trace for Tabular Value Representation

>[!important] Definition
>In TD($\lambda$), define the **eligibility trace** as a real-valued function for each state. That is,
>$$
>x\to e(x) \in \mathbb{R}
>$$
>
>
>Given state $X_{t}$ at time $t$,  the **update rule** for *eligibility trace*  is
>$$
>\begin{align*}
> e_{t}(X_{t}) &= e_{t-1}(X_{t}) + 1 \\[5pt]
> e_{t}(x) &= \lambda\,e_{t-1}(x) \quad \forall x \neq X_{t}
>\end{align*}
>$$

^cba720

>[!important] Definition
>The **TD($\lambda$) update rule** for *state-value function* given **eligibility trace** $e(x, a)$ is defined as
>$$
> \begin{align}
> V_{t+1}(x) &\leftarrow  V_{t}(x) + \alpha_{t}\left(R_{t+1} + \gamma V_{t}(X_{t+1})  - V_{t}(X_{t})\right)\;e_{t}(x) \\[5pt]
>&=   V_{t}(x) + \alpha_{t}\,\delta_{t}\,e_{t}(x), \quad \forall x\in \mathcal{X}
> \end{align} 
>$$
>Note that, 
>- unlike the *TD(0) update rule* which only update the value for *observed states*, the *TD($\lambda$) update rule* applies to *unobserved states* too.
>- the TD($\lambda$) propagate the **TD error** based on *observed value* to *unobserved state*
>
>- For observed state $X_{t}$,
>$$
> \begin{align}
> V_{t+1}(X_{t}) &\leftarrow  V_{t}(X_{t}) + \alpha_{t}\left(R_{t+1} + \gamma V_{t}(X_{t+1})  - V_{t}(X_{t})\right)\;e_{t}(X_{t}) \\[5pt]
>&=   V_{t}(X_{t}) + \alpha_{t}\,\delta_{t}\,e_{t}(X_{t})
> \end{align} 
>$$
>where $\delta_{t}$ is the **TD error** $$\delta_{t} := R_{t+1} + \gamma V_{t}(X_{t+1})  - V_{t}(X_{t}).$$
>- For unobserved state $x\neq X_{t}$
>$$
>V_{t+1}(x) \leftarrow V_{t}(x) + \alpha_{t}\,\delta_{t}\,\lambda\,e_{t-1}(x)
>$$


###  TD($\lambda$) Algorithm for Tabular Representation

>[!important] Definition
>The **tabular-based TD($\lambda$) algorithm** is described as below:
>- *Require*: policy $\pi$
>- *Require*: step size $\alpha >0$, discount factor $\gamma \in (0,1)$
>- *Require*: decay parameter $\lambda \in [0,1]$
>- *Initialize* **table for state-value function** $V_{0}(x)$ for all $x\in \mathcal{X}$. 
>	- Note that the **terminal state** $V_{0}(x_{\text{terminal}}) = 0$
>- For **episode** $k=1,\,2\,{,}\ldots{,}\,$:
>	- Initialize state $X_{0}$
>	- Initialize *eligibility trace* $e_{-1}(x) = 0$ for all state $x\in \mathcal{X}$
>	- For step $t=0,\,1\,{,}\ldots{,}\,T$:
>		- Generate a **sample action** according to *policy* $\pi$ and *current state* $$A_{t} \sim \pi(\cdot| X_{t})$$
>		- Take action $A_{t}$
>		- Observe **reward** $R_{t}$ and **next state** $X_{t+1}$
>		- Compute the **temporal difference error** $$\delta_{t} = R_{t} + \gamma\,V_{t}(X_{t+1}) - V_{t}(X_{t})$$
>		- Update **eligibility trace** for *observed state* $$e_{t}(X_{t}) = e_{t-1}(X_{t}) + 1$$ 
>			- Set eligibility trace of *unobserved state* as the same $e_{t}(x) = e_{t-1}(x)$ for $x\neq X_{t}$
>		- For all state $x\in \mathcal{X}$
>			- Update value function for **all state** (not just observed state) using **TD error** with **eligibility trace** $$V_{t+1}(x) = V_{t}(x) + \alpha\,\delta_{t}\, e_{t}(x)  $$
>			- Update the *eligibility trace* with **$\lambda$-decay** $$e_{t}(x) \leftarrow  \gamma\,\lambda\,e_{t}(x)$$

- [[Temporal Difference Learning]]



## Eligibility Trace for Semi-Gradient Algorithm

>[!important] Definition
>In *semi-gradient TD($\lambda$)*, the **eligibility trace** vector is initialized with zero at the *beginning of the episode*; and it is incremented on each time by the *value gradient*, with *decay* $\gamma\,\lambda$ 
>$$
>\begin{align*}
> z_{-1} &= 0 \\[5pt]
> z_{t} &= \gamma\,\lambda\,z_{t-1} + \nabla \hat{v}(X_{t}, w_{t}), \quad 0 \le t\le T.
>\end{align*}
>$$
>where $\gamma >0$ is the *discount rate,* and $\lambda \in [0,1]$ is the parameter determine the *$\lambda$-return.* 
>
>This *eligibility trace* defined above is called the **accumulating trace**.

- [[Eligibility Traces]]
- [[Reinforcement Learning An Introduction by Sutton]] pp 301

### Semi-Gradient TD($\lambda$) Update

![[Semi-Gradient Temporal Difference#^5680d7]]

>[!important] 
>The **temporal difference error** for approximated value function is 
>$$
>\delta_{t} := R_{t+1} + \gamma \,\hat{v}(X_{t+1}, w_{t}) - \hat{v}(X_{t}, w_{t}).
>$$

>[!important] Definition
>The **TD($\lambda$) update** based on the *TD error* and the *eligibility trace vector* is 
>$$
>\begin{align*}
> w_{t+1} &= w_{t} + \alpha\,\left[ R_{t+1} + \gamma\,  \hat{v}(X_{t+1}, w_{t})  - \hat{v}(X_{t}, w_{t}) \right]\;  z_{t} \\[5pt]
> &= w_{t} + \alpha\,\delta_{t}\,z_{t}
>\end{align*}
>$$
>Using *eligibility trace vector*, we are allowed to **put more attention** to the *component* of TD error $\delta_{t}(i)$ when that component has the *high trace* $z_{t}(i)$.

- [[Semi-Gradient Temporal Difference]]

### Semi-Gradient TD($\lambda$) Algorithm

>[!important] Definition
>The **Semi-Gradient TD($\lambda$)** algorithm is described as the followings:
>- *Require*: the *policy* $\pi$ in evaluation
>- *Require*: approximate value function $\hat{v}(\cdot; w): \mathcal{X} \to \mathbb{R}$ parameterized by $w\in \mathbb{R}^d$ and is *differentiable* in $w$. Set $\hat{v}(\text{terminal}; w) = 0$ for all $w$
>- *Require*: step size $\alpha >0$
>- *Require*: **trace decay rate** $\lambda\in [0,1]$
>- *Initialize* $w_{0}\in \mathbb{R}^d$
>- For *episode* $k=1 \,{,}\ldots{,}\,$
>	- Initialize state $X_{0}$
>	- Initialize $z_{-1} = 0$
>	- For $t=0\,{,}\ldots{,}\,T-1$
>		- Choose and take *action* $$A_{t} \sim \pi(\cdot\,|\,X_{t})$$
>		- Observe *reward* $R_{t+1}$ and *next state* $X_{t+1}$
>		- Compute the **eligibility trace vector** $$z_{t} = \gamma\,\lambda\,z_{t-1} + \nabla \hat{v}(X_{t}, w_{t})$$
>		- Compute the **temporal difference error** $$\delta_{t} = R_{t+1} + \gamma \,\hat{v}(X_{t+1}, w_{t}) - \hat{v}(X_{t}, w_{t})$$
>		- Update **parameter** for value function using **SGD** on **TD error** $$\begin{align*}w_{t+1} &=  w_{t} + \alpha\,\left[ R_{t+1} + \gamma\,  \hat{v}(X_{t+1}, w_{t})  - \hat{v}(X_{t}, w_{t}) \right]\;  z_{t}\\[5pt]&=w_{t} + \alpha\,\delta_{t}\,z_{t} \end{align*}$$

- [[Semi-Gradient Temporal Difference]]


### Backward View

>[!info]
>$$
>\begin{align*}
> w_{t+1} &= w_{t} + \alpha\,\left[ R_{t+1} + \gamma\,  \hat{v}(X_{t+1}, w_{t})  - \hat{v}(X_{t}, w_{t}) \right]\;  z_{t} \\[5pt]
> &= w_{t} + \alpha\,\delta_{t}\,z_{t} \\[5pt]
> &= w_{t} + \alpha\, \delta_{t}\, \sum_{s=0}^{t}\left(\lambda\,\gamma\right)^{t-s}\;\nabla \hat{v}(X_{s}, w_{s}) \\[5pt]
> &= w_{t} + \alpha\, \sum_{s=0}^{t}\left(\lambda\,\gamma\right)^{t-s}\;\left[ \delta_{t}\,\nabla \hat{v}(X_{s}, w_{s})   \right]
>\end{align*}
>$$
>If a state $X'$ has appeared **multiple times in the past**, it will has **higher contribution** to the *eligibility trace* $z_{t}$  since the state-value will change a lot.  
>
>The total contribution of a specific state $X'$ in the *eligibility trace* $z_{t}$ is
>$$\delta_{t}\,\sum_{s\in T'}\left(\lambda\,\gamma\right)^{t-s}\;\nabla \hat{v}(X', w_{s}) $$ where $T' = \{ t: X_{t} = X' \}$




![[backward_view.png]]

>[!quote]
>TD($\lambda$) is **oriented backward in time**. At each moment we look at the **current TD error** and **assign it backward** to each *prior state* according to how much that state contributed to the current eligibility trace at that time. We might imagine ourselves riding along the stream of states, computing TD errors, and shouting them back to the previously visited states, as suggested by Figure 12.5. Where the *TD error* and *traces* come together, we get the update given by (12.7), **changing the values** of those **past states** for when they **occur again in the future**.
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 294




## Explanation

>[!quote]
>**TD($\lambda$)** improves over the **offiine $\lambda$-return algorithm** in three ways. **First** it updates the weight vector on *every step* of an episode rather than *only at the end*, and thus its estimates may be better *sooner*. **Second**, its *computations* are *equally distributed* in time rather than all at the end of the episode. And **third**, it can be applied to *continuing problems* rather than just to episodic problems. In this section we present the **semi-gradient** version of **TD($\lambda$) with function approximation**.
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 292

>[!quote]
>With function approximation, the **eligibility trace** is a vector $z_{t} \in \mathbb{R}^d$ with the *same number of components* as the *weight vector* $w_{t}$. Whereas the weight vector is a **long-term memory**, accumulating over the lifetime of the system, the *eligibility trace* is a **short-term memory**, typically lasting less time than the length of an episode. Eligibility traces assist in the learning process; their only consequence is that they *affect the weight vector*, and then the weight vector determines the estimated value.
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 292






-----------
##  Recommended Notes and References


- [[Multi-Step Truncated lambda-Return Method]]

- [[lambda-Return and Compound Update]]
- [[Temporal Difference Learning]]
- [[Eligibility Traces]]
- [[Returns and Goals of Reinforcement Learning]]
- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]






- [[Value Function and Bellman Equation for MDP]]
- [[Monte Carlo and Applications]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 292 - 293