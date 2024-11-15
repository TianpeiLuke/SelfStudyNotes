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
  - real_nvp_density_estimation
topics:
  - deep_learning/generative_models
name: Real Non-Volume-Preserving as Coupling Flows for Deep Density Estimation
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Real Non-Volume-Preserving as Coupling Flows for Deep Density Estimation

![[Coupling Flows#^f016a0]]

>[!important] Definition
>The **real-valued non-volume-preserving (real NVP)** is a **coupling flow** which are described by the following system of equations
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

^79cbda

- [[Coupling Flows]]
- [[Normalizing Flows]]
- [[Normalizing Flows Construction]]


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

## Real NVP for Deep Density Estimation


![[real_nvp_flow.png]]




-----------
##  Recommended Notes and References


- [[Bijective Function and Inverse Function]]
- [[Jacobian Matrix and Jacobian Determinant]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Hadamard Product of Matrices]]
- [[Artificial Neural Network and Deep Learning]]



- [[Wasserstein Distance]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 825 - 826
- [[Deep Learning Foundations and Concepts by Bishop]] pp 549 - 551
- [[Foundations of Computer Vision by Torralba]]