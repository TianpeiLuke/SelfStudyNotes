---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - math/differential_equation
  - numerical_methods/numerical_differential_equations
keywords:
  - neural_ordinary_differential_equations
  - ordinary_differential_equations
  - normalizing_flow_model
topics:
  - deep_learning/generative_models
  - differential_equation
  - numerical_differential_equation
name: Neural Ordinary Differential Equations
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Neural Ordinary Differential Equations

![[Continuous-Time Flows#^f77037]]

>[!important] Definition
>The **neural ordinary differential equation** characterized a *continuous flow* $$x(t) = f_{t}(z)$$ in terms of *ordinary differential equations* with *initial value condition*
>$$\left\{
>\begin{align}
> \frac{d}{dt} x(t) &= F(x(t), t) \\[5pt] 
> x(0) &= z
>\end{align}
>\right.
>$$
>where
>- the vector field $$F: \mathbb{R}^{d} \times [0,T] \to \mathbb{R}^{d}$$ is parameterized by a **neural network** 
>- The **continuous flow** is defined as the map from the initial value to final value, along integral curve of ODE $$f(z) = x(T).$$
>- Note that the **log-determinant of Jacobian** of *continuous flow* $f_{t}$ is determined by another *ODE* $$\left\{\begin{align}\frac{d}{dt} L(t) &= \text{tr}\left[(D\,F(\cdot, t))\,(x(t))\right]  \\[5pt]  L(0) &= 0\end{align}\right.$$ where
>	- $$L(t)  := \log \lvert \det D f_{t}(x_{0}) \rvert.$$
>	- To avoid *backpropagation through ODE solver*, weuse the **adjoint sensitivity method** to express the time evolution of the gradient with respect to $x(t)$ as a *separate ODE*.


- [[Continuous-Time Flows]]
- [[Ordinary Differential Equations]]
- [[Vector Field as Infinitesimal Generator of Global Flow]]
- [[Global Flow on Smooth Manifold]]
- [[Existence and Uniqueness of Solution of Ordinary Differential Equations]]
- [[Lipschitz Continuous Function]]
- [[Back-Propagation Algorithm]]

###  Adjoint Sensitivity Method




### Numerical Solution

- [[Explicit Euler Method for Discretization of ODE]]
- [[Implicit Euler Method for Discretization of ODE]]
- [[Runge-Kutta Methods for Numerical ODE]]
- [[k-Step Methods for Numerical ODE]]


## Explanation




-----------
##  Recommended Notes and References




- [[Artificial Neural Network and Deep Learning]]

- [[Normalizing Flows]]
- [[Residual Flows]]
- [[Maximal Integral Curve of Vector Field]]

- [[Markov Chain and Markov Process]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 834 - 837
- [[Deep Learning Foundations and Concepts by Bishop]] pp 555 - 559