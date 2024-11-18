---
tags:
  - concept
  - machine_learning/kernel_methods
  - machine_learning/theory
  - machine_learning/models
  - deep_learning/architecture
keywords:
  - margin_based_loss
topics:
  - machine_learning_theory
  - machine_learning_models
name: Margin-based Loss Function
date of note: 2024-09-09
---

## Concept Definition

>[!important]
>**Name**: Margin-based Loss Function

>[!important] Definition
>Consider a linear classifier $$h(x) = \left\langle  w\,,\,  x  \right\rangle + b.$$
>
>The **geometric margin** or **margin** of $h$ at a point $x\in \mathbb{R}^{d}$ is the *Euclidean distance* to the *hyperplane* $\left\langle  w\,,\, x \right\rangle + b =0$
>$$
>\rho_{h}(x) := \frac{\lvert \left\langle  w\,,\, x \right\rangle + b \rvert }{\lVert w \rVert_{2}}.
>$$

^81d98d

>[!important] Definition
>Consider a linear classifier $$h(x) = \left\langle  w\,,\,  x  \right\rangle + b.$$
>
>The **geometric margin** or **margin** of $h$ for a sample $\mathcal{S} := (x_{1}\,{,}\ldots{,}\,x_{m})$ is the *minimum geometric margin* over the points in the sample, $$\rho_{h}(\mathcal{S}) = \min_{x_{i}\in \mathcal{S}}\rho_{h}(x_{i}),$$ that is the *distance of the hyperplane* defining $h$ to the *closest sample points.*

^048de3

![[geometric_margin.png]]

### Margin-Loss Function

>[!important] Definition
>Let $(X,Y)$ be sample from a joint distribution $P$ on $\mathcal{X}\times \mathcal{Y}$ and $$f: \mathcal{X} \to \mathcal{Y}$$ be measurable function. 
>
>A *loss function* $L_{\phi}: \mathcal{Y}\times \mathcal{Y} \to \mathbb{R}_{+}$ is called a **margin-based loss** function if it is of the form 
>$$
>L_{\Phi}(Y, f(X)) := \phi \left(Yf(X)\right)
>$$
>where 
>- $\phi: \mathcal{Y} \to \mathbb{R}$ is a *convex surrogate function*,  and $$\phi(x) \ge \phi_{\rho, ramp}(x)$$
>- $yf(x)$ is called the **confidence margin** or the **margin.**
>  
>The **margin-based risk** is defined as $$L_{\Phi}(f) := \mathbb{E}_{ X,Y }\left[\, \phi(Yf(X)) \,\right]$$  

^a01095

- [[Statistical Decision Problem]]
- [[Empirical Risk Minimization]]
- [[Convex Function]]

>[!important] Definition
>The **ramp loss** is a *margin-based loss* function, which is defined as
>$$
>L_{\rho}(Y, f(X)) := \phi_{\rho,ramp} \left(Yf(X)\right)
>$$
>where
>$$
>\phi_{\rho, ramp}(x) := \min\left\{ 1,\, \max\left\{ 0,\, 1- \frac{x}{\rho} \right\}  \right\} =  \left\{\begin{array}{cl} 1 & \text{ if }x \le 0 \\[5pt] 1 - \dfrac{x}{\rho} & \text{ if }x\in [0, \rho] \\[5pt] 0 & \text{ if }x \ge \rho \end{array}\right.
>$$
>- The *convex surrogate function* of the ramp loss is given by any convex function $\phi$ such that  $$\phi(x) \ge \phi_{\rho, ramp}(x)$$ 
>- Note that **ramp loss** is a *surrogate function* for the **empirical error** 
>$$
>\mathbb{1}\left\{ f(X) \neq Y \right\} = \mathbb{1}\left\{ f(X) Y < 0\right\} \le  \phi_{\rho, ramp}(Yf(X))
>$$ 
>Thus the *generalization error* is bounded above by the *margin loss* $$\begin{align*}L(f) &:= \mathbb{E}_{ X,Y }\left[  \mathbb{1}\left\{ f(X) \neq Y \right\}  \right] \\[5pt] &\le  \mathbb{E}_{ X,Y }\left[  \phi_{\rho}(Yf(X))  \right] \\[5pt] &:= L_{\phi}(h) \end{align*}$$

^19baca

- [[Surrogate Loss Minimization]]

![[ramp_loss.png]]


![[surrogate_loss_comparison.png]]


## Explanation

>[!info]
>$$
>\begin{align*}
>\rho_{h}(x) &= \min\{ \lVert x - v \rVert_{2}: \left\langle  w\,,\,v  \right\rangle + b  = 0 \}
>\end{align*}
>$$
>Assume that $\lVert w \rVert = 1.$ Take $$v = \left( \frac{- \left\langle  w\,,\,x    \right\rangle -b}{\left\langle  w\,,\,w    \right\rangle} \right) w + x \implies \left\langle  w\,,\,v  \right\rangle + b = 0$$ and $$\lVert x - v \rVert_{2} = \lvert  \left\langle  w\,,\,x \right\rangle + b\rvert\,\lVert w \rVert = \lvert  \left\langle  w\,,\,x \right\rangle + b\rvert  $$
>
>For any other $u$ such that $\left\langle  w\,,\,u  \right\rangle + b  = 0$. We show that 
>$$
>\begin{align*}
>\lVert x - u \rVert_{2}^2 &=  \lVert x - v + v - u \rVert_{2}^2\\
>&= \lVert x - v  \rVert_{2}^2 + \lVert v - u \rVert_{2}^2 + 2 \left\langle  x - v\,,\, v - u   \right\rangle\\
>&\ge \lVert x - v  \rVert_{2}^2 + 2 \left\langle  x - v\,,\, v - u   \right\rangle\\
>&=  \lVert x - v  \rVert_{2}^2 + 2 ( \left\langle  w\,,\,x \right\rangle + b) \left\langle   w\,,\, v - u   \right\rangle\\
>&= \lVert x - v  \rVert_{2}^2 
>\end{align*}
>$$
>since $$\left\langle  w\,,\,u  \right\rangle + b = \left\langle  w\,,\,v  \right\rangle + b \implies \left\langle   w\,,\, v - u   \right\rangle = 0.$$
>
>Thus $v = \left( \frac{- \left\langle  w\,,\,x    \right\rangle -b}{\left\langle  w\,,\,w    \right\rangle} \right) w + x$ is the optimal solution with minimum distance being $$\lVert x - v \rVert_{2} = \lvert  \left\langle  w\,,\,x \right\rangle + b\rvert\,\lVert w \rVert$$


## Generational Bound for Margin-Based Loss 

- [[Margin-based Generalization Error Bound]]
- [[Margin-based Generalization Error Bound for Kernel Hypothesis]]

## Connection to $f$-Divergence

- [[Density Ratio Estimation via Binary Classifiers]]



-----------
##  Recommended Notes and References


- [[Support Vector Machine Linear Separable Case]]
- [[Representer Theorem]]

- [[Margin-based Generalization Error Bound]]
- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]

- [[Support Vector Machine Linear Separable Case]]
- [[AdaBoost Algorithm]]


- [[Learning with Kernels by Schölkopf]]
- [[Kernel Methods in Machine Learning by Hofmann]]


- [[Boosting Foundations and Algorithms by Schapire]] pp 94 - 96

- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 167 - 178
- [[Foundations of Machine Learning by Mohri]] pp 79 - 92


- [[Probabilistic Machine Learning Advanced Topics by Murphy]]