---
tags:
  - concept
  - machine_learning/dynamic_system
  - probabilistic_graphical_models/sequential_models
  - EKM
  - extended_kalman_filter
keywords:
  - extended_kalman_filter
  - EKM
topics:
  - dynamic_system
  - probabilistic_graphical_model
name: Extended Kalman Filter
date of note: 2024-08-14
---

## Concept Definition

>[!important]
>**Name**: Extended Kalman Filter

![[State Space Models and Nonlinear Dynamic System#^4beaac]]

- [[State Space Models and Nonlinear Dynamic System]]

>[!info]
>The Kalman filter can be extended to the case where the *system dynamics* and/or the *observation model* are *nonlinear*.
>
>The basic idea is to **linearize** the *dynamics and observation models* about the previous state estimate using a *first order Taylor series expansion*, and then to apply the standard *Kalman filter* equations. 
>
>This approach is called the **extended Kalman filter (EKF)**


>[!important] Definition
>The *discrete-time* **Extended Kalman Filter (EKF)** is an extension of the Kalman filter designed for *non-linear dynamic models*. Consider the following non-linear state and observation equations:
>$$\left\{\begin{align*}X^{(t+1)} &= f(X^{(t)}, U^{(t)}) + W^{(t)} \\[5pt] O^{(t)} &= h(X^{(t)}, U^{(t)}) + V^{(t)} \end{align*} \right.$$
>where 
>- $f$ and $h$ are non-linear functions, 
>- $U^{(t)}$ is the control input,
>- $W^{(t)} \sim \mathcal{N}(0, Q^{(t)})$ is the *process noise*, 
>- $V^{(t)} \sim \mathcal{N}(0, R^{(t)})$ is the *measurement noise*.

- [[State Space Models and Nonlinear Dynamic System]]
- [[State-Observation Models]]
- [[Kalman Filter Discrete-Time]]

### Algorithm

>[!important] Definition
>The *discrete-time* **Extended Kalman Filter (EKF)** is described as
>- *Require*: the *non-linear dynamic model* $$\left\{\begin{align*}X^{(t+1)} &= f(X^{(t)}, U^{(t)}) + W^{(t)} \\[5pt] O^{(t)} &= h(X^{(t)}, U^{(t)}) + V^{(t)} \end{align*} \right.$$
>- *Require*: the *prior* for state $$X^{(0)} \sim \mathcal{N}(\mu_{0|0}, \Sigma_{0|0}).$$
>- For $t=1 \,{,}\ldots{,}\,T$:
>	- **Prediction Step**: 
>		- compute the *predicted state estimate* and *predicted error covariance*. 
>		- **Linearizing** the non-linear *state transition* function $f$ around the previous state estimate $\mu_{t-1|t-1}$. 
>			- The *Jacobian matrix* of $f$ with respect to $X$ is denoted by $F_x(t-1)$ and evaluated at $\mu_{t-1|t-1}$ and $U^{(t-1)}$ (if applicable). $$F_{x}(t-1) := \nabla f(\mu_{t-1|t-1}, U^{(t-1)})$$
>		- The **predicted state estimate** is given by $$\mu_{t|t-1} = f(\mu_{t-1|t-1}, U^{(t-1)})$$
>		- The **predicted error covariance** is updated via $$\Sigma_{t|t-1} = F_x(t-1)\,\Sigma_{t-1|t-1}\,F_x(t-1)^{T} + Q^{(t-1)}$$
>	- **Update Step**: (also called the **measurement update step**) 
>		- **Linearizing** the non-linear observation function $h$ around the predicted state estimate $\mu_{t|t-1}$. 
>			- The *Jacobian matrix* of $h$ with respect to $X$ is denoted by $H_x(t)$ and evaluated at $\mu_{t|t-1}$ and $U^{(t)}$ (if applicable). $$H_x(t) = \nabla h(\mu_{t|t-1}, U^{(t)})$$
>		- The **predicted measurement** is given by $$\hat{O}^{(t)} = h(\mu_{t|t-1}, U^{(t)})$$
>		- The **innovation (measurement residual)** is given by $$e_{t} = O^{(t)} - \hat{O}^{(t)} = O^{(t)} - h(\mu_{t|t-1}, U^{(t)})$$
>		- The **innovation covariance matrix** (or measurement covariance) is given by $$S^{(t)} = H_x(t)\,\Sigma_{t|t-1}\,H_x(t)^{T} + R^{(t)}$$
>		- Compute the **Kalman gain matrix** $$K_{t} = \Sigma_{t|t-1}\,H_x(t)^{T}\,\left(S^{(t)}\right)^{-1}$$
>			- Note that the *cross covariance matrix* between the predicted state and the predicted measurement is $$\Sigma_{t|t-1}\,H_x(t)^{T}.$$
>			- In practice, we solve *a system of linear equations* $$(S^{(t)})^{T}\,K_{t}^{T}\, = (H_x(t)\,\Sigma_{t|t-1})^{T}$$
>		- **Update** the **state estimate** $$\mu_{t|t} = \mu_{t|t-1} + K_{t}\,e_{t} = \mu_{t|t-1} + K_{t}\,\left(O^{(t)} - h(\mu_{t|t-1}, U^{(t)})\right)$$
>		- **Update** the **error covariance matrix** $$\Sigma_{t|t} = (I - K_{t}\,H_x(t))\,\Sigma_{t|t-1}$$

- [[Jacobian Matrix and Jacobian Determinant]]
- [[System of Linear Equations or Linear System]]
- [[Bayesian Filtering and Smoothing Equations for State Observation Models]]



## Explanation

>[!info]
>The Extended Kalman Filter approximates the non-linear system by **linearizing** around the current estimate, allowing the application of Kalman filter principles. 
>
>However, this linearization can introduce errors, especially if the non-linearities are strong.




-----------
##  Recommended Notes and References


- [[Kalman Filter Discrete-Time]]
- [[Bayesian Neural Network]]
- [[Hidden Markov Model]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 369 - 373
