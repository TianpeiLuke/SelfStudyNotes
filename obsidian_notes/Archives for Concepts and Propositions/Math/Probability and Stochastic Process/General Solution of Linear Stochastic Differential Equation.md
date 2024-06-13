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
name: General Solution of Linear Stochastic Differential Equation
date of note: 2024-06-11
---

## Concept Definition

>[!important]
>**Name**: General Solution of Linear Stochastic Differential Equation

![[Stochastic Differential Equations#^dda568]]


![[Linear Stochastic Differential Equation#^a12b01]]

>[!important] Proposition (Linear Stochastic Differential Equations in Narrow Sense)
>The **solution** of *linear stochastic differential equation*
>$$
>\left\{ 
>\begin{align*}
>dX &= \left[c(t) + D\,X\right]\;dt + E(t)\,dW\\
>X(0)&= X_{0}
>\end{align*}
>\right.
>$$
>is
>$$
>\begin{align*}
> X(t) &= e^{D\,t}X_{0} + \int_{0}^{t}e^{D(t-s)}\left[c(s)ds + E(s)dW\right]
>\end{align*}
>$$
>where  $D$ does not depend on $X$ or $t$ and
>$$
>e^{D\,t} = \sum_{k=0}^{\infty}\frac{D^k\,t^k}{k!}.
>$$

>[!important] Proposition (Linear Stochastic Differential Equations in Narrow Sense)
>The **solution** of 
>$$
>\left\{ 
>\begin{align*}
>dX &= \left[c(t) + D(t)\,X\right]\;dt + E(t)\,dW\\
>X(0)&= X_{0}
>\end{align*}
>\right.
>$$
>is
>$$
>\begin{align*}
> X(t) &= \Phi(t)\left\{X_{0} + \int_{0}^{t}\Phi^{-1}(s)\left[c(s)ds + E(s)dW\right]\right\}
>\end{align*}
>$$
>where  $\Phi(\cdot)$ is the **fundamental matrix** of the following *non-autonomous system of ordinary differential equations*
>$$
>\left\{ 
>\begin{align*}
>\frac{d}{dt} \Phi(t) &= D(t)\,\Phi(t)\\
>\Phi(0)&= I
>\end{align*}
>\right.
>$$


>[!important] Proposition (Scalar Stochastic Differential Equations)
>Suppose $n=1$ but $m \ge 1$ is arbitrary. 
>
>The **solution** of 
>$$
>\left\{ 
>\begin{align*}
>dX(t) &= \left[c(t) + b(t)\,X\right]\;dt +\sum_{j=1}^{m}\left[e^{j}(t) + f^{j}(t)X\right]\,dW^{j}\\
>X(0)&= X_{0}
>\end{align*}
>\right.
>$$
>is
>$$
>\begin{align*}
> X(t) &= \Phi(t)\left\{X_{0} + \int_{0}^{t}\Phi^{-1}(s)\left[c(s) - \sum_{j=1}^{m}e^{j}(s) f^{j}(s) \right]\,ds\;\right\} \\
> & \qquad + \int_{0}^{t}\,\sum_{j=1}^{m}\,\Phi^{-1}(s)e^{j}(s)\,dW^{j},
>\end{align*}
>$$
>where 
>$$
>\Phi(t) = \exp\left(\int_{0}^{t}\,\left(b -  \sum_{j=1}^{m}\frac{(f^j)^2}{2}\right)\;ds \, + \, \int_{0}^{t}\sum_{j=1}^{m}f^j\,dW^j \right)
>$$

- [[Linear Stochastic Differential Equation]]
- [[Stochastic Differential Equations]]
- [[Existence and Uniqueness of Solution for Stochastic Differential Equation]]
- [[Brownian Motion Wiener Process]]


>[!info]
>- The effect of **scalar term** $c(t)$  in **drift part** is $$\Phi(t)\left\{\int_{0}^{t}\Phi^{-1}(s)c(s)\,ds\;\right\}$$
>- The effect of **scalar term** $e(t)$ in **diffusion part** is 
>  $$
>\begin{align*}
>\Phi(t)\left\{\int_{0}^{t}\Phi^{-1}(s)\left[ - \sum_{j=1}^{m}e^{j}(s) f^{j}(s) \right]\,ds\;\right\} + \int_{0}^{t}\,\sum_{j=1}^{m}\,\Phi^{-1}(s)e^{j}(s)\,dW^{j}.
>\end{align*}
> $$
> This shows the **compound effect** of *multiplicative noise*.
>- The **multiplicative factor** $$\Phi(t) \equiv \Phi(b, f, t)$$ only depends on the **linear coefficient** in **both drift and diffusion parts**.
>- The **linear coefficient** in **diffusion part**, which makes it a **multiplicative noise** will also take effect in $$\Phi(t)\int_{0}^{t}\Phi^{-1}(s)\left[ - \sum_{j=1}^{m}e^{j}(s) f^{j}(s) \right]\,ds.$$ In this term, the effect will be *multiplied* by the **scalar term** in the diffusion part 


## Explanation

>[!important]
>If $X_{0}$ is **Gaussian distributed**, the solution of linear SDE is also a **Gaussian process**.

- [[Gaussian Process]]

>[!important]
>From the general formula, we can see that for **homogeneous linear stochastic equation** $c\equiv e \equiv 0$, 
>$$
>X_{t} = X_{0}\,\exp\left(\int_{0}^{t}\,\left(b -  \sum_{j=1}^{m}\frac{(f^j)^2}{2}\right)\;ds \, + \, \int_{0}^{t}\sum_{j=1}^{m}f^j\,dW^j \right)
>$$




## Examples

>[!example]
>Consider the **Langevin equation** which is a *linear SDE* with **additive noise**
>$$
>\left\{ 
>\begin{align*}
>dX &= -\beta\,X\;dt + \sigma\,dW\\
>X(0)&= X_{0}
>\end{align*}
>\right.
>$$
>
>The solution is [[Ornstein–Uhlenbeck Process]], which is of form
>$$
>X_{t} = e^{-\beta t} X_{0} + \sigma \int_{0}^{t}e^{-\beta(t-s)}dW(s) = e^{-\beta t}\left\{ X_{0} + \sigma \int_{0}^{t}e^{\beta s}dW(s)  \right\} 
>$$
>The solution contains two **additive** terms.

- [[Langevin Equation]]


>[!example]
>Consider a **homoegeneous**  *linear SDE* with **multiplicative noise**
>$$
>\left\{ 
>\begin{align*}
>dX &= a\,X\;dt + b\,X\,dW\\
>X(0)&= X_{0}
>\end{align*}
>\right.
>$$
>
>The solution is 
>$$
>X_{t} = X_{0}\;\exp\left( \left(a - \frac{1}{2}b^2\right)t + b\,W_{t} \right)
>$$
>We see that the solution is a **multiplicative scaling** to $X_{0}.$






-----------
##  Recommended Notes and References

- [[Stochastic Differential Equations]]

- [[Lipschitz Continuous Function]]
- [[Contraction Function]]
- [[Contraction Map Principle]]
- [[Borel-Cantelli Lemma]]


- [[Introduction to Stochastic Differential Equations by Evans]]