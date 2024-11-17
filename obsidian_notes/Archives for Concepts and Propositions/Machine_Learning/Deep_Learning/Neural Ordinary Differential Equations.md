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
>- Note that the **log-determinant of Jacobian** of *continuous flow* $f_{t}$ is determined by another *ODE* $$\left\{\begin{align}\frac{d}{dt} L(t) &= \text{tr}\left[(D_{x}\,F(\cdot, t))\,(x(t))\right]  \\[5pt]  L(0) &= 0\end{align}\right.$$ where
>	- $$L(t)  := \log \lvert \det D_{x}f_{t}(x_{0}) \rvert.$$
>	- This requires us to compute $$\text{tr}(D_{x}F)$$ for neural network $F$ by **back-propagation** at each step of the ODE solver.
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
>Consider the task of training the neural network $F$ under the loss $\mathcal{L}$, i.e. $$\min_{w}\;\mathcal{L}(x(T))$$ where $$x(T) := x(0) +  \int_{0}^{T}F(x(t),t; w)\;dt$$
>
>The **adjoint sensitive method** solve above problem in the *forward-backward pass* as follows:
>- Define the **adjoint** as $$a(t) := \frac{d\mathcal{L}}{dx(t)}$$
>	- $a(T)$ corresponds to the usual gradient of loss with respect to output of the network.
>- The **adjoint** satisfies its own *ordinary differential equation* $$\frac{d}{dt} a(t) = -   a(t)^{T}\,D_{x}F(\cdot,t; w)(x(t))$$
>	- This is the *chain of rule* in continuous time.
>	- The ODE can be solved by **integration backwards**, starting with $a(T)$  with *ODE solver*.
>- In order to use ODE solver, we need to **store $x(t)$ in forward mode** for $t\in [0,T]$
>	- If we want to use $x(t_{i})$ not stored, we can recompute any required values of $x(t)$ by integrating $$\frac{d}{dt} x(t) = F(x(t), t; w)$$ along $$\frac{d}{dt} a(t) = -   a(t)^{T}\,D_{x}F(\cdot,t; w)(x(t))$$ given output $x(T).$
>- Finally, the **gradient of loss** *with respect to* **parameter** $w$  is given by $$\nabla_{w}\mathcal{L} = - \int_{0}^{T}\,a(t)^{T}\,\nabla_{w}\,F(x(t), t; w)dt$$
>	- Both $\nabla_{w}F$ and $D_{x}\,F$ can be evaluated efficiently via *back-propagation.*
>- The  **adjoint sensitive method** is seen as the **continuous-time** analogue of **back-propagation.**


- [[Back-Propagation Algorithm]]

### Reverse-Mode Derivative of Neural ODE Initial Value Problem

>[!important] Definition
>The algorithm that computes the **reverse-mode derivative** of **neural ODE initial value problem (IVP)** is described as below:
>$$
>\left\{
>\begin{align}
> \frac{d}{dt} x(t) &= F(x(t), t; w) \\[5pt] 
> x(0) &= z
>\end{align}
>\right.
>$$
>
>- *Require*: parameter $w\in \mathbb{R}^{p}$; 
>- *Require*: stop time $T$
>- *Require*: final state $x(T) =x$ where $x$ is the *observation*
>- *Require*: the loss function $\mathcal{L}(x; w)$
>- *Require*: the *loss gradient* $$a(T) := \frac{ \partial \mathcal{L} }{ \partial x(T) }$$
>- Define the *initial augmented state* $$s(T) := \left[ \begin{array}{ccc}x(T) & \dfrac{ \partial \mathcal{L} }{ \partial x(T) } & \dfrac{ \partial \mathcal{L} }{ \partial w(T) }   \end{array} \right] := [x(T),\; a(T),\; a_{w}(T)]$$ where $$a_{w}(T) := \dfrac{ \partial \mathcal{L} }{ \partial w(T) }  = 0.$$
>- Define the **augmented dynamic system (aug-dynamic)** with *reverse-time ODE* as $$\left\{\begin{align}\frac{d}{dt} s(t) &= \left[ \begin{array}{c} F(x(t), t; w) \\[8pt] -a(t)^{T}\,D_{x}F(\cdot,t; w)(x(t)) \\[8pt] -a(t)^{T}\,\nabla_{w}F(x(t),t; w)  \end{array} \right] \\[8pt] s(T) &= \left[ \begin{array}{ccc}x(T) & a(T) & 0 \end{array} \right]\end{align}\right.$$ where
>	- the state $$s(t) := \left[ \begin{array}{ccc}x(t) & a(t) & a_{w}(t) \end{array} \right]$$
>	- Compute the **vector-Jacobian products** $$a(t)^{T}\,D_{x}F(\cdot,t; w), \quad a(t)^{T}\,\nabla_{w}F(x(t),t; w)$$
>- Call the *ODE solver* to solve the **reverse-time ODE.** $$\left[ \begin{array}{ccc} x(0) & \dfrac{ \partial \mathcal{L} }{ \partial x(0) }  & \dfrac{ \partial \mathcal{L} }{ \partial w} \end{array} \right] = \text{ODE-Solver}\left( s(T), \text{ aug-dynamic}, T, 0, w \right) $$ where $$\frac{ \partial \mathcal{L} }{ \partial w} := \frac{ \partial \mathcal{L} }{ \partial w(0)}.$$
>- *Return*:
>	- the gradient of loss with respect to both flow and network parameter $$\dfrac{ \partial \mathcal{L} }{ \partial x(0) }, \quad  \dfrac{ \partial \mathcal{L} }{ \partial w}$$

- [[Theory and Algorithms for Numerical Solution of Differential Equations]]

>[!info]
>The vector-Jacobian products 
>$$a(t)^{T}\,D_{x}F(\cdot,t; w), \quad a(t)^{T}\,\nabla_{w}F(x(t),t; w)$$  
>can be efficiently evaluated by **automatic differentiation**, at a time *cost* similar to that of evaluating $F$.

- [[Automatic Differentiation]]

>[!info]
>All integrals for solving $$s(t) = \left[ \begin{array}{ccc}x(t) & \dfrac{ \partial \mathcal{L} }{ \partial x(t) } & \dfrac{ \partial \mathcal{L} }{ \partial w } \end{array} \right] $$
>can be computed in a **single call to an ODE solver**



### Proof on the ODE for Adjoint

>[!info]
>Define the **bounded linear operator** $T_{\epsilon}$
>$$
>T_{\epsilon}(x(t), t) = x(t) + \int_{t}^{t+\epsilon}\;F(x(t), t; w)\,dt = x(t+\epsilon) 
>$$
>based on the assumption that $F$ is *Lipschitz continuous* with Lipschitz constant independent from $t$.

- [[Existence and Uniqueness of Solution of Ordinary Differential Equations]]

>[!info]
>We have
>$$
>\begin{align*}
> \frac{d\mathcal{L}}{dx(t)} &=  \frac{d\mathcal{L}}{dx(t+\epsilon)}\;\frac{d x(t+\epsilon)}{dx(t)} \\[10pt]
> \iff a(t) &= a(t+\epsilon)^{T}\;\frac{d x(t+\epsilon)}{dx(t)}\\[8pt]
> &= a(t+\epsilon)^{T}\;\frac{\partial \;T_{\epsilon}(x(t), t)}{\partial x(t)} 
>\end{align*}
>$$

>[!info]
>Consider the *Taylor expansion* of $T_{\epsilon}$ at $x(t)$ as
>$$
>\begin{align*}
>T_{\epsilon}(x(t), t) &= x(t) + \int_{t}^{t+\epsilon}\;F(x(t), t; w)\,dt  \\[10pt]
>&= x(t) + \epsilon\, F(x(t), t; w) + O(\epsilon^2)
>\end{align*}
>$$
>
>Note that 
>$$
>\begin{align*}
>\frac{\partial \;T_{\epsilon}(x(t), t)}{\partial x(t)} &= \frac{ \partial  }{ \partial x(t) }\left[  x(t) + \epsilon\, F(x(t), t; w) + O(\epsilon^2) \right]  \\[8pt]
>&= I + \epsilon\, D_{x}F(x(t), t; w) + O(\epsilon^2)
>\end{align*}
>$$

- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]

>[!info]
>The **derivative** of $a(t)$ is obtained via the definition
>$$
>\begin{align*}
> \frac{d}{dt}a(t) &= \lim_{ \epsilon \to 0 }\; \frac{1}{\epsilon}\;\left[ a(t+\epsilon) - a(t) \right]  \\[8pt]
> &= \lim_{ \epsilon \to 0 }\; \frac{1}{\epsilon}\;\left[ a(t+\epsilon) - a(t+\epsilon)^{T}\;\frac{\partial \;T_{\epsilon}(x(t), t)}{\partial x(t)}  \right]  \\[8pt]
>&= \lim_{ \epsilon \to 0 }\; \frac{1}{\epsilon}\;a(t+\epsilon)^{T}\,\left[ I - \frac{\partial \;T_{\epsilon}(x(t), t)}{\partial x(t)}  \right]  \\[8pt]
>&= \lim_{ \epsilon \to 0 }\; \frac{1}{\epsilon}\;a(t+\epsilon)^{T}\,\left[ I - I - \epsilon\, D_{x}F(x(t), t; w) - O(\epsilon^2) \right]  \\[8pt]  
>&= \lim_{ \epsilon \to 0 }\; \frac{1}{\epsilon}\;a(t+\epsilon)^{T}\,\left[ - \epsilon\,D_{x}F(x(t), t; w)  \right]  -\frac{1}{\epsilon}\ O(\epsilon^2)\\[8pt]
>&= \lim_{ \epsilon \to 0 }\; - a(t+\epsilon)^{T}\,D_{x}F(x(t), t; w)  -\frac{1}{\epsilon}\ O(\epsilon^2)\\[8pt]
>&= - a(t)^{T}\,D_{x}F(x(t), t; w)
>\end{align*}
>$$

### Proof on the Gradient of Loss w.r.t. Parameter 

>[!info]
>We can view that
>-  $w(t) =w$ is constant, i.e. $$\frac{\partial}{\partial t} w(t) = 0$$
>- and $t(t) = t$ is identity map, $$\frac{d}{dt} t = 1$$
>
>We have an augmented ODE
>$$
>\begin{align*}
> \frac{d}{dt} (x(t), w(t), t) = \left[ \begin{array}{c}F(x(t),t, w(t)) \\[5pt] 0 \\[5pt] 1\end{array} \right] 
>\end{align*}
>$$
>
>Let 
>$$a_{aug}(t) := \left[ \begin{array}{c}a(t) \\[5pt] a_{w}(t) \\[5pt] a_{t}(t)\end{array} \right] = \left[ \begin{array}{c} \dfrac{ \partial \mathcal{L} }{ \partial x(t) }  \\[5pt] \dfrac{ \partial \mathcal{L} }{ \partial w(t) } \\[5pt] \dfrac{ \partial \mathcal{L} }{ \partial t } \end{array} \right]$$
>where $$\mathcal{L} :=  \mathcal{L}(x(t), w(t), t)$$
>
>Note that the above derivation regarding the **gradient of adjoint**  still holds which means that 
>$$
>\frac{d}{dt} a_{aug}(t) =  -  \left[ \begin{array}{cc}a(t) & a_{w}(t) & a_{t}(t)\end{array} \right]\left[ \begin{array}{ccc}D_{x}F & \nabla_{w}F & \partial_{t} F  \\[5pt] 0 & 0 &0 \\[5pt] 0 & 0 & 0 \end{array} \right]    = - \left[ \begin{array}{c}a(t)^{T}\,D_{x}F \\[5pt] a(t)^{T}\,\nabla_{w}F \\[5pt] a(t)^{T}\,\partial_{t}F \end{array} \right] 
>$$
>which includes 
>$$
>\frac{d}{dt} a_{w}(t) = - a(t)^{T}\,\nabla_{w}F
>$$
>
>Finally, 
>$$
>\begin{align*}
> \frac{d\mathcal{L}}{dw} &= \int_{0}^{T}\; \frac{d}{dt}  \frac{d\mathcal{L}}{dw(t)}\;dt  \\[8pt]
> &:= \int_{0}^{T} \frac{d}{dt} a_{w}(t)\;dt \\[8pt]
> &= -\int_{0}^{T}a(t)^{T}\,\nabla_{w}F(x(t), w(t))\;dt \\[8pt]
> &:= -\int_{0}^{T}a(t)^{T}\,\nabla_{w}F(x(t), w)\;dt
> \end{align*}
>$$




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
- Youtube [Neural ODEs (NODEs) Physics Informed Machine Learning](https://www.youtube.com/watch?v=nJphsM4obOk)