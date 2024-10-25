---
tags:
  - concept
  - machine_learning/dynamic_system
  - probabilistic_graphical_models/sequential_models
keywords:
  - extended_kalman_filter
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

>[!important] Definition
>The Kalman filter can be extended to the case where the *system dynamics* and/or the *observation model* are *nonlinear*.
>
>The basic idea is to **linearize** the *dynamics and observation models* about the previous state estimate using a *first order Taylor series expansion*, and then to apply the standard *Kalman filter* equations. 
>
>This approach is called the **extended Kalman filter (EKF)**

- [[Kalman Filter Discrete-Time]]
- [[State Space Models and Nonlinear Dynamic System]]



## Explanation





-----------
##  Recommended Notes and References


- [[Kalman Filter Discrete-Time]]
- [[State Space Models and Nonlinear Dynamic System]]
- [[Linear Dynamic System]]
- [[State-Observation Models]]
- [[Bayesian Filtering and Smoothing Equations for State Observation Models]]

- [[Bayesian Neural Network]]

- [[Hidden Markov Model]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 369 - 373
