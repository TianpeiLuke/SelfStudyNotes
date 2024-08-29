---
tags:
  - concept
  - statistics/monte_carlo_simulation
  - optimization/algorithm
keywords:
  - simulated_annealing
  - gradient_free_optimization
topics:
  - statistics/monte_carlo
name: Simulated Annealing
date of note: 2024-07-04
---

## Concept Definition

>[!important]
>**Name**: Simulated Annealing

![[Gibbs measure#^bfb840]]

- [[Gibbs measure]]

>[!important] Definition
>Consider the **energy maximization problem** $$x^{*} = \arg\max_{x\in \mathcal{X}}\,E(x)$$ where  $E(x)$ is called the **energy** of the system.
>
  The **simulated annealing** find the optimal solution by generating a sequence of sample $X_{t},\; t=1\,{,}\ldots{,}\,$ according to *Gibbs measures* $P_{t}$ where the p.d.f. is given by  $$\pi_{t}(x) = \frac{1}{Z}\,\exp \left(- \frac{E(x)}{T_{t}}\right)$$ where $E(x)$ is the **energy** of the system and $T_{t} >0$ is called the **temperature**. 
>
>As the temperature $$T_{t} \to 0,$$ the values simulated from this distribution become *concentrated* in a narrower and narrower *neighborhood* of the **local maxima** of $E$.

- [[Monte Carlo and Applications]]
- [[Stochastic Hill Climbing]]

>[!important] Definition
>The **Simulated Annealing (SA) algorithm** can be implemented as 
>- Simulate $\xi$ from an **instrumental distribution** with density $$g(\lVert \xi - X_{t} \rVert);$$
>- **Accept** $X_{t+1} = \xi$ with **probability**
>$$ 
> \begin{align*}
> \alpha(X_t, \xi)&= \min\left\{ 1, \exp \left(\frac{\Delta E_{t}}{T_{t}}\right) \right\} 
> \end{align*}
>$$  
>where the energy difference $$\Delta E_t := E(\xi) - E(X_t);$$
>- Otherwise, *accept* $X_{t+1} = X_t$.
>- **Decrease temperature** $T_{t}$ to $T_{t+1}$.
>

- [[Accept-Reject Sampling]]

### Combining with MCMC


>[!info]
>The sampling according to the Gibbs measure can be implemented using **Markov Chain Monte Carlo methods**.

- [[Markov Chain Monte Carlo Methods]]

>[!important] Definition
>The **Simulated Annealing algorithm** with **MCMC** can be implemented as 
>- *Initialize* configuration $X_{1}$
>- For $t=1 \,{,}\ldots{,}\,$ until convergence
>	- Let $Y^{1} = X_{t}$
>	- For $k = 1\,{,}\ldots{,}\,$ until mixed
>		- **Generate** $\xi$ given $Y^{k}$, according to a **symmetric proposal function** $p(\cdot|\cdot)$,  $$\xi \sim  p(\xi \,|\, Y^{k})$$
>		- Compute the **difference** in **energy**  $$\Delta E^{k} := E(\xi) -  E(Y^{k})$$
>		- Generate a **uniform** random variable $U\in \mathcal{U}[0,1]$.
>			- **Accept** $Y^{k+1} = \xi$ if $$U \le \frac{\pi(\xi)}{\pi(Y^{k})} := \exp \left( - \frac{\Delta E^{k} }{T_{t}}\right);$$
>			- **Otherwise** accept $Y^{k+1} =  Y^{k}$
>	- When the chain mixed at iteration $N_{t}$, accept $$X_{t+1} = Y^{N_{t}}$$
>	- **Decrease temperature** $T_{t}$ to $T_{t+1}$.
>

- [[Metropolis-Hastings Algorithm]]
- [[Gibbs Sampling]]

>[!info]
>For high dimensional distribution $p$, we can use [[Probabilistic Graphical Models]] such as [[Bayesian Network on Directed Acyclic Graph]].

## Explanation

>[!important]
>The **fundamental idea** of *simulated annealing methods* is that a change of scale, called **temperature**, allows for *faster moves* on the surface of the function $h$ to maximize, whose negative is called **energy**. Therefore, *rescaling* partially avoids the *trapping* attraction of *local maxima.*

- [[Saddle Point of Lagrangian Function]]

>[!info]
>Since there is *non-zero probability* of accepting a new proposal even if it is *not local maximal*, it allows the algorithm to **escape the attraction** of $x_t$ if $x_t$ is a **local maximum** of $E$. 
>
>The temperature $T_{t}$ controls the **probability of acceptance** of non-optimal proposal.

>[!info]
>It can be shown that the **global optimum** of $E(x)$ can be reached by **Simulated Annealing** algorithm with probability $1$ if the temperature variable $T_t$ **decreases sufficiently slowly**, i.e., at the order of $$\mathcal{O}(\log(L_t)-1),$$ where $$L_k = N_1 +\ldots + N_k,$$ and  $N_k$ is the number of *iterations of MCMC* at time $t$. 
>
>In practice, however, no one can afford to have such a slow annealing schedule. Most frequently, people use a **linear** or even **exponential temperature decreasing schedule**, which can no longer guarantee that the global optimum will be reached.
>
>--  [[Monte Carlo Strategies in Scientific Computing by Liu]] 


## Stochastic Local Search


>[!important]
>Simulated annealing is a **stochastic hill climbing algorithm**, where at each iteration, the generated samples improve the energy by concentrated in a *narrower neighborhood* of the *local maxima* of $E$
>$$
>x_{k+1} \in \arg\max_{x\in B(x^{*}; d_{k})}E(x)
>$$
>
>It requires no gradient from the energy function which is a **derivative-free optimization**

- [[Stochastic Hill Climbing]]





-----------
##  Recommended Notes and References


- [[Gibbs measure]]
- [[Stochastic Hill Climbing]]
- [[Derivative-Free Optimization]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Monte Carlo Statistical Methods by Robert]] pp 163 - 172, 209, 287, 315
- [[Monte Carlo Strategies in Scientific Computing by Liu]] pp 209

- [[Probabilistic Graphical Models by Koller]] pp 524
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 301
- [[Introduction to Evolutionary Computing by Eiben]] pp 47, 142
- [[Artificial Intelligence Modern Approach by Russell]]
