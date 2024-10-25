---
tags:
  - concept
  - math/stochastic_process
  - math/differential_equation
keywords:
  - ito_integration
  - integration_by_parts
topics:
  - stochastic_process
  - differential_equation
name: Integration by Parts of Itô Stochastic Integration
date of note: 2024-06-18
---

## Concept Definition

>[!important]
>**Name**: Integration by Parts of Itô Stochastic Integration

>[!important] Proposition
>Let $X_{t}$ and $Y_{t}$ be **semi-martingales.** 
>
>Then the following **integration by parts** holds for **Itô integral**
>$$
>\begin{align*}
> \int_{0}^{t}X_{s-} dY_{s} &= - \int_{0}^{t}Y_{s-} dX_{s} + X_{t}\,Y_{t} - X_{0}\,Y_{0} - \left[ X, Y \right]_{t} 
>\end{align*}
>$$
>where
>$$
>\left[X, Y \right]_{t} :=  \lim_{ \Delta(P_{t}^n) \to 0 }\sum_{i=0}^{k_{n}-1}\left(X_{t_{i+1}^n} - X_{t_{i}^n}\right)\left(Y_{t_{i+1}^n} - Y_{t_{i}^n}\right)  
>$$
>is the **covariation** (or **cross-variance**) term.

^f05140

- [[Ito Stochastic Integration]]
- [[Ito Chain Rule and Ito Formula]]
- [[Quadratic Variation and Covariation of Stochastic Process]]

>[!important] 
>For **Itô process** $X_1$ and $X_{2}$,  
>$$
>\begin{align*}
>dX_{1} &= F_{1}\,dt + G_{1}\,dW\\
>dX_{2} &= F_{2}\,dt + G_{2}\,dW
>\end{align*}
>$$
>the **chain rule** gives 
>$$
>\begin{align*}
>d\left( X_{1}\,X_{2} \right) = X_{1}\,dX_{2} + X_{2}\,dX_{1} + dX_{1}\,dX_{2}
>\end{align*}
>$$
 >
>The integrated version is
>$$
>\begin{align*}
> \int_{s}^{t}X_{2}\,dX_{1} &=  - \int_{0}^{t} X_{1}\,dX_{2} -  \int_{0}^{t} G_{1}\,G_{2}\,dt  +  X_{1}(t)\,X_{2}(t) -  X_{1}(s)\,X_{2}(s).
>\end{align*}
>$$
>It is the **Itô integration-by-part formula**.

- [[Ito Process]]
- [[Ito Product Rule and Stochastic Integration by Parts]]

## Explanation

>[!important]
>Compare with **Riemann–Stieltjes integration by parts**
>$$
>\int_{0}^{t} X(s)\,dY(s) = - \int_{0}^{t} Y(s)\,dX(s) + X(t)Y(t) - X(0)Y(0),
>$$
>the stochastic integration by parts has additional **quadratic variation term** $$\left[ X, Y \right] $$
>
>This addition term is due to **Itô integral** choosing tagged point $$\tilde{t_{i}^{n}} = t_{i}^n$$
>as **left-boundary**.
 
- [[Integration by Parts]]
- [[Quadratic Variation and Covariation of Stochastic Process]]


-----------
##  Recommended Notes and References

- [[Integration by Parts]]
- [[Ito Stochastic Integration]]

- [[Introduction to Stochastic Calculus by Klebaner]]
- Wikipedia [Ito Calculus](https://en.wikipedia.org/wiki/It%C3%B4_calculus)