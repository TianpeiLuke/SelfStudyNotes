---
tags:
  - concept
  - math/stochastic_process
  - math/differential_equation
keywords:
  - linear_stochastic_differential_equation
topics:
  - differential_equation
  - stochastic_process
name: Linear Stochastic Differential Equation
date of note: 2024-06-11
---

## Concept Definition

>[!important]
>**Name**: Linear Stochastic Differential Equation

![[Stochastic Differential Equations#^dda568]]


>[!important] Definition
>The stochastic differential equation
>$$
>\left\{ 
>\begin{align*}
>dX(t) &= b\left( X(t), t\right)\,dt + A\left( X(t), t \right)\,dW\\
>X(0)&= X_{0}
>\end{align*}
>\right.
>$$
>is called **linear** if the **coefficients** $b$ and $A$ has the following form
>- $$b(x, t) := c(t) + D(t)\,x$$ for $$c: [0,T] \to \mathbb{R}^n, \quad D: [0,T] \to \mathbb{M}^{n\times n}$$
>- $$A(x, t) := E(t) + F(t)\,x$$ for $$E: [0,T] \to \mathbb{M}^{n\times m}, \quad F: [0,T] \to L(\mathbb{R}^n, \mathbb{M}^{n\times m}),$$ the space of bounded linear map from $\mathbb{R}^n$ to $\mathbb{M}^{n\times m}.$
>
>If, in addition, $F \equiv 0$, then we called it **linear stochastic differential equation** in **narrow sense**. 

^a12b01


- [[Stochastic Differential Equations]]
- [[Progressively Measurable Stochastic Process]]
- [[Space of Bounded Linear Operators]]

- [[Homogeneous Linear Stochastic Differential Equation]]

## Explanation

>[!important] 
>The **linear stochastic differential equations** has the form
>$$
>\left\{ 
>\begin{align*}
>dX &= \left[c(t) + D(t)\,X\right]\;dt + \left[E(t) + F(t)\,X\right]\,dW\\
>X(0)&= X_{0}
>\end{align*}
>\right.
>$$

^6bba38

>[!important] 
>The **linear stochastic differential equations** in **narrow sense** has the form
>$$
>\left\{ 
>\begin{align*}
>dX &= \left[c(t) + D(t)\,X\right]\;dt + E(t)\,dW\\
>X(0)&= X_{0}
>\end{align*}
>\right.
>$$
>
>That is, it only has **additive noise** term not *multiplicative noise*.


## Example

>[!example]
>The **Langevin equation** is a *linear stochastic differential equation (in narrow sense)*
>$$
>\left\{
>\begin{align*}
> dX &= - \beta X\,dt + \sigma\, dW\\
> X(0) &= X_{0}
>\end{align*}
>\right.
>$$
>where $c(t) = 0$, $D(t)= -\beta$,  $E(t)= \sigma$, and $F(t) = 0.$
>
>Its solution is the **Ornstein-Uhlenbeck process.**

- [[Homogeneous Linear Stochastic Differential Equation]]
- [[Ornstein–Uhlenbeck Process]]




-----------
##  Recommended Notes and References

- [[Stochastic Differential Equations]]

- [[Lipschitz Continuous Function]]
- [[Contraction Function]]
- [[Contraction Map Principle]]
- [[Borel-Cantelli Lemma]]

- [[Linear Semilinear and Quasilinear Partial Differential Equations]]

- [[State Space Models and Linear Dynamic System]]

- [[Introduction to Stochastic Differential Equations by Evans]]