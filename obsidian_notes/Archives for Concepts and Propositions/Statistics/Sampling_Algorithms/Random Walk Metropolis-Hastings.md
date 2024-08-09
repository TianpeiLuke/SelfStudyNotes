---
tags:
  - concept
  - statistics/monte_carlo_simulation
keywords:
  - random_walk_metropolis_hastings
  - metropolis_hastings_algorithm
topics:
  - monte_carlo
name: Random Walk Metropolis-Hastings
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Random Walk Metropolis-Hastings

![[Metropolis-Hastings Algorithm#^f582b7]]


>[!important] Definition
>Assume that there exists a **symmetric kernel function** $K_{\sigma}(\cdot)$ such that the *proposal distribution* can be reformulated as $$p(y|x) = K_{\sigma}(\lVert x - y \rVert), \quad \forall  x, y \in \mathcal{X}$$ where $\lVert \cdot \rVert$ is a norm in $\mathcal{X}$ and $\sigma >0$ is the **radius** that control the *range* of *exploration*. 
>
>Moreover, the kernel function $K_{\sigma}: \mathbb{R} \to \mathbb{R}$ has the following properties
>- $$K_{\sigma}(d) = K_{\sigma}(-d).$$
>- $$K_{\sigma}(d) > 0,\; \; \forall d \le \delta.$$
>
>
>
> The **Random-walk Metropolis-Hastings** is described as below:
>- *Require*: parameter $\epsilon >0$ and $\sigma >0$ that controls the range of random exploration
>- *Require*: kernel function $K_{\sigma}(\cdot)$ to generate perturbations
>- *Initialize* configuration $X_{0}$
>- For $t=0,\,1\,{,}\ldots{,}\,$
>	- **Generate** a random **jump (perturbation)** $\xi_{t}$ from kernel $$\xi_{t} \sim K_{\sigma}(\epsilon)$$ 
>	- Generate a new **proposal** by $$Y = X_{t} + \xi_{t}$$
>	- Compute the **Hastings ratio**: $$\begin{align}r(X_{t}\,, Y):= &\frac{\pi(Y)}{\pi(X_{t})} \end{align}$$ 
>	- **Metropolis Rejection**: Generate a **uniform** random variable $U\in \mathcal{U}[0,1]$.
>		- **Accept** $X_{t+1} = Y$ if $$U \le \min\{1, \; r(X_{t}, Y)\};$$
>		- **Otherwise** accept $X_{t+1} = X_{t}$

- [[Metropolis-Hastings Algorithm]]


## Explanation

>[!info]
>Random-walk Metropolis is not only **simple to implement**, it also has a particularly nice **intuition**. 
>
>- The **proposol distribution** is biased towards **large volumes**, measured by $K_{\sigma}(\cdot)$, and hence away from the **tails** of the target distribution. 
>- the **Metropolis correction** *rejects* those proposals that jump into *neighborhoods* where **the density is too small** $(\pi(x^{(t)}))$. 
>- The combined procedure then preferentially selects out those proposals that fall into *neighborhoods of high probability mass*, concentrating towards the **typical set** as desired.





-----------
##  Recommended Notes and References


- [[Markov Chain Monte Carlo Methods]]
- [[Diffusion Process]]


- [[Metropolis-Hastings Algorithm]]
- [[Markov Chain and Markov Process]]
- [[Hamiltonian Monte Carlo]]


- [[All of Statistics A Concise Course by Wasserman]] pp 411
- [[Monte Carlo Statistical Methods by Robert]]
- [[Monte Carlo Strategies in Scientific Computing by Liu]]

- Wikipedia [Metropolis-Hastings_algorithm](https://en.wikipedia.org/wiki/Metropolis%E2%80%93Hastings_algorithm)