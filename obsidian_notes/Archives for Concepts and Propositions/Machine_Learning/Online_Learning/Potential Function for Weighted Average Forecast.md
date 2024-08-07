---
tags:
  - concept
  - online_learning/theory
  - machine_learning/theory
  - machine_learning/online_learning
keywords:
  - exp_concave_loss
  - exp_potential
topics:
  - online_learning
name: Potential Function for Weighted Average Forecast
date of note: 2024-08-05
---

## Concept Definition

>[!important]
>**Name**: Potential Function for Weighted Average Forecast


![[Regret for Online Learning#^7704b4]]

>[!important] Definition
>Define the **potential function** $\Phi: \mathbb{R}^{k} \to \mathbb{R}_{+}$ as
>$$
>\Phi \left( u \right) := \psi \left( \sum_{i=1}^{k}\phi(u_{i}) \right)
>$$
>where $u=(u_{1} \,{,}\ldots{,}\,u_{k})$ and 
>- $\phi: \mathbb{R}\to \mathbb{R}$ is any *non-negative*, *increasing* and *twice-differentiable function*,
>- $\psi: \mathbb{R}\to \mathbb{R}$ is any *non-negative*, *strictly increasing* and *concave*, and *twice-differentiable function*.

^f29770

- [[Convex Function]]
- [[Operations that Preserve Convexity]]
- [[Convex Differentiation Theorem]]
- [[Regret for Online Learning]]

## Explanation

>[!info]
>We concern about the *potential function* of *cumulative regret* of all experts after round $T$
>$$
>\Phi(R_{T}) = \Phi \left( R_{1, T} \,{,}\ldots{,}\, R_{k, T}\right) = \psi \left( \sum_{i=1}^{k}\phi \left( R_{i, T} \right) \right)
>$$

>[!info]
>We can find the gradient of $\Phi$ as
>$$
>\nabla \Phi(u)_{i} := \frac{ \partial  }{ \partial u_{i} } \Phi = \psi'\left(  \sum_{i=1}^{k}\phi(u_{i}) \right)\,\phi'(u_{i}) 
>$$
>So in the **normalized weight**, the *factor* involving function $\psi$ can be cancelled. 
>$$
>\begin{align*}
> w_{i} := \frac{\nabla \Phi(u)_{i}\,f_{i}}{\sum_{i=1}^{k}\nabla \Phi(u)_{i}\,f_{i}} = \frac{\phi'(u_{i})\, f_{i} }{\sum_{i=1}^{k}\phi'(u_{i})\,f_{i} }
>\end{align*}
>$$
>In other word, the **normalized weight** is *independent of* the choice of *function* $\psi$.
>
>On the other hand, the condition on **convexity** of $\phi$ is *not needed* for **no-regret guarantee**. But usually we choose a convex function $\phi$.


## Example

>[!example]
>We define the **exponential potential** as 
>$$
>\Phi(u; \eta) := \frac{1}{\eta}\log \left( \sum_{i=1}^{k}\exp \left( \eta\, u_{i} \right) \right)
>$$
>
>See that the **gradient of exponential potential** is
>$$
>\nabla \Phi(u; \eta)_{i} = \frac{\exp \left( \eta\, u_{i} \right)}{\sum_{i=1}^{k}\exp \left( \eta\, u_{i} \right)}
>$$

^57afc0




-----------
##  Recommended Notes and References


- [[Exponential Weights Algorithm for Convex Loss]]
- [[Prediction with Expert Advice]]


- [[Convex Function]]
- [[Convex Optimization Problem]]

- [[f-Divergence]]
- [[Phi Entropy Functional]]

- [[Prediction Learning and Games by Cesa-Bianchi]] pp 9, 45
