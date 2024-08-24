---
tags:
  - concept
  - machine_learning/models
  - deep_learning/discriminative_models
  - online_learning/algorithms
keywords:
  - perceptron
  - perceptron_algorithm
topics:
  - online_learning
  - deep_learning/algorithm
  - machine_learning_algorithm
name: Perceptron Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Perceptron Algorithm

>[!important] Definition
>Consider the task of **linear classification**, i.e. given a collection of samples $(X_{i},Y_{i})$ for $Y_{i} \in \{ 0,1 \}$ $i=1 \,{,}\ldots{,}\,n$ , the goal is to find a *linear function* $$f(x; w) = \left\langle  w\,,\, x   \right\rangle$$ such that the *classification error* of *threshold function* of $f$ is minimized, $$\min_{w} \sum_{i=1}^{n} \ell(f(X_{i}, w)， Y_{i})$$ where $$\ell(f(x; w)， y) = \max\left\{ 0, -y\;f(x;w) \right\}$$
>
>Note that the above loss function is called the **hinge loss**, which is a **surrogate loss function** for the **empirical risk**
>$$
> \mathbb{1}\left\{ y \neq \text{sgn}\left\{ f(x;w) \right\}  \right\}  \le  \max\left\{ 0, -y\;f(x;w) \right\} 
>$$

- [[Surrogate Loss Minimization]]
- [[Empirical Risk Minimization]]



>[!important] Definition
>The **Perceptron algorithm** is described as follow:
>- *Require*: initial weight $w_{0} = 0$
>- *Require*: learning rate $\eta >0$
>- *Initialize* $w_{1} = w_{0}$
>- For $t=1\,{,}\ldots{,}\,T$:
>	- Learner **receives** observation $x_{t}$
>	- **Predict** label based on which **side** the sample $x_{t}$ lies in **relative to the hyperplane** parameterized by $w_{t}$ $$\hat{y}_{t} = \text{sgn}\left\{ \left\langle  w_{t}\,,\,x_{t}    \right\rangle \right\} $$
>	- *Environment* reveals **outcome** $y_{t}\in \{ 0 ,1 \}$
>	- If **error** $\hat{y}_{t} \neq y$
>		- Update **linear parameter** i.e. new **hyperplane** $$w_{t+1} = w_{t} + \eta\, y_{t}\,x_{t}$$
>	- Otherwise keep the weight $w_{t+1} = w_{t}$
>- *Return*: $w_{T+1}$


## Explanation

>[!quote]
>The **Perceptron algorithm** is one of the earliest machine learning algorithms. It is an **on-line linear classification algorithm**. Thus, it learns a decision function based on a hyperplane by processing training points one at a time.
>
>-- [[Foundations of Machine Learning by Mohri]] pp 190


## Perceptron as Sub-Gradient Descent

>[!important] Definition
>The **Perceptron algorithm** can be seen as a **subgradient descent algorithm** for solving 
>$$
>\sum_{i=1}^{n} \max\left\{ 0, -y_{i}\left\langle  w\,,\,x_{i}    \right\rangle \right\} 
>$$
>
>In particular, let $\hat{f}_{x,y}(w) =  \max\left\{ 0, -y\left\langle  w\,,\,x    \right\rangle \right\}.$ 
>- For each $(x,y)$,  $\hat{f}$ is **convex** since it is **maximum** of a **convex (linear) function** $\left\langle  w\,,\,x    \right\rangle$
>- $\hat{f}$ is non-differentiable at $\left\langle  w\,,\, x   \right\rangle=0$
>- When $\left\langle  w\,,\, x   \right\rangle=0$, we can find a **subgradient** of $\hat{f}$ as $$\partial \hat{f}(w) \ni - y\,x$$
>- If $\left\langle  w\,,\,x    \right\rangle \neq 0$, the function is differentiable, and the gradient is computed based on value of $y\left\langle  w\,,\, x   \right\rangle$
>	- if $y\left\langle  w\,,\,  x \right\rangle < 0$  $$\hat{f}(w; x,y) = -y\left\langle  w\,,\,x    \right\rangle \implies  \nabla_{w} \hat{f}(w; x,y) = - y\,x$$
>	-  if $y\left\langle  w\,,\,  x \right\rangle > 0$  $$\hat{f}(w; x,y) = 0 \implies  \nabla_{w} \hat{f}(w; x,y) = 0$$
>- The **subgradient descent algorithm** update the weight as
>$$
>\begin{align*}
> w_{t+1} = \left\{\begin{array}{lc}w_{t} - \eta\, \nabla_{w}\hat{f}(w_{t}; x_{t}, y_{t})& \text{if }  \left\langle  w_{t}\,,\,x_{t} \right\rangle \neq 0\\ w_{t} + \eta\,y_{t}\,x_{t} & \text{if }  \left\langle  w_{t}\,,\,x_{t} \right\rangle = 0 \end{array}\right.
>\end{align*}
>$$
>- Substituting the *gradient formula* above, we have
>$$
>\begin{align*}
> w_{t+1} = \left\{\begin{array}{lc}w_{t}& \text{if } y\left\langle  w_{t}\,,\,x_{t} \right\rangle > 0\\ w_{t} + \eta\,y_{t}\,x_{t} & \text{if }  y\left\langle  w_{t}\,,\,x_{t} \right\rangle \le 0 \end{array}\right.
>\end{align*}
>$$

- [[Rectified Linear Unit as Activation for Deep Learning]]
- [[Convex Function]]
- [[Operations that Preserve Convexity]]
- [[Subgradient Methods]]
- [[Stochastic Gradient Descent Algorithm]]

## Perceptron as Artificial Neural Network

![[perceptron_simple_ann.png]]

>[!important] 
>**Perceptron** can be seen as the simplest **artificial neural network** where there is only **one output node**.
>$$
>\hat{y} = \sigma \left(\left\langle  w\,,\, x   \right\rangle\right)
>$$
>where $$\sigma(s) := \text{sgn}(s)$$ is a **nonlinear activation function**, given by a non-differentiable *hard-thresholding function*

- [[Artificial Neural Network and Deep Learning]]







-----------
##  Recommended Notes and References


- [[Follow-The-Leader Algorithm]]
- [[Follow-The-Regularized-Leader Algorithm]]

- [[Artificial Neural Network and Deep Learning]]
- [[Multi-Layer Perceptron and Feed-Forward Network]]
- [[Iterative Maximum Entropy Learning for AdaBoost]]


- [[Understanding Machine Learning by Shalev-Shwartz]] pp 92
- [[Foundations of Machine Learning by Mohri]] pp 100, 190 - 200
- [[Prediction Learning and Games by Cesa-Bianchi]] pp 336 - 338,  340 - 344

- [[Deep Learning by Goodfellow]]  pp 14, 23
- [[Deep Learning Foundations and Concepts by Bishop]] pp 17 - 18
