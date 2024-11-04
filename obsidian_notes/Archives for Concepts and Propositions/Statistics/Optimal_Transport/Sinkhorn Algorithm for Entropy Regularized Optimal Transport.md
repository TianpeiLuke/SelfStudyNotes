---
tags:
  - concept
  - math/optimal_transport
  - optimization/algorithm
  - optimization/theory
keywords:
  - sinkhorn_algorithm_optimal_transport
  - entropic_regularization
  - optimal_transport
topics:
  - optimal_transport
  - optimization/theory
name: Sinkhorn Algorithm for Entropy Regularized Optimal Transport
date of note: 2024-10-17
---

## Concept Definition

>[!important]
>**Name**: Sinkhorn Algorithm for Entropy Regularized Optimal Transport

![[Entropic Regularized Optimal Transport in Discrete Settings#^c5a6e6]]

- [[Entropic Regularized Optimal Transport in Discrete Settings]]
- [[Optimal Transport in Discrete Setting]]

![[Entropic Regularized Optimal Transport in Discrete Settings#^9fefcb]]

- [[Entropy Minimization Algorithm]]
- [[Bregman Divergence Minimization]]
- [[Generalized Proximal Method]]
- [[Hadamard Product of Matrices]]

>[!important] Definition
>Consider the *entropic-regularized Kantarovich optimal transport*
>$$
>\begin{align*}
>\min_{P_{i,j} \in \mathbb{R}_{+}^{n \times m}} & \sum_{i,j}C_{i,j} P_{i,j} + \epsilon \sum_{i,j}P_{i,j}\left(\log(P_{i,j}) - 1\right) \\
\text{s.t. }&  \sum_{j=1}^{m}P_{i,j} = a_{i}, \quad 1 \le i \le n \\
&\sum_{i=1}^n P_{i,j}  = b_{j}, \quad 1 \le j \le m   \\
&P_{i,j} \ge 0 \nonumber
\end{align*}
>$$
>- The optimal *transportation plan* is of the form $$\begin{align}P_{i,j} &= u_{i}\,K_{i,j}\,v_{j} \quad \forall i\in [n], j\in [m]\end{align}$$ where $$K_{i,j} = \exp \left(- \frac{C_{i,j}}{\epsilon}\right), \quad i\in [n], j\in [m]$$
>- The *scaling factor* $u$ and $v$ can be found via the **matrix scaling problem** $$u \odot \left(Kv\right)  = a$$  and $$v \odot\left(K^{T} u\right)  = b$$
>
>The **Sinkhorn algorithm** that solves the above *matrix scaling problem* iteratively is described as follows:
>- *Require*: the *cost matrix* $C = [C_{i,j}] \in \mathbb{R}_{+}^{n\times m}$ for $i\in [n]$ and $j\in [m]$, and *equality constraint* vector $a\in \mathbb{R}^{n}$ and $b\in \mathbb{R}^{m}$
>- *Require*: the *entropy regularization* parameter $\epsilon >0$
>- Construct the **kernel** $$K_{i,j} = \exp \left(- \frac{C_{i,j}}{\epsilon}\right), \quad i\in [n], j\in [m]$$
>- Initialize $u_{0}$ and $v_{0}$
>- For $t=0,\,1\,{,}\ldots{,}\,$ until convergence:
>	- Update **scaling factor** for *source* $u$, $$u_{t+1} \leftarrow \frac{a}{K\,v_{t}}$$ 
>		- or $$u_{t+1}^{i} \leftarrow \frac{a^{i}}{\left\langle  K_{i,:}\,,\,v_{t}  \right\rangle}, \quad i=1\,{,}\ldots{,}\,n$$
>	- Update **scaling factor** for *target* $v$, $$v_{t+1} \leftarrow \frac{b}{K^{T}\,u_{t+1}}$$ 
>		- or $$v_{t+1}^{j} \leftarrow \frac{b^{j}}{\left\langle  K_{:,j}\,,\,u_{t+1}  \right\rangle}, \quad j=1\,{,}\ldots{,}\,m$$
>- *Return*: 
>	- $u^{*}\in \mathbb{R}^{n}$ and $v^{*}\in \mathbb{R}^{m}$
>	- the optimal transportation plan $$\begin{align}P_{i,j} &= u_{i}^{*}\,K_{i,j}\,v_{j}^{*} \quad \forall i\in [n], j\in [m]\end{align}$$

- [[Fixed Point of Map]]
- [[Contraction Map Principle]]


## Explanation





-----------
##  Recommended Notes and References


- [[Entropy Minimization Algorithm]]
- [[Linear Optimization Problem]]
- [[Logarithmic Barrier Function and Central Path for Interior Point Methods]]
- [[Stochastic Matrix and Doubly Stochastic Matrix]]
- [[Optimal Assignment Problem and Monge Problem]]

- [[Perron-Frobenius Theorem on Irreducible Nonnegative Matrix]]



- [[Computational Optimal Transport by Peyre]] pp 63 - 84