---
tags:
  - concept
  - optimization/theory
  - evolutionary_algorithm
  - evolutionary_computation
  - swam_intelligence
keywords:
  - particle_swam_optimization
  - swam_intelligence
topics:
  - optimization/algorithm
  - swam_intelligence
name: Particle Swarm Optimization
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: Particle Swarm Optimization

>[!info]
>**Particle swarm optimization (PSO)** is a *population-based* *stochastic optimization algorithm* motivated by intelligent collective behavior of some animals such as flocks of birds or schools of fish.

>[!important] Definition
>In **Particle swarm optimization (PSO)**, every member in population is represented by a pair $(x, p)$ where
>- $x\in \mathbb{R}^{n}$ is a **candidate solution** vector.
>- $p \in \mathbb{R}^{n}$ is a **perturbation** vector, which decides how the solution $x$ is changed to produce an *offspring*.
>  
>The **main idea** is that a new pair $(x' ,v')$ is produced by $(x,v)$ by
>- first computing a *new perturbation vector* $v'$
>- then *add this perturbation vector* to $x$ to produce $x'$, i.e. $$x' = x + p'.$$

>[!important] Definition
>For $i$-th **swam member**, the **new velocity vector** $v_{i}'$ is determined by *three components*:
>- the **current velocity** for the  $i$-th candidate $v_{i}$
>- the **difference** from the **current position**  $x_{i}$ to the **best ever position** $b_{i}$ for the **individual candidate** in its past history $$(b_{i} - x_{i})$$
>- the **difference** from the **current position** $x_{i}$ to the  **best ever position** $c$ for the **entire population** in its past history $$(c - x_{i})$$
>  
>In particular,
>$$
>v_{t+1}^{i} = w\,v_{t}^{i} + \phi_{1}\,U_{1}\,\left(b_{t}^{i} - x_{t}^{i}\right) + \phi_{2}\,U_{2}\,\left(c_{t} - x_{t}^{i}\right)
>$$  
>where
>-  $w \in \mathbb{R}$ is called the **inertia**
>- $\phi_{1}, \phi_{2} \in \mathbb{R}$ are called **learning rate** for **personal influence** and **social influence**, respectively. 
>- $U_{1}, U_{2}$ are **random diagonal matrices** whose diagonal entities are drawn from *uniform distribution* in $[0,1]$

>[!important] Definition
>Consider the optimization problem
>$$
> \min_{x\in \mathcal{X}}\; f(x)
>$$
>
>**Particle swarm optimization (PSO)** solves above problem as follow
>- *Require*: fitness function $f$
>- *Require*: **inertia** $w\in \mathbb{R}$
>- *Require*: **learning rate** for **personal influence** and **social influence** $\phi_{1}, \phi_{2} \in \mathbb{R}$
>- *Require*: initial population of size $\lambda$ $$\mathcal{S}_{0} = \left\{ (x_{0}^{1}, v_{0}^{1}, b_{0}^{1}) \,{,}\ldots{,}\,  (x_{0}^{\lambda}, v_{0}^{\lambda}, b_{0}^{\lambda})\right\} $$ where 
>	- $x_{0}^{i}\in \mathbb{R}^{n}$, $v_{0}^{i} \in \mathbb{R}^{n}$, $b_{0}^{i} = x_{0}^{i}$
>- *Initialize* the population's **global best solution** (**champion**) $$c_{0} = \arg\min_{i=1\,{,}\ldots{,}\,\lambda}f(b_{0}^{i})$$
>- For $t=0\,,1\,{,}\ldots{,}\,$ until termination condition is met
>	- For each *particle* in **swam** $i=1\,{,}\ldots{,}\,\lambda$ 
>		- Generate two *random diagonal matrices* with diagonal entities drawn from *uniform distribution* in $[0,1]$ $$U_{1}[i,i],\;  U_{2}[i,i] \sim \text{Uniform}[0,1], \;i=1\,{,}\ldots{,}\,n$$
>		- *Compute* the **new velocity** $$v_{t+1}^{i} =  w\,v_{t}^{i} + \phi_{1}\,U_{1}\,\left(b_{t}^{i} - x_{t}^{i}\right) + \phi_{2}\,U_{2}\,\left(c_{t} - x_{t}^{i}\right)$$
>		- *Move* the **position** from $x_{t}^{i}$  by a new velocity $v_{t+1}^{i}$ $$x_{t+1}^{i} = x_{t}^{i} + v_{t+1}^{i}$$
>		- *Update* the **personal best position** in history $$b_{t+1}^{i} = \left\{\begin{array}{ll}x_{t}^{i} & \text{ if }f(x_{t+1}^{i}) < f(b_{t}^{i})\\ b_{t}^{i} & \text{ otherwise} \end{array} \right.$$
>	- Update the **population (swam)** $$\mathcal{S}_{t+1} = \left\{ (x_{t+1}^{1}, v_{t+1}^{1}, b_{t+1}^{1}) \,{,}\ldots{,}\,  (x_{t+1}^{\lambda}, v_{t+1}^{\lambda}, b_{t+1}^{\lambda})\right\} $$
>	- Update the population's **global best solution** (**champion**) $$c_{t+1} = \arg\min_{i=1\,{,}\ldots{,}\,\lambda}f(b_{t+1}^{i})$$




## Explanation

>[!important]
>PSO is a **stochastic** and **parallel optimization algorithm**. 
>
>Its **advantages** can be summarized as follows: 
>- It does *not require* the optimized functions *differential, derivative and continuous*; 
>- its *convergence rate* is fast; 
>- and the algorithm is *simple* and easy to execute through programming.

>[!quote]
>Unfortunately, it also has some **disadvantages** (Wang 2012):
>- For the functions with **multiple local extremes**, it probably falls into the local extreme and cannot get correct result. 
>	- Two reasons result in this phenomenon: 
>		- One is the **characteristics** of the *optimized functions* and 
>		- the other is the **particles’ diversity** disappearing quickly, causing premature convergence. These two factors are usually inextricably intertwined.
>- Due to lack of **cooperation** of good *search methods*, PSO algorithm cannot get satisfactory results. 
>	- The reason is that the PSO algorithm **does not sufficiently use** the information obtained in the calculation procedure. During each iteration, instead it only uses the information of **the swarm optima** and **individual optima**.
>- Though PSO algorithm provides the possibility of global search, it **cannot guarantee convergence** to the global optima.
>- PSO algorithm is a **meta-heuristic bionic optimization algorithm**, and there is no rigorous theory foundation so far. 
>	- It is designed only through simplifying and *simulating the search phenomenon of some swarms*, but it neither explains why this algorithm is effective from the principle, nor specifies its applicable range. 
>
>Therefore, PSO algorithm is generally suitable for a class of optimization problems which are **high dimensional** and need *not to get very accurate* solutions.



>[!quote]
>Similarly to **Differential Evolution**, the distinguishing feature of **PSO** is a twist to the usual reproduction operators in EC: *PSO* **does not use crossover** and its **mutation** is defined through a *vector addition*. However, PSO differs from DE and most other EC dialects in that every candidate solution $x \in \mathbb{R}^{n}$ carries its *own perturbation vector* $p \in \mathbb{R}^{n}$. Technically, this makes them quite similar to **evolution strategies** that use the mutation step sizes in the perturbation vector parts. However, the **PSO mindset** and terminology is based on a *spatial metaphor* of *particles* with a **location** and **velocity**, rather than a biological one of individuals with a genotype and mutation.
>
>-- [[Introduction to Evolutionary Computing by Eiben]] pp 112

- [[Differential Evolution Algorithm]]
- [[Evolutionary Strategies]]

>[!quote]
>**PSO algorithm** can be summarized as follows: PSO algorithm is a kind of **searching process** based on **swarm**, in which each individual is called a **particle** defined as a *potential solution* of the optimized problem in $D$-dimensional search space, and it can **memorize the optimal position** of the **swarm** and that of **its own**, as well as the **velocity**. In each generation, the particles information is combined together to *adjust* the velocity of each dimension, which is used to compute the new position of the particle. Particles change their states constantly in the multi-dimensional search space, until they **reach balance** or optimal state, or beyond the calculating limits. Unique connection among different dimensions of the problem space is introduced via the objective functions.
>
>-- Wang, D., Tan, D., & Liu, L. (2018). Particle swarm optimization algorithm: an overview. _Soft computing_, _22_(2), 387-408. pp 2





## Tangent Bundle and Phase Space


>[!important] 
>The **core** of the **PSO perspective** is to consider a population member as a *particle* in **phase space** as $(x, v)$ with a **position** $x$ and a **velocity** $v$ and use the latter to determine a *new position* (and a *new velocity*).


- [[Tangent Bundle]]
- [[Phase Space of Hamiltonian Systems of Differential Equations]]





-----------
##  Recommended Notes and References


- [[Ant Colony Optimization]]
- [[Evolutionary Computation Algorithms]]
- [[Derivative-Free Optimization]]

- [[Parent Selection for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]

- [[Tangent Bundle]]



- [[Introduction to Evolutionary Computing by Eiben]] pp 112
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 298 - 307
- Wikipedia [Particle_swarm_optimization](https://en.wikipedia.org/wiki/Particle_swarm_optimization)