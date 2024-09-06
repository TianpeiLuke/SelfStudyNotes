---
tags:
  - concept
  - statistics/monte_carlo_simulation
keywords:
  - particle_filter
  - boostrap_sampling
topics:
  - statistics/monte_carlo
name: Particle Filter
date of note: 2024-07-04
---

## Concept Definition

>[!important]
>**Name**: Particle Filter or *Sampling-Importance-Resampling*

>[!important] Definition
>Assume $\xi_{k} \in \mathbb{R}^{d}$ is the **state** at time $k$ and $y_{k}$ is the **observation** at time $k$. $\xi_{1:t} = [\xi_1, \ldots, \xi_{t}] \in \mathbb{R}^{d \times t}$ is the **trajectory of states** up to $t$. 
>
>Assume that $(\xi_{t}, y_{t})_{t}$ follow the **state-space model**
>$$
> \begin{align*}
> \xi_{t} &\sim q_{t}(\xi_{t} \,|\, \xi_{t-1},\, \theta) &\quad (\text{state equation})\\
> y_{t} &\sim f_{t}(y_t \,|\, \xi_{t},\, \phi) &\quad (\text{observation equation})
> \end{align*}
>$$
>Consider the task of the **online estimation** and **prediction** (**filtering**) of the state $\xi_{t}$ given a sequential observations $y_{1:t} = (y_{1}\,{,}\ldots{,}\,y_{t}).$  
>
>The **optimal online estimation** is the *conditional mean estimator*
>$$
>\bar{\xi}_{t} =  \mathbb{E}\left[ \xi_{t} \,|\,  y_{1}\,{,}\ldots{,}\,y_{t} \right]
>$$

- [[State-Observation Models]] 
- [[State Space Models and Nonlinear Dynamic System]]


>[!important] Definition
>Consider the task of approximation of  the *belief states*, i.e. the **filtering task**
>$$
>\bar{\xi}_{t} =  \mathbb{E}\left[ \xi_{t} \,|\,  y_{1}\,{,}\ldots{,}\,y_{t} \right]
>$$
>
>The **particle filter** or **boostrap filter** or **Sampling-Importance-Resampling (SIR)**  is described as below:
>
>- *Require*: the *state equations* $\left\{ q_{t}(\xi_{t}\,|\,\xi_{t-1}, \theta),\, t\in [T] \right\}$ with parameter $\theta$
>- *Require*: the *observation equations* $\left\{ f_{t}(y_{t}\,|\,\xi_{t},\, \phi),\, t\in [T] \right\}$ with parameter $\phi$
>- *Require*:  a sequence of *observations* $y_{[T]} = (y_{1} \,{,}\ldots{,}\,y_{T})$
>- *Initialize* a sequence of sample weights $w_{0}^{(j)} = \frac{1}{m},$ $j=1\,{,}\ldots{,}\,m$
>- *Initialize* a sequence of sample states $\xi_{0}^{(j)}$, $j=1\,{,}\ldots{,}\,m$
>- For $t= 1 \,{,}\ldots{,}\,T$
>	- For $j= 1\,{,}\ldots{,}\,m$
>		- Generate a **bootstrap sample** $\xi_{t}^{(*,j)}$ from the **state equation** $q_{t}(\cdot|\xi_{t-1},\,\theta)$  $$\xi_{t}^{(*,j)} \sim q_{t}(\cdot\, | \, \xi_{t-1}^{(j)}, \theta)$$
>		- Update the **importance weight** for each sample via product of **observation equation** and previous *normalized weights* $$\widetilde{w}_{t}^{(j)} = f_{t}(y_{t} \,|\, \xi_{t}^{(*,j)}, \phi)\times \;w_{t-1}^{(j)}$$
>	- **Normalize weight** $\widetilde{w}_{t}^{(j)}$ as $w_{t}^{(j)}$ i.e. $$w_{t}^{(j)} = \frac{\widetilde{w}_{t}^{(j)}}{\sum_{j=1}^{m}\widetilde{w}_{t}^{(j)}},\quad j=1\,{,}\ldots{,}\,m$$
>	- **Resample** a random sample $$\{\xi_{t}^{(1)}, \ldots, \xi_{t}^{(m)}\}$$ from $$\{\xi_{t}^{(*,1)}, \ldots, \xi_{t}^{(*,m)}\}$$ according to **multinomial distribution** with probability $(w_{t}^{(1)}\,{,}\ldots{,}\,w_{t}^{(m)})$
>	- *Output*: The **conditional mean estimator** at time $t$ is approximated by sample mean $$\hat{\xi}_{t} = \frac{1}{m}\sum_{j=1}^{m}\xi_{t}^{(j)}$$

- [[Bayesian Filtering and Smoothing Equations for State Observation Models]]
- [[Linear Dynamic System]]
- [[Kalman Filter Discrete-Time]]

- [[Bootstrap Method]]
- [[Multinomial Random Variable]]
- [[Roulettle Wheel Algorithm to Resample from CDF]]


## Explanation


>[!important] 
>The **particle filter** (or **boostrap filter**) is proposed to fix the *particle degeneracy* by  **weight resampling**.



-----------
##  Recommended Notes and References


- [[Sequential Importance Sampling]]
- [[Bootstrap Method]]
- [[Importance Sampling]]
- [[Kalman Filter Discrete-Time]]

- [[Feynman-Kac Formula]]

- [[Conditional Expectation]]
- [[Exponential Weights Algorithm for Convex Loss]]


- [[Monte Carlo Strategies in Scientific Computing by Liu]] pp 66-101
- [[Monte Carlo Statistical Methods by Robert]] pp 552

- [[Deep Learning Foundations and Concepts by Bishop]] pp 439
- [[Probabilistic Graphical Models by Koller]] pp 667
- Wikipedia [Particle_filter](https://en.wikipedia.org/wiki/Particle_filter)