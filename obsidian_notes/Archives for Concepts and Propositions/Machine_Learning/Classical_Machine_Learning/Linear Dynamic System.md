---
tags:
  - concept
  - machine_learning/models
  - statistics/signal_processing
  - probabilistic_graphical_models/sequential_models
  - machine_learning/dynamic_system
keywords:
  - state_space_model
  - linear_dynamic_system
  - linear_time_invariant_system
topics:
  - machine_learning_models
  - dynamic_system
  - probabilistic_graphical_model
name: Linear Dynamic System
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Linear Dynamic System

### Linear Dynamic System

>[!important] Definition
>In *control theory*, a **continuous-time linear dynamic system** is defined by the following system of ordinary differential equations
>$$
>\left\{
>\begin{align*}
> \frac{d}{dt} x(t) &= A(t)\,x(t) + B(t)\,u(t) \\[5pt]
> y(t) &= C(t)\,x(t) + D(t)\,u(t)
>\end{align*} \right.
>$$
>where
>- $x(t) \in \mathbb{R}^{n}$ is called a **state vector**;
>- $y(t) \in \mathbb{R}^{m}$ is called an **observation vector**;
>- $u(t) \in \mathbb{R}^{p}$ is called an **input vector** or **control vector**.
>- $A(t) \in \mathbb{R}^{n\times n}$ is called the **system matrix** or **state matrix**
>- $B(t) \in \mathbb{R}^{n\times p}$ is called the **input matrix**
>- $C(t) \in \mathbb{R}^{m\times n}$ is called the **output matrix**
>- $D(t) \in \mathbb{R}^{m\times p}$ is called the **feedforward (feed-through) matrix**
>  
>The dynamic system above is characterized by the state space $(y(t), x(t))$, which is called the **state-space model**.

^78b0f0

- [[Ordinary Differential Equations]]
- [[Autoregressive Models]]

#### Linear Time Invariant System

>[!important] Definition
>A **linear time-invariant (LTI) system** is a linear dynamic system where all transition matrices are *time-invariant*, (i.e. the ODE is *time-homogeneous*)
>$$
>\left\{
>\begin{align*}
> \frac{d}{dt} x(t) &= A\,x(t) + B\,u(t) \\[5pt]
> y(t) &= C\,x(t) + D\,u(t)
>\end{align*} \right.
>$$


- [[Homogeneous Linear Differential Equations]]
- [[Time-Homogeneous Markov Process]]
- [[Homogeneous Linear Stochastic Differential Equation]]
- [[Stationary Process]]

#### Discrete-Time Linear Dynamic System

>[!important] Definition
>A **discrete-time linear dynamic system** is defined by the following equations
>$$
>\left\{
>\begin{align*}
> X_{t+1} &= A(t)\,X_{t} + B(t)\,U_{t} \\[5pt]
> Y_{t} &= C(t)\,X_{t} + D(t)\,U_{t}
>\end{align*} \right.
>$$
>
>A **discrete-time linear time-invariant (LTI) system**  is defined by the following equations
>$$
>\left\{
>\begin{align*}
> X_{t+1} &= A\,X_{t} + B\,U_{t} \\[5pt]
> Y_{t} &= C\,X_{t} + D\,U_{t}
>\end{align*} \right.
>$$

^90435d


### State-Space Model as Nonlinear Dynamic System

![[State Space Models and Nonlinear Dynamic System#^4beaac]]

- [[State Space Models and Nonlinear Dynamic System]]




## Explanation

>[!info]
>A *linear dynamical system* can be viewed as a **dynamic Bayesian network** where the variables are all *continuous* and all of the dependencies are **linear Gaussian**.

- [[Dynamic Bayesian Network]]
- [[Gaussian Bayesian Network]]

>[!info]
>A *linear dynamic model* is a basic model in **modern control theory**.


## State-Observation Models

![[State-Observation Models#^dc6850]]

>[!important] Definition
>The **discrete-time linear time-invariant (LTI) system** can be formulated as a **state-observation model** where
>- the *transition model* is defined by the *Gaussian distribution* $$\mathcal{P}(X_{t+1} | X_{t}, \,U_{t}) = \mathcal{N}(\,A(t) X_{t} + B(t) U_{t}\;;\;  \Sigma_{X}\,),$$
>- the *observation model* is defined by the *Gaussian distribution* $$\mathcal{P}(Y_{t} | X_{t},\, U_{t}) = \mathcal{N}(\,C(t) X_{t} + D(t) U_{t}\;;\;  \Sigma_{O}\,).$$
>  
>The above model is also called a **linear Gaussian state space model (LG-SSM)**.  

^550f59


- [[State-Observation Models]]
- [[Gaussian Random Vector]]
- [[Kalman Filter Discrete-Time]]

## Stochastic Control and Stochastic Differential Equation

>[!important] 
>In *stochastic control*, we assume that the control process $(U(t), t\ge 0)$ is a *Gaussian white noise*. 
>
>We can formulate the *continuous-time* linear dynamic system using **(homogeneous) linear stochastic differential equation**
>$$
>\left\{
>\begin{align*}
> dX(t) &= A(t)\,X(t)\,dt + B(t)\,d\mathcal{W}(t) \\[5pt]
> dY(t) &= C(t)\,X(t)\,dt + D(t)\,d\mathcal{W}(t)
>\end{align*} \right.
>$$

^dbfda1

- [[Homogeneous Linear Stochastic Differential Equation]]
- [[Linear Stochastic Differential Equation]]
- [[Stochastic Differential Equations]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 379





-----------
##  Recommended Notes and References


- [[Extended Kalman Filter]]
- [[Kalman Filter Discrete-Time]]
- [[Sequential Importance Sampling]]


- [[Dynamic Bayesian Network]]
- [[Markov Chain Monte Carlo Methods]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Probabilistic Graphical Models by Koller]] pp 211 - 222
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 357, 969 - 996
- [[Deep Learning Foundations and Concepts by Bishop]] pp 515
- [[Introduction to Stochastic Calculus by Klebaner]] pp 379
- Wikipedia [State-space_representation](https://en.wikipedia.org/wiki/State-space_representation)