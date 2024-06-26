---
tags:
  - concept
  - math/stochastic_process
keywords:
  - global_balance_equation
  - invariant_measure
topics:
  - stochastic_process
name: Global Balance Equation for Invariant Measure
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Global Balance Equation for Invariant Measure


![[Invariant Measure and Stationary Distribution#^56092f]]

### Discrete State Markov Chain

>[!important] Definition (Discrete State)
>Let $(X_{n})$ be a *Markov chain* with *discrete state* $\mathcal{X}$.
>
>The **invariant distribution** $\pi$ satisfies the following **global balance equation**:
>$$
> \begin{align}
> \sum_{y \in \mathcal{X}}\pi(x)K(x, y) &=  \sum_{y \in \mathcal{X}}\pi(y)K(y, x), \quad \forall x\in \mathcal{X}. 
> \end{align}
>$$  
>This means the **total flow out** of $x$ (LHS) is **equal** to the **total flow into** $x$ (RHS) in steady state.

### Harris Chain


>[!important] Definition (Uncountable State)
>Let $(X_{n})$ be a *Harris chain* with *uncountable state* $\mathcal{X}$.
>
>The **invariant distribution** $\pi$ satisfies the following **global balance equation**:
>$$
> \begin{align}
> \int_{\mathcal{X}}\int_{A}\pi(dx)\,K(x, dy) &=  \int_{\mathcal{X}}\int_{A}\pi(dy)\,\,K(y, dx), \quad \forall A\in \mathcal{B}(\mathcal{X}). 
> \end{align}
>$$  
>This means the **total flow out** of $A$ (LHS) is **equal** to the **total flow into** $A$ (RHS) in steady state.
>$$
>\int_{\mathcal{X}}\int_{A}K(x,y)\,\pi(x)\,dx\,dy = \int_{\mathcal{X}}\int_{A}K(y,x)\,\pi(y)\,dx\,dy, \quad \forall A\in \mathcal{B}(\mathcal{X}). 
>$$


## Explanation



## Detailed Balance Equation

- [[Detailed Balance Equation]]




-----------
##  Recommended Notes and References

- [[Detailed Balance Equation]]

- [[Invariant Measure and Stationary Distribution]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]]
- Wikipedia [Balance_equation](https://en.wikipedia.org/wiki/Balance_equation)