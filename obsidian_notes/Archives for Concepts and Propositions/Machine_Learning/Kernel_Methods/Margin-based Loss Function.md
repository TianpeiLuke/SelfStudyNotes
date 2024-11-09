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
>A *loss function* $\ell: \mathcal{Y}\times \mathcal{Y} \to \mathbb{R}_{+}$ is called a **margin-based loss** function if it is of the form 
>$$
>\ell(Y, f(X)) := \hat{\ell} \left(Yf(X)\right)
>$$
>where 
>- $\hat{\ell}: \mathcal{Y} \to \mathbb{R}$ is a *convex function*, and
>- $yf(x)$ is called the **margin.**
>  
>The **margin-based risk** is defined as $$R_{\ell}(f) := \mathbb{E}_{ X,Y }\left[ \hat{\ell}(Y\,f(X)) \right]$$  

- [[Statistical Decision Problem]]
- [[Empirical Risk Minimization]]
- [[Convex Function]]



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