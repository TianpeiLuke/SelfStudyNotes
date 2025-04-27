---
tags:
  - concept
  - machine_learning/algorithms
  - machine_learning/dynamic_system
  - probabilistic_graphical_models/sequential_models
  - statistics/signal_processing
  - math/stochastic_process
  - kalman_filter
  - Kalman_Filter
keywords:
  - kalman_filter
  - kalman_bucy_filter
topics:
  - stochastic_process
  - statistics/signal_processing
  - probabilistic_graphical_model
name: Kalman Filter Continuous-Time
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Kalman Filter Continuous-Time

![[Linear Dynamic System#^78b0f0]]

![[Linear Dynamic System#^dbfda1]]

>[!important] Definition
>The *Kalman filter* can be extended to work with *continuous time dynamical systems*; the resulting method is called the **Kalman Bucy filter**.
>
>In particular, consider the *linear SDE* with *time-dependent non-random coefficients* for *state* and *observation process*
>$$
>\left\{
>\begin{align*}
> dX(t) &= A(t)\,X(t)\,dt + B(t)\,d\mathcal{W}_{1}(t) \\[5pt]
> dY(t) &= C(t)\,X(t)\,dt + D(t)\,d\mathcal{W}_{2}(t)
>\end{align*} \right.
>$$
>where $(\mathcal{W}_{1}(t), \mathcal{W}_{2}(t))$ are *independent Brownian motions* and initial conditions on $X(0)$ and $Y(0)$

- [[Kalman Filter Discrete-Time]]
- [[Linear Dynamic System]]
- [[Linear Stochastic Differential Equation]]
- [[Homogeneous Linear Stochastic Differential Equation]]
- [[Brownian Motion Wiener Process]]

>[!important] Definition
>The goal is to infer the *optimal estimator* for $X(t)$ given *filtration* $\mathscr{F}_{t}^{Y}$, which is given by
>$$
> \hat{X}(t) = \pi_{t}(X) = \mathbb{E}_{  }\left[ X(t)\;|\;\mathscr{F}_{t}^{Y} \right]
>$$

- [[Filtration]]
- [[Minimum Mean Square Estimation]]

>[!important] Theorem
>Suppose that the state $X(t)$ and observation $Y(t)$ are given by 
>$$
>\left\{
>\begin{align*}
> dX(t) &= A(t)\,X(t)\,dt + B(t)\,d\mathcal{W}_{1}(t) \\[5pt]
> dY(t) &= C(t)\,X(t)\,dt + D(t)\,d\mathcal{W}_{2}(t)
>\end{align*} \right.
>$$
>
>Then the **optimal estimator**
>$$
> \hat{X}(t) = \pi_{t}(X) = \mathbb{E}_{  }\left[ X(t)\;|\;\mathscr{F}_{t}^{Y} \right]
>$$
>satisfies the following **SDE**
>$$
>d\hat{X}(t) = \left( A(t) - v(t)\, \frac{C^2(t)}{D^2(t)} \right)\,\hat{X}(t)\,dt + v(t)\, \frac{C(t)}{D^2(t)}\,dY(t)
>$$
>where $$v(t) =  \mathbb{E}\left[ \left(X(t) - \hat{X}(t) \right)^2 \right]$$ is the **mean squared error**. 
>
>- The **mean squared error** satisfies the **Riccati ordinary differential equation** with initial conditions
>$$
>\left\{
>\begin{align*}
> \frac{d}{dt}v(t) &= 2 A(t)\,v(t) + B^2(t) - \frac{C^2(t)}{D^2(t)}\,v^2(t) \\[8pt]
> v(0) &= \text{Var}(X(0)) - \frac{\text{Cov}^2(X(0), Y(0))}{\text{Var}(Y(0))}
>\end{align*} \right.
>$$
>and initial conditions on $X(0)$.






## Explanation


>[!info]
>Due to linearity, the linear SDE for dynamic system has *closed-form solution* and the solution processes are *Gaussian process*.

- [[Gaussian Process]]






-----------
##  Recommended Notes and References


- [[Kalman Filter Discrete-Time]]
- [[Extended Kalman Filter]]
- [[Linear Dynamic System]]


- [[Linear Stochastic Differential Equation]]
- [[Stochastic Differential Equations]]
- [[Brownian Motion Wiener Process]]
- [[Gaussian Process]]


- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]




- [[Introduction to Stochastic Calculus by Klebaner]] pp 379 - 381
- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 364
- [[Artificial Intelligence Modern Approach by Russell]]