---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - optimization/theory
  - math/optimal_transport
keywords:
  - entropic_regularization
  - optimal_transport
topics:
  - information_theory
  - information_geometry
  - optimization
  - optimal_transport
name: entropic regularized optimal transport
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Entropic Regularized Optimal Transport

![[Optimal Transport in Discrete Setting#^afc0dd]]
![[Optimal Transport in Discrete Setting#^ad1beb]]

- [[Optimal Transport in Discrete Setting]]

### Kantorovich Optimal Transport with Entropic Regularization

>[!important]
>This section introduces a family of numerical schemes to approximate solutions to *Kantorovich formulation* of **optimal transport** and its many generalizations. It operates by adding an **entropic regularization penalty** to the original problem. This regularization has several important advantages:
> - the minimization of the regularized problem can be solved using a simple **alternate minimization** scheme, which only required matrix-vector multiplication, 
> 
> - the resulting approximate distance is **smooth** with respect to input histogram weights and positions of the Diracs and can be differentiated using **automatic differentiation**.

- [[Tikhonov Regularization in Optimization and Learning]]
- [[Automatic Differentiation]]

>[!important] Definition
>We introduce the **entropic regularization** term to the primal problem:
>$$
> \begin{align}
> H(\boldsymbol{P}) &:= -\sum_{i,j}P_{i,j}\left(\log(P_{i,j}) - 1\right)
> \end{align}
>$$
>

- [[Shannon Entropy]]
- [[Kullback-Leibler Divergence]]
- [[Convex Function]]

>[!info]
>The function $H$ is **$1$-strongly concave**, because its *Hessian* is 
>$$\partial^2 H(\boldsymbol{P}) = − \text{diag}\left(\frac{1}{P_{i,j}}\right)  > 0$$ and $P_{i,j} \le 1$. 

- [[Strongly Convex Function]]

>[!important] Entropic-Regularized Optimal Transport (Discrete)
>The **entropic-regularized optimal transport** is formulated as the following convex optimization problem
>$$
>\begin{align*}
>\min_{P_{i,j} \in \mathbb{R}_{+}^{n \times m}} & \sum_{i,j}C_{i,j} P_{i,j} + \lambda \sum_{i,j}P_{i,j}\left(\log(P_{i,j}) - 1\right) \\
\text{s.t. }&  \sum_{j=1}^{m}P_{i,j} = a_{i}, \quad 1 \le i \le n \\
&\sum_{i=1}^n P_{i,j}  = b_{j}, \quad 1 \le j \le m   \\
&P_{i,j} \ge 0 \nonumber
\end{align*}
>$$

- [[Theory and Algorithms for Convex Optimization]]
- [[Nonnegative and Positive Matrix]]
- [[Entropy Minimization Algorithm]]
- [[Logarithmic Barrier Function and Central Path for Interior Point Methods]]

## Explanation

![[optimal_transport_entropy.png]]





-----------
##  Recommended Notes and References


- [[Linear Optimization Problem]]
- [[Mirror Descent Algorithm]]
- [[Generalized Proximal Method]]
- [[Entropy Minimization Algorithm]]
- [[Bregman Divergence Minimization]]
- [[Tikhonov Regularization in Optimization and Learning]]
- [[Optimal Transport in Space of Measures]]

- [[Perron-Frobenius Theorem on Irreducible Nonnegative Matrix]]

- [[Computational Optimal Transport by Peyre]] pp 57 - 62
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 314 - 315