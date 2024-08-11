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

### Eligibility Trace

>[!important] Definition
>In TD($\lambda$), the **eligibility trace** vector is initialized with zero at the *beginning of the episode*; and it is incremented on each time by the *value gradient*, with *decay* $\gamma\,\lambda$ 
>$$
>\begin{align*}
> z_{-1} &= 0 \\[5pt]
> z_{t} &= \gamma\,\lambda\,z_{t-1} + \nabla \hat{v}(X_{t}, w_{t}), \quad 0 \le t\le T.
>\end{align*}
>$$
>where $\gamma >0$ is the *discount rate,* and $\lambda \in [0,1]$ is the parameter determine the *$\lambda$-return.* 

- [[Eligibility Traces]]

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
>The *eligibility trace vector* **put more attention** the TD error in the update when the trace vector is high.

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


- [[lambda-Return and Compound Update]]
- [[Temporal Difference Learning]]
- [[Eligibility Traces]]
- [[Returns and Goals of Reinforcement Learning]]
- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]






- [[Value Function and Bellman Equation for MDP]]
- [[Monte Carlo and Applications]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 292 - 293