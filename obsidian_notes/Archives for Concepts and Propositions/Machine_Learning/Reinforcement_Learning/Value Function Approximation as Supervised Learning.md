---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - value_function_approximation
topics:
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
name: Value Function Approximation
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: Value Function Approximation

### Tabular-based and Function Approximation Methods

- [[Tabular Representation and Function Approximation RL]]


>[!important] Definition
>We approximate the **value function** $v_{\pi}: \mathcal{X}\to \mathbb{R}$ under policy $\pi$ by a parametric family $$\mathcal{F}:= \left\{ \hat{v}(\cdot\,;\, w): \mathcal{X}\to \mathbb{R}: \; w\in \mathbb{R}^{d} \right\}.$$
>
>That is, we define a function $\hat{v}: \mathcal{X}\to \mathbb{R}$ *parameterized* by $w\in \mathbb{R}^{d}$
>$$
> \hat{v}(x; w) \approx v_{\pi}(x).
>$$

^ac5adb

### Value Function Approximation as Supervised Learning problem

>[!important]
>**Value-function approximation** problem can be treated as a **supervised learning problem**. 
>
>Note that in supervised learning, we are given a set of covariates-target pairs $$\set{(X_{t}, G_{t})}_{t=1, \ldots, T},$$ the problem is to estimate the function $v: \mathcal{X} \rightarrow \mathbb{R}$ so that $$\| G_{t} - v(X_{t})\|_{2}^{2}$$ is small in expectation. 
> 

^edee92

- [[Supervised Learning and Unsupervised Learning]]

>[!important]
>In RL, 
>- the **target** is defined as the **expected returns** or its *approximation*. 
>- The **covariates** are *states* or *state-action pairs*. 
>
>Given the functional form of value function $v(x, w)$, we listed out the **target definition** of several important algorithms 
> 
>- **Expected returns (Ground Truth)**: $$v_{\pi}(s_{t}):= \mathbb{E}_{ \pi }\left[  G_{t} \,|\, X_{t} = x_{t} \right].$$ The ground truth target is the expected returns given state $x_{t}$ and policy $\pi$ and dynamic $p(x', r| x, a)$.  
> 
>- **Boostrapped expected returns (Dynamic Programming)**: $$v_{\pi}(s, w_{t}) := \mathbb{E}_{ \pi }\left[  R_{t+1}  + \gamma\,v_{\pi}(X_{t+1}, w_{t}) \,|\, X_{t} = x \right].$$ The target depends on expected estimate of *next rewards*, the expected estimate of *value* for *all next states*. 
> 
> 
>- **Sample returns (Monte Carlo methods)}**: $$G_{t} = \sum_{s=1}^{T}\gamma^{s-1}R_{t+s},$$ obtained by *sampling* the entire episode starting at $S_{t}$ and *averaging* all rewards in the process.
> 
>- **Boostrapped sample returns (Temporal difference methods)**: $$\hat{G}_{t} := R_{t+1} + \gamma v_{\pi}(X_{t+1}, w_{t}),$$ i.e. the target depends on both the *next rewards* and the *value estimate* of *next state*.
>

### Prediction Objective 

>[!important] Definition
>The **predictive objective** is the **weighted mean squared error**
>$$
>\ell(w, v_{\pi}) := \sum_{x\in \mathcal{X}}\mu_{x}\,\left[ v_{\pi}(x) - \hat{v}(x, w) \right]^2 
>$$

^08c9a9




## Explanation










-----------
##  Recommended Notes and References

- [[Supervised Learning and Unsupervised Learning]]

- [[Value Function and Bellman Equation for MDP]]
- [[Monte Carlo and Applications]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 197 - 199