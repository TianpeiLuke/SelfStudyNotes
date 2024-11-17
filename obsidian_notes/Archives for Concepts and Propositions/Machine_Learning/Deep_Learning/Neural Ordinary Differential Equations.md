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
>	- This requires us to compute $$\text{tr}(DF)$$ for neural network $F$ by **back-propagation** at each step of the ODE solver.
>	- To avoid *backpropagation through ODE solver*, weuse the **adjoint sensitivity method** to express the time evolution of the gradient with respect to $x(t)$ as a *separate ODE*.


- [[Continuous-Time Flows]]
- [[Ordinary Differential Equations]]
- [[Vector Field as Infinitesimal Generator of Global Flow]]
- [[Global Flow on Smooth Manifold]]
- [[Existence and Uniqueness of Solution of Ordinary Differential Equations]]
- [[Lipschitz Continuous Function]]
- [[Back-Propagation Algorithm]]

![[neural_ode.png]]


###  Adjoint Sensitivity Method

>[!important] Definition
>The *continuous flow* is characterized by the  *joint ODE* for the flow $x(t)$ and the *log-determinant of Jacobian*
>$$\left\{
>\begin{align}
> \frac{d}{dt} (x(t), L(t)) &= \left[ \begin{array}{c}F(x(t), t) \\[5pt] \text{tr}\left[(D_{x}\,F(\cdot, t))\,(x(t))\right] \end{array} \right]  \\[5pt] 
> (x(0), L(0)) &= (z, 0)
>\end{align}
>\right.
>$$  
>where the vector field requires to compute the *gradient of neural network*  $$\text{tr}\left[(D_{x}\,F(\cdot, t))\,(x(t))\right] $$ at each step of the ODE solver.
>
>Consider the task of training the neural network $F$ under the loss $\mathcal{L}$, i.e. $$\min_{w}\;\mathcal{L}(x_{w}(T))$$ where $$x(T) := x_{w}(T) := \int_{0}^{T}F(x(t); w)\;dt$$
>
>The **adjoint sensitive method** solve above problem in the *forward-backward pass* as follows:
>- Define the **adjoint** as $$a(t) := \frac{d\mathcal{L}}{dx(t)}$$
>	- $a(T)$ corresponds to the usual gradient of loss with respect to output of the network.
>- The **adjoint** satisfies its own *ordinary differential equation* $$\frac{d}{dt} a(t) = -   a(t)^{T}\,D_{x}F(\cdot, w)(x(t))$$
>	- This is the *chain of rule* in continuous time.
>	- The solution can be solved by **integration backwards**, starting with $a(T)$  with *ODE solver*.
>- In order to use ODE solver, we need to **store $x(t)$ in forward mode** for $t\in [0,T]$
>	- If we want to use $x(t_{i})$ not stored, we can recompute any required values of $x(t)$ by integrating $$\frac{d}{dt} x(t) = F(x(t); w)$$ along $$\frac{d}{dt} a(t) = -   a(t)^{T}\,DF(\cdot, w)(x(t))$$ given output $x(T).$
>- Finally, the **gradient of loss** *with respect to* **parameter** $w$  is given by $$\nabla_{w}\mathcal{L} = - \int_{0}^{T}\,a(t)^{T}\,\nabla_{w}\,F(x(t), w)dt$$
>	- Both $\nabla_{w}F$ and $D_{x}\,F$ can be evaluated efficiently via *back-propagation.*








### Numerical Solution

>[!info]
>- The **explicit Euler method** for the neural ODE is given by 
>$$
>x_{t+1} = x_{t} + F(x_{t}; w)
>$$ 
>- The **implicit Euler method** for the neural ODE is given by 
>$$
>x_{t+1} = x_{t} + F(x_{t+1}; w)
>$$ 
>- The **$2$-step Nyström method** for the neural ODE is given by 
>$$
>x_{t+2} = x_{t} + 2F(x_{t+1}; w)
>$$ 
>- The **trapezoidal rule** for the neural ODE is given by 
>$$
>x_{t+1} = x_{t} + \frac{1}{2}(F(x_{t+1}; w) + F(x_{t}; w))
>$$ 

- [[Explicit Euler Method for Discretization of ODE]]
- [[Implicit Euler Method for Discretization of ODE]]
- [[Theory and Algorithms for Numerical Solution of Differential Equations]]


## Explanation

>[!quote]
>One **benefit** of *neural ODEs trained* using the **adjoint method**, compared to *conventional layered networks*, is that 
>- there is **no need to store** the *intermediate* results of the *forward propagation*, and hence the **memory cost is constant**. 
>- Furthermore, neural ODEs can naturally handle **continuous-time data** in which observations occur at arbitrary times. 
>	- If the error function $\mathcal{L}$ depends on values of $x(t)$ *other than the output value*, then **multiple runs of the reverse-model solver** are required, with one run for *each consecutive pair of outputs*, so that the single solution is broken down into multiple consecutive solutions in order to access the intermediate states (Chen et al., 2018). 
>	- Note that a *high level of accuracy* in the solver can be used during training, with a lower accuracy, and hence fewer function evaluations, during inference in applications for which *compute resources are limited*.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 556 - 557	  



## Continuous-Time Diffusion Network

![[Continuous-Time Diffusion Network via Stochastic Differential Equations#^cf4caf]]

- [[Continuous-Time Diffusion Network via Stochastic Differential Equations]]


-----------
##  Recommended Notes and References




- [[Artificial Neural Network and Deep Learning]]

- [[Normalizing Flows]]
- [[Residual Flows]]
- [[Maximal Integral Curve of Vector Field]]

- [[Markov Chain and Markov Process]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 834 - 837
- [[Deep Learning Foundations and Concepts by Bishop]] pp 555 - 559
- Chen, R. T., Rubanova, Y., Bettencourt, J., & Duvenaud, D. K. (2018). Neural ordinary differential equations. _Advances in neural information processing systems_, _31_.