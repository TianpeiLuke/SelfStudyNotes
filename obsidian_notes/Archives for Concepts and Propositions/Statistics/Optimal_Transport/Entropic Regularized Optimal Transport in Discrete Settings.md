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

^c5a6e6

- [[Theory and Algorithms for Convex Optimization]]
- [[Nonnegative and Positive Matrix]]
- [[Entropy Minimization Algorithm]]
- [[Logarithmic Barrier Function and Central Path for Interior Point Methods]]

## Explanation

![[optimal_transport_entropy.png]]

## Solution 

>[!important] Proposition
>The **optimal coupling** to the *entropic-regularized Kantarovich optimal transport*
>$$
>\begin{align*}
>\min_{P_{i,j} \in \mathbb{R}_{+}^{n \times m}} & \sum_{i,j}C_{i,j} P_{i,j} + \epsilon \sum_{i,j}P_{i,j}\left(\log(P_{i,j}) - 1\right) \\
\text{s.t. }&  \sum_{j=1}^{m}P_{i,j} = a_{i}, \quad 1 \le i \le n \\
&\sum_{i=1}^n P_{i,j}  = b_{j}, \quad 1 \le j \le m   \\
&P_{i,j} \ge 0 \nonumber
\end{align*}
>$$
>is **unique** and has the form
>$$
> \begin{align}
> P_{i,j} &= u_{i}\,K_{i,j}\,v_{j} \quad \forall i\in [n], j\in [m]
> \end{align} 
>$$ 
> where 
> - $$K_{i,j} = \exp \left(-\frac{C_{i,j}}{\epsilon}\right)$$ is the **Gibbs distribution**. 
> - and $(u, v) \in \mathbb{R}_{+}^{n} \times \mathbb{R}_{+}^{m}$ are two (unknown) **scaling variables**
>
>We can represent the solution in **matrix form**
>$$
>\begin{align}
> P^{*} &= \text{diag}(u)\,\exp\left(-\frac{C}{\epsilon}\right)\,\text{diag}(v)
>\end{align} 
>$$
>which is a **doubly stochastic matrix**.
>- The **scaling factor** $u$ and $v$ are define by the equality constraint $$u \odot \left(\exp\left(-\frac{C}{\epsilon}\right)v\right)  = a$$  and $$v \odot\left(\exp\left(-\frac{C^{T}}{\epsilon}\right) u\right)  = b$$

^9fefcb

- [[Entropy Minimization Algorithm]]
- [[Gibbs Measure and Energy-based Model]]
- [[Linear Optimization Problem]]
- [[Logarithmic Barrier Function and Central Path for Interior Point Methods]]
- [[Stochastic Matrix and Doubly Stochastic Matrix]]
- [[Hadamard Product of Matrices]]

>[!important] Definition
>The problem of finding $u, v$ that satiesfies the equation
> $$\begin{align*}
>u \odot \left(\exp\left(-\frac{C}{\epsilon}\right)v\right)  &= a \\[5pt]
>v \odot\left(\exp\left(-\frac{C^{T}}{\epsilon}\right) u\right)  &= b
>\end{align*}$$ 
>
>This problem is known in the numerical analysis community as the **matrix scaling problem**.
>- We can use **SInkhorn algorithm** to solve the matrix scaling problem.

- [[Sinkhorn Algorithm for Entropy Regularized Optimal Transport]]

### Proof

>[!info]
>We introduce the **dual variable** $\lambda$ and $\mu$ for each *marginal constraint*. 
>
>The Lagrangian is 
>$$
> \begin{align*}
> L(P, \lambda, \mu) := \left\langle P\,,\, C \right\rangle_{F} - \epsilon H(P) - \left\langle  \lambda\,,\, P\,1_{m} - a \right\rangle -  \left\langle  \mu\,,\, P^{T}\,1_{n} - b  \right\rangle
> \end{align*}
>$$  
>
>The **KKT condition** yields
>$$
> \begin{align*}
> \frac{ \partial  }{ \partial P } L(P, \lambda, \mu)   &= C + \epsilon \log P  - \lambda 1_{m}^{T} - 1_{n}\mu^{T} = 0 \\
> \implies & -\frac{1}{\epsilon}\left(C -  \lambda 1_{m}^{T} - 1_{n}\mu^{T}\right)  = \log P \\
> P &= \exp \left\{-\frac{1}{\epsilon}\left(C -  \lambda 1_{m}^{T} - 1_{n}\mu^{T}\right)\right\} \\
> \implies P_{i,j}&= \exp\left( \frac{\lambda_i}{\epsilon} \right)\exp\left( -\frac{C_{i,j}}{\epsilon} \right)\exp\left( \frac{\mu_j}{\epsilon} \right) \\[5pt] 
> &:= u_i K_{i,j} v_{j}
> \end{align*}
>$$  
>where the **matrix scaling factor** $$u = [\exp(\lambda_i / \epsilon)] = \exp(\lambda/\epsilon)$$ and $$v =  [\exp(\mu_j / \epsilon)] = \exp(\mu/\epsilon).$$

- [[Methods of Lagrangian Multipliers]]
- [[Entropy Functional]]
- [[Karush-Kuhn-Tucker Optimality Condition]]





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