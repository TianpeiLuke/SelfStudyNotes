---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
keywords:
  - normalizing_flow_model
  - coupling_flow
  - global_flow_smooth_manifold
  - local_flow_smooth_manifold
topics:
  - deep_learning/generative_models
name: Coupling Flows
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Coupling Flows

![[Normalizing Flows#^294151]]

>[!important] Definition
>Consider a *partition* of latent variable space $z\in \mathcal{Z} \subset \mathbb{R}^{d}$ as $$z := (z^{A}, z^{B})$$ where $z^{A}\in \mathbb{R}^{p}$ and $z^{B} \in \mathbb{R}^{d-p}$.
>
>A layer of **coupling flows** is described by the following system of equations
>$$
>\left\{\begin{align}
> x^{A} &= \hat{f}(z^{A};\; \Theta(z^{B})) \\[8pt]
> x^{B} &= z^{B}
>\end{align}\right.
>$$
>where 
>- the function $\hat{f}$ is a *bijection* on subspace $\mathbb{R}^{p}$, i.e. $$\hat{f}: \mathbb{R}^{p} \to \mathbb{R}^{p}$$
>- The corresponding function $f: \mathbb{R}^{d} \to \mathbb{R}^{d}$ parameterized by $\theta$ is called the **coupling layer**
>	- The function $f: (z^{A}, z^{B})\to (x^{A}, x^{B})$ *couples* $z^{A}$ and $z^{B}$ together through $\hat{f}$ and $\Theta$
>- The *parameter* of $\hat{f}$ is given by $$\theta := \Theta(z^{B}),$$ where $\Theta$ is an arbitrary function, called the **conditioner.** 
>	- $\Theta$ can be a *neural network*.
>- The **inverse** of **coupling flow** is given by $$z = f^{-1}(x)$$ where $$\left\{\begin{align}z^{A} &= \hat{f}^{-1}(x^{A};\; \Theta(x^{B})) \\[8pt] z^{B} &= x^{B} \end{align}\right.$$
>- The **Jacobian** of $f$ is *block triangular* $$Df = \left[ \begin{array}{cc} \partial x^{A} / \partial z^{A} & \partial x^{A} / \partial z^{B} \\[5pt] \partial x^{B} / \partial z^{A} & \partial x^{B} / \partial z^{B}  \end{array} \right]  =  \left[ \begin{array}{cc} D\hat{f} & \partial x^{A} / \partial z^{B} \\[5pt] 0 & I_{d-p}  \end{array} \right]$$
>	- The *Jacobian determiant* of $f$ and $\hat{f}$ are equal, i.e. $$\det Df = \det D\hat{f}.$$
>- A common choice of $\hat{f}$ is the **elementwise flow**, i.e. $$\hat{f}(z^{A}; \Theta(z^{B})) := (h(z^{A,1}; \theta_{1})\,{,}\ldots{,}\,h(z^{A,p}; \theta_{p}))$$
>	- We can define a *binary mask* $b\in \mathbb{R}^{d}$ so that we can implement *arbitrary partitions* $$x = b \odot z + (1- b) \odot  \hat{f}(z; \; \Theta(b \odot z))$$

^f016a0


- [[Normalizing Flows]]
- [[Normalizing Flows Construction]]

- [[Bijective Function and Inverse Function]]
- [[Jacobian Matrix and Jacobian Determinant]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Hadamard Product of Matrices]]


![[coupling_flow.png]]

>[!info]
>For one **coupling layer**, one part of the input is unchanged, like the *residual connection*.
>
>We can **reverse the role** of $z^{A}$ and $z^{B}$ in next layer so that the value of $z^{B}$ is changed next layer.


![[coupling_flow_multiple_layer.png]]



## Explanation

>[!quote]
>Unlike 
>- **affine flows**, which mix dimensions linearly, 
>- and **elementwise flows**, which do not mix dimensions at all, 
>
>**coupling flows** can *mix dimensions* with a flexible *non-linear conditioner* $\Theta$. 
>- In practice we often implement $\Theta$ as a *deep neural network*; any architecture can be used, including MLPs, CNNs, ResNets, etc.
>  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 826  

>[!quote]
>There are many ways to **define the partition** of $z$ into $(z^{A}, z^{B})$. 
>- A simple way is just to partition $z$ into **two halves**. 
>- We can also exploit **spatial structure** in the partitioning. 
>	- For example, if u is an image, we can partition its pixels using a “checkerboard” pattern, where pixels in “black squares” are in $z^{A}$ and pixels in “white squares” are in $z^{B}$ [DSDB17]. 
>	- Since only *part of the input* is transformed by each coupling layer, in practice we typically *employ different partitions* **along a coupling flow**, to ensure all variables get transformed and are given the opportunity to interact.
>	  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 826  	  

## Real-valued Non-Volume-Preserving

>[!important] Definition
>The **real-valued non-volume-preserving (NVP)** is a **coupling flow** which are described by the following system of equations
>$$
>\left\{\begin{align}
> x^{A} &= \exp(s(z^{B}, w)) \odot z^{A} + b(z^B, w) \\[8pt]
> x^{B} &= z^{B}
>\end{align}\right.
>$$
>where 
>- $$s(z^{B}, w), \quad b(z^{B}, w)$$ are real-valued outputs of *neural networks*, and the exponential ensures that the *multiplicative term is non-negative.*
>	- Note that the networks $s(z^{B}, w)$ and $b(z^{B}, w)$ are *not required to be bijective*.
>- The **inverse** of flow is described as $$\left\{\begin{align}z^{A} &= \exp(-s(z^{B}, w)) \odot \left(x^{A} - b(z^B, w) \right)\\[8pt] z^{B} &= x^{B} \end{align}\right.$$
>- The **Jacobian** is given by $$Df =  \left[ \begin{array}{cc} \text{diag}\left(\exp(s)\right) & \partial x^{A} / \partial z^{B} \\[5pt] 0 & I_{d-p}  \end{array} \right]$$
>	- The **Jacobian determinant** is given by $$\det Df = \prod_{i}^{p}\exp(s^{i}(z^{B}, w))$$


![[real_nvp_flow.png]]




-----------
##  Recommended Notes and References


- [[Artificial Neural Network and Deep Learning]]



- [[Wasserstein Distance]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 825 - 826
- [[Deep Learning Foundations and Concepts by Bishop]] pp 549 - 551
- [[Foundations of Computer Vision by Torralba]]