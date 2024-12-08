---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/sequential_models
  - statistics/signal_processing
  - machine_learning/dynamic_system
keywords:
  - state_space_model
  - linear_dynamic_system
topics:
  - machine_learning_models
  - probabilistic_graphical_model
  - dynamic_system
name: State Space Models and Nonlinear Dynamic System
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: State Space Models and Nonlinear Dynamic System

### Linear Dynamic System

![[Linear Dynamic System#^78b0f0]]

![[Linear Dynamic System#^90435d]]

- [[Linear Dynamic System]]
- [[Ordinary Differential Equations]]

### State-Space Model as Nonlinear Dynamic System

>[!important] Definition
>A **state-space model (SSM)** is a *partially observed Markov model*, in which the hidden state, $x_{t}$, evolves over time according to a *Markov process*, and each hidden state generates some observations $y_{t}$ at each time step.
>
>An SSM can be represented by a *stochastic nonlinear dynamic system*
>$$
>\left\{
>\begin{align*}
> \frac{d}{dt} x(t) &= f(x(t), u(t), \xi(t)) \\[5pt]
> y(t) &= h(x(t), u(t), y(t-1) \,{,}\ldots{,}\, y(1), \zeta(t))
>\end{align*} \right.
>$$
>where
>- $x(t) \in \mathbb{R}^{n}$ is the *hidden* **state vector**;
>- $y(t) \in \mathbb{R}^{m}$ is called an **observation vector**;
>- $u(t) \in \mathbb{R}^{p}$ is called an **input vector** or **control vector**.
>- $f$ is called the **(state) transition function**
>- $h$ is called the **observation function**
>- $(\xi(t))_{t}$ is the **process noise**
>- $(\zeta(t))_{t}$ is  the **observation noise**

^4beaac

- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]


## Explanation

>[!info]
>A *state-space model* can be viewed as a **dynamic Bayesian network** 

- [[Dynamic Bayesian Network]]

>[!info]
>A *state-space model* is a standard model in **modern control theory**.



## State-Observation Models

![[State-Observation Models#^dc6850]]

>[!important] Definition
>The **discrete-time linear time-invariant (LTI) system** can be formulated as a **state-observation model** where
>- the *transition model* is defined by the *Gaussian distribution* $$\mathcal{P}(X_{t+1} | X_{t}) = \mathcal{N}(AX_{t};  \Sigma_{X}),$$
>- the *observation model* is defined by the *Gaussian distribution* $$\mathcal{P}(Y_{t} | X_{t}) = \mathcal{N}(CX_{t};  \Sigma_{O}).$$
>  
>We can see this when
>-  the *control vector* $U_{t}$ are assumed to be *i.i.d.* for all $t$ 
>- $U_{t} \sim \mathcal{N}(0,I)$ are assumed to be a *Gaussian while noise vector*
>- $U_{t} \perp X_{t}$ for all $t$

- [[State-Observation Models]]
- [[Gaussian Random Vector]]
- [[Statistical Prediction Filtering and Smoothing for State Observation Model]]

## Stochastic Control and Stochastic Differential Equation

>[!important] 
>In *stochastic control*, we assume that the control process $(U(t), t\ge 0)$ is a *Gaussian white noise*. 
>
>We can formulate the *continuous-time* linear dynamic system using **(homogeneous) stochastic differential equation**
>$$
>\left\{
>\begin{align*}
> dX(t) &= A\left( X(t)\right)\,dt + B\left( X(t)\right)\,dW(t) \\[5pt]
> dY(t) &= C\left( X(t)\right)\,dt + D\left( Y(t)\right)\,dW(t) 
>\end{align*} \right.
>$$

- [[Homogeneous Linear Stochastic Differential Equation]]
- [[Stochastic Differential Equations]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 379


## Recurrent Neural Network

- [[Recurrent Neural Network]]
- [[Long-Short Term Memory Network or LSTM]]
- [[Gated Recurrent Units in Neural Network]]



-----------
##  Recommended Notes and References


- [[Hidden Markov Model]]
- [[Extended Kalman Filter]]
- [[Sequential Importance Sampling]]
- [[Particle Filter or Sampling-Importance-Resampling]]
- [[Linear Dynamic System]]



- [[Dynamic Bayesian Network]]
- [[Markov Chain Monte Carlo Methods]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Probabilistic Graphical Models by Koller]] pp 211 - 222
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 969 - 970
- [[Deep Learning Foundations and Concepts by Bishop]] pp 352
- [[Introduction to Stochastic Calculus by Klebaner]] pp 379
- Wikipedia [State-space_representation](https://en.wikipedia.org/wiki/State-space_representation)