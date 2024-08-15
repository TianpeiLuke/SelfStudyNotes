---
tags:
  - concept
  - statistics/monte_carlo_simulation
  - math/differential_equation_simulation
keywords:
  - hamiltonian_monte_carlo
topics:
  - statistics/monte_carlo
  - differential_equation
name: Hamiltonian Monte Carlo
date of note: 2024-07-04
---

## Concept Definition

>[!important]
>**Name**: Hamiltonian Monte Carlo

![[Hamiltonian Systems of Differential Equations#^ad0948]]

- [[Hamiltonian Systems of Differential Equations]]

### Definition of Hamiltonian Dynamic for Sampling from given P.D.F.

>[!important] Definition
>Consider the task of generating samples $\left\{ X_{1} \,{,}\ldots{,}\,X_{n}\,{,}\ldots \right\}$ so that
>$$X_{i} \sim F, \quad i=1 \,{,}\ldots$$ 
>where $$F(x) := \exp \left( - f(x) - \log Z \right)$$ is the probability density function of $X$ with respect to Lebesgue measure. The function $f: \mathbb{R}^n \to \mathbb{R}$ is called the **(potential) energy function** and $$\log Z = \log \int \exp \left( - f(x) \right) dx$$ is the *log-partition function*.
>
>The **Hamiltonian Monte Carlo (HMC)** *method* or the **Hybrid Monte Carlo** method achieves this task via *Hamiltonian dynamics*. In particular,
>- We introduce auxiliary *independent momentum random variables* $P \in \mathbb{R}^{n}$ so that the *joint p.d.f.* is a Gibbs measure. $$\pi(x, p; T) := \exp \left( - \frac{H(x, p)}{T} - \log Z \right)$$
>- Define the energy function of joint probability as the *Hamiltonian* $$H(x, p) = f(x) + K(p)$$ where $K: \mathbb{R}^{n} \to \mathbb{R}_{+}$ is the **kinetic energy term**. Assume that the kinetic energy term is of the *quadratic form* $$K(p) = \sum_{i=1}^{n}\frac{(p^{i})^2}{2 \sigma_{i}^2} = \frac{1}{2} \left\langle  \Lambda^{-1}\,p,  p\right\rangle.$$ where $\Lambda = \text{diag}\left\{ \sigma_{1}^2 \,{,}\ldots{,}\,\sigma_{n}^2 \right\}.$
>- The Hamiltonian follows the *system of differential equations*
>$$
>\left\{\begin{align*}
> \frac{d}{dt} x^{i} &= \frac{ \partial H }{ \partial p^{i} } = \frac{p_{i}}{\sigma_{i}^2}, \quad i=1 \,{,}\ldots{,}\, n \\[5pt]
> \frac{d}{dt} p^{i} &= - \frac{ \partial H }{ \partial x^{i} } = - \frac{ \partial}{ \partial x^{i} }f(x), \quad i=1 \,{,}\ldots{,}\, n
>\end{align*}
>\right.
>$$
>In compact form, we have 
>$$
>\left\{\begin{align*}
> \frac{d}{dt} x &= \Lambda^{-1}\,p \\
> \frac{d}{dt} p &= - \nabla f(x)
>\end{align*}
>\right.
>$$
>- The *solution* of Hamiltonian system of differential equations forms a **Hamiltonian flow**  $$\theta_{t}: (x, p) \mapsto (x_{t}(x,p), p_{t}(x, p))$$ as the position and momentum of the particle after time $t$ staring from $(x,p).$

- [[Radon-Nikodym Derivative]]
- [[Gibbs measure]]
- [[Parametric Models]]
- [[Hamiltonian Systems of Differential Equations]]

### Hamiltonian Monte Carlo

>[!important] Definition
>An *idealized* **Hamiltonian Monte Carlo (HMC)** *method* or the **Hybrid Monte Carlo** method works as follows
>- Initialized with starting point $X_{0} \in \mathbb{R}^d$, $T >0$, $N \in \mathbb{N}$
>- Input *first-order oracle* for $f:\mathbb{R}^n \to \mathbb{R}$
>- For $k = 1 \,{,}\ldots{,}\, N$ 
>	- **Sample a momentum** $$\xi \sim \mathcal{N}(0, \Lambda)$$
>	- **Simulate Hamiltonian trajectory** $$(X_{k}, P_{k}) = \theta_{T}\left( X_{k-1}, \xi \right)$$
>- Output $X_{N}$
>  
>Each step of the *HMC Markov chain* $X_{1} \,{,}\ldots{,}\,$ is determined by *first sampling* a new *independent momentum* $\xi \sim \mathcal{N}(0, \Lambda)$, and then running Hamilton’s equations for *a fixed time* $T$ , that is $X_{i} = x_{T}(X_{i-1}, \xi).$

- Vishnoi, N. K. (2021). _An Introduction to Hamiltonian Monte Carlo Method for Sampling_ (arXiv:2108.12107). arXiv. pp 4

### Discretizing HMC (Leapfrog Method)

>[!info] 
>We can approximate the Hamiltonian dynamic with a **first-order Euler integrator**, which iteratively computes the *first-order Taylor expansions* $(\hat{x}_{\eta}, \hat{p}_{\eta})$ of Hamilton's equation.
>$$
>\begin{align*}
> \hat{p}_{\eta}(x, p) &= p + \eta\frac{d}{dt}\hat{p}_{t}(x, p)  \\
> &= p - \eta \nabla f(x)\\
> \hat{x}_{\eta}(x, p) &= x + \eta\frac{d}{dt}\hat{x}_{t}(x, p) \\
> &= x + \eta \frac{ \partial H }{ \partial p }(x, p)\\
> &= x + \eta \, \Lambda^{-1}\,p
>\end{align*}
>$$

>[!info] 
>uch better results can be obtained by slightly **modifying Euler’s method**, as follows
>$$
>\begin{align*}
> \hat{p}_{\eta}(x, p) &= p - \eta \nabla f(x)\\
> \hat{x}_{\eta}(x, p) &= x + \eta \, \Lambda^{-1}\,\hat{p}_{\eta}\\
>\end{align*}
>$$
>We simply use the **new value** for the *momentum variables*, $\hat{p}_{\eta}$, when *computing the new value* for the *position variables*, $\hat{x}_{\eta}$. A method with similar performance can be obtained by instead updating the $\hat{x}_{\eta}$ first and *using their new values* to update the $\hat{p}_{\eta}$.


>[!important] Definition (HMC Leapfrog)
>The **leapfrog method**  for **Hamiltonian Monte Carlo (HMC)** *method* works as follows
>- Initialized with starting point $X_{0} \in \mathbb{R}^d$, 
>- Set $T >0$, $N \in \mathbb{N}$, $\eta >0$
>- Input *first-order oracle* for $f:\mathbb{R}^n \to \mathbb{R}$
>- For $k = 1 \,{,}\ldots{,}\, N$ 
>	- **Sample a momentum** $$\xi \sim \mathcal{N}(0, \Lambda)$$
>	- Set $$q_{0} = X_{k-1}, \quad p_{0} = \xi$$
>	- For $j = 1 \,{,}\ldots{,}\,  T/\eta$:
>		- **Update momentum** with **half-step** $$\tilde{p}_{j} = p_{j-1} - \frac{1}{2}\,\eta\,\nabla f(q_{j-1})$$
>		- **Update position** $$q_{j} = q_{j-1} + \eta\,\Lambda^{-1}\,\tilde{p}_{j}$$
>		- **Update momentum**  with **new position** and **half-step** $$p_{j} = \tilde{p}_{j} - \frac{1}{2}\,\eta\,\nabla f(q_{j})$$
>	- Choose new sample as the end position$$X_{k} = q_{T / \eta}\left(X_{k-1}, \xi\right)$$
>- Output $X_{N}$

>[!info]
>It is shown in [^1] that the **Leapfrog integrator** requires a numerical step size of $O^{*}(d^{-1 / 4})$ to maintain an $\Omega(1)$ *Metropolis acceptance probability* in the limit as the dimension $d\to \infty$.

[1]: Mangoubi, O., & Vishnoi, N. (2018). Dimensionally tight bounds for second-order Hamiltonian Monte Carlo. _Advances in neural information processing systems_, _31_

>[!important] Definition (HMC Leapfrog with multiple steps and MH rejection)
>The **leapfrog method**  for **Hamiltonian Monte Carlo (HMC)** *method* works as follows
>- Initialized with starting point $X_{0} \in \mathbb{R}^d$, 
>- Set $T >0$, $N \in \mathbb{N}$, $\eta >0$
>- Input *first-order oracle* for $f:\mathbb{R}^n \to \mathbb{R}$
>- For $k = 1 \,{,}\ldots{,}\, N$ 
>	- **Sample a momentum** $$\xi \sim \mathcal{N}(0, \Lambda)$$
>	- Set $$q_{0} = X_{k-1}, \quad p_{0} = \xi$$
>	- **Update momentum** with **half-step** $$\tilde{p}_{0} = p_{0} - \frac{1}{2}\,\eta\,\nabla f(q_{0})$$
>	- For $j = 1 \,{,}\ldots{,}\,  T/\eta$:
>		- **Update position** $$q_{j} = q_{j-1} + \eta\,\Lambda^{-1}\,\tilde{p}_{j}$$
>		- **Update momentum**  $$\tilde{p}_{j} = \tilde{p}_{j-1} - \eta\,\nabla f(q_{j})$$
>	- **Update momentum**  with **new position** and **half-step** $$p_{T/\eta} = \tilde{p}_{T/\eta} - \frac{1}{2}\,\eta\,\nabla f(q_{T/\eta})$$
>	- Set $(\hat{q}, \hat{p}) = (q_{T / \eta}\,,\, p_{T / \eta})$
>	- **Metropolis-Hastings correction**:
>		- Draw $$u \sim \text{Uniform}[0,1]$$
>		- Compute $$\rho = \exp \left(H(\hat{q}, \hat{p}) - H(X_{k-1}, \xi)\right)$$
>		- If $u < \min\{ 1, \rho \}$:
>			- *accept* new sample $$X_{k} = \hat{q}$$ 
>- Output $(X_{1} \,{,}\ldots{,}\,X_{N})$

- [[Metropolis-Hastings Algorithm]]
- Chen, T., Fox, E., & Guestrin, C. (2014, June). Stochastic gradient hamiltonian monte carlo. In _International conference on machine learning_ (pp. 1683-1691). PMLR.

### Discretizing HMC (Second-Order Approximation)

>[!important] Definition (HMC Second-Order)
>The *unadjusted* **Hamiltonian Monte Carlo (HMC)** *method* works as follows
>- Initialized with starting point $X_{0} \in \mathbb{R}^d$, 
>- Set $T >0$, $N \in \mathbb{N}$, $\eta >0$
>- Input *first-order oracle* for $f:\mathbb{R}^n \to \mathbb{R}$
>- For $k = 1 \,{,}\ldots{,}\, N$ 
>	- **Sample a momentum** $$\xi \sim \mathcal{N}(0, \Lambda)$$
>	- Set $$q_{0} = X_{k-1}, \quad p_{0} = \xi$$
>	- For $j = 1 \,{,}\ldots{,}\,  T/\eta$:
>		- **Update position** $$q_{j} = q_{j-1} + \eta\,\Lambda^{-1}\,p_{j-1} - \frac{1}{2}\eta^2\,\Lambda^{-1}\,\nabla f(q_{j-1})$$
>		- **Update momentum** with **difference of gradient** between *old position* and *new position* $$p_{j} = p_{j-1} - \frac{1}{2}\,\eta\,\left(\nabla f(q_{j-1}) - \nabla f(q_{j})\right)$$
>	- Choose new sample as the end position $$X_{k} = q_{T / \eta}\left(X_{k-1}, \xi\right)$$
>- Output $X_{N}$

^d957f6

- Mangoubi, O., & Vishnoi, N. (2018). Dimensionally tight bounds for second-order Hamiltonian Monte Carlo. _Advances in neural information processing systems_, _31_.

>[!info] 
>Here we approximate the Hamiltonian dynamic with a **second-order Euler integrator**, which iteratively computes the *second-order Taylor expansions* $(\hat{x}_{\eta}, \hat{p}_{\eta})$ of Hamilton's equation.
>$$
>\begin{align*}
> \hat{x}_{\eta}(x, p) &= x + \eta\frac{d}{dt}\hat{x}_{t}(x, p) + \frac{1}{2}\eta^2\, \frac{d^2}{dt^2}\hat{x}_{t}(x, p)   \\
> &= x + \eta \, \Lambda^{-1}\, p - \frac{1}{2}\eta^2\,\Lambda^{-1}\,\nabla f(x) \\
> \hat{p}_{\eta}(x, p) &= p + \eta\frac{d}{dt}\hat{p}_{t}(x, p) + \frac{1}{2}\eta^2\, \frac{d^2}{dt^2}\hat{p}_{t}(x, p)   \\
> &= p - \eta \nabla f(x) - \frac{1}{2} \eta^2\,\nabla^2 f(x)\,\Lambda^{-1}\,p 
>\end{align*}
>$$
>Note
>$$
>\frac{d}{dt}  \left( \nabla f(x) \right) = \nabla^2 f(x)^{T} \frac{d}{dt} x = \nabla^2 f(x)\, \Lambda^{-1} p
>$$
>here we apply the approximate
>$$
>\nabla^2 f(x)\,\Lambda^{-1} p \approx \frac{\nabla f(\hat{x}_{\eta}) - \nabla f(x)}{\eta} 
>$$
>thus
>$$
>\begin{align*}
> \hat{x}_{\eta}(x, p) &= x + p\,\eta - \frac{1}{2}\eta^2\,\nabla f(x) \\
> \hat{p}_{\eta}(x, p) &= p - \frac{1}{2}\eta \left(\nabla f(x) - \nabla f(\hat{x}_{\eta}) \right)
>\end{align*}
>$$

>[!quote]
>It can be shown that under a mild “regularity” condition, this unadjusted HMC requires at most (roughly) $O ( d^{1/4} \epsilon^{- 1 /2})$ gradient evaluations;
>
>-- [[vishnoiIntroductionHamiltonianMonte2021]] pp 10



## Explanation

>[!important]
>Challenge for Monte Carlo sampling on high dimensional space.
>
>
>-- Betancourt, M. (2018). _A Conceptual Introduction to Hamiltonian Monte Carlo_ (Methodology (Stat.ME) arXiv:1701.02434). arXiv. pp 7

>[!important]
>Challenge for MCMC with high curvature
>
>
>-- Betancourt, M. (2018). _A Conceptual Introduction to Hamiltonian Monte Carlo_ (Methodology (Stat.ME) arXiv:1701.02434). arXiv. pp 7

>[!quote]
>**Hamiltonian Monte Carlo** is the unique procedure for automatically generating this *coherent exploration* for sufficiently *well-behaved* target distributions.
>
>-- Betancourt, M. (2018). _A Conceptual Introduction to Hamiltonian Monte Carlo_ (Methodology (Stat.ME) arXiv:1701.02434). arXiv. pp 17


>[!quote]
>In other words, instead of fumbling around parameter space with *random, uninformed jumps*, we can **follow the direction** *assigned to each at point for a small distance*. By construction this will move us to *a new point* in the **typical set**, where we will *find a new direction to follow*. Continuing this process traces out a **coherent trajectory through the typical set** that efficiently moves us far away from the initial point to **new, unexplored regions** of the typical set **as quickly as possible**.
>
>-- Betancourt, M. (2018). _A Conceptual Introduction to Hamiltonian Monte Carlo_ (Methodology (Stat.ME) arXiv:1701.02434). arXiv. pp 17

>[!quote]
>**Avoidance of random-walk behavior**, as illustrated above, is one **major benefit of HMC**.... The number of iterations needed to reach a state almost *independent of the current state* is mostly determined by how long it takes to *explore* the less constrained direction....
>
>The stepsize used for the leapfrog steps is similarly limited by the most constrained direction, but the movement will be in the same direction for many steps. The distance moved after $n$ steps will therefore tend to be proportional to $n$, until the distance moved becomes comparable to the overall width of the distribution. The **advantage** compared to movement by a random walk will be a **factor** roughly equal to the **ratio of the standard deviations** in the **least confined direction** and **most confined direction**.
>
>-- Brooks, S., Gelman, A., Jones, G., & Meng, X.-L. (Eds.). (2011). _Handbook of Markov Chain Monte Carlo_ (1st edition). Chapman and Hall/CRC. pp 130

- [[Random Walk Metropolis-Hastings]]

## Stationarity of HMC

![[Hamiltonian Systems of Differential Equations#^46b385]]


>[!info] 
>Compared to MCMC, *Hamiltonian Monte Carlo* take *longer steps* while still **conserving the target distribution**.
>
>This is due to the properties of Hamiltonian dynamics.

>[!important] Theorem (Stationarity of HMC)
>Let $f: \mathbb{R}^{n} \to \mathbb{R}$ be a *differentiable function*. Let $T >0$ be the **step size** of the **HMC.**
>
>Suppose that $(X, P)$ is a sample from the density
> $$\pi(x, p) := \exp \left( - H(x, p) - \log Z \right)$$ where $$H(x, p) = f(x) +  \frac{1}{2} \left\langle  \Lambda^{-1}\,p,  p\right\rangle$$ and $\log Z$ is the *log-partition function*.
> 
> Then
> -  the **density** of $\theta_{T}(X, P)$ **is $\pi$** for any $T \ge 0$.
> 
> - Moreover, the density of  $\theta_{T}(X, \xi)$, where $\xi \sim \mathcal{N}(0, \Lambda)$ is **also** $\pi$.
>   
>Thus the **idealized HMC algorithm preserve $\pi$,**

- Vishnoi, N. K. (2021). _An Introduction to Hamiltonian Monte Carlo Method for Sampling_ (arXiv:2108.12107). arXiv. [[vishnoiIntroductionHamiltonianMonte2021]] pp 5

## Markov Chain Monte Carlo

>[!important]
>The **Hamiltonian Monte Carlo** method is a special case of **Markov Chain Monte Carlo (MCMC)**.
>
>In particular, since the **Hamiltonian flow** $\theta_{T}: \mathbb{R}^{2n} \to \mathbb{R}^{2n}$ for fixed $t$ is both 
>- *measure preserving* due to above theorem and 
>- *bijective* due to *time-reversibility*,
>  
>the corresponding Markov chain has *transition kernel* as
>$$
> K((q,p), A) = \int_{\Gamma}\,\mathbb{1}\left\{  \theta_{T}(q,p) \in A\right\} d\nu\left( \theta_{T} \right).
>$$
>where $\theta_{T} = \theta_{T}(X_{0}, \xi)$ is assumed to be random given the initial momentum $\xi$ is random.
>
>This kernel has invariant measure $\pi(x,p)$ as described in the theorem above.

- [[Markov Chain Monte Carlo Methods]]
- [[Markov Kernel with Invariant Measure via Measure Preserving Map]]



## Convergence for Strongly Convex and Smooth Potentials

>[!important] Proposition
>Let $f: \mathbb{R}^{n} \to \mathbb{R}$ be a **twice-differentiable function** which satisfies
>$$
> m\,I_{n} \preceq \nabla^2 f(x) \preceq M\,I_{n}.
>$$
>i.e. $f$ is **strongly convex**. Let $\nu_{k}$ be the distribution of $X_{k}$ at step $k \in \mathbb{Z}_{+}$ from the idealized **HMC**.
>
>Suppose that both $\nu_{0}$ and joint probability measure $\pi$ have **mean** and **variance bounded by** $O(1)$. 
>
>Then given any $\epsilon >0$, for $$T = \Omega \left(\frac{\sqrt{ m }}{M}\right) \;\;\text{ and }\;\; k = O\left(\left(\frac{M}{m}\right)^2\log\left( \frac{1}{\epsilon} \right)\right),$$ we have that 
>$$
>\mathcal{W}_{2}\left(\nu_{k}, \pi\right) \le \epsilon.
>$$
>where $\mathcal{W}_{2}$ is the *$2$-Wasserstein distance*.


- [[Strongly Convex Function]]
- [[Wasserstein Distance]]
- Vishnoi, N. K. (2021). _An Introduction to Hamiltonian Monte Carlo Method for Sampling_ (arXiv:2108.12107). arXiv. [[vishnoiIntroductionHamiltonianMonte2021]] pp 5


## Langevin Dynamics

>[!info]
>We see that in **unadjusted HMC** with second-order approximation
>$$
>q_{j} = q_{j-1} - \frac{1}{2}\eta^2\,\nabla f(q_{j-1}) + \eta\,p_{j-1} 
>$$
>where $p_{0} \sim \mathcal{N}(0, I)$
>
>This compares to the **Langevin dynamic**
>$$
>q_{j} = q_{j-1} - \frac{1}{2}\eta^2\,\nabla f(q_{j-1}) + \eta\,\xi_{j-1}
>$$
>where $\xi_{j} \sim \mathcal{N}(0, I)$. Here
>- $- \frac{1}{2}\eta^2\,\nabla f(q_{j-1})$ acts as the **friction force**
>- $\eta\,p_{j-1}$ is the **momentum force**; 
>	- for **Langevin dynamic**, the momentum force is **Gaussian white noise**, i.e. it is *completely random*. 
>	- While for the **HMC**, the momentum force follows the **Hamiltonian equation**, i.e. it is *deterministic*.

- [[Langevin Dynamics and Langevin Sampling]]


>[!info]
>These conservation properties allow HMC to **choose the momentum** at the *beginning of each step* and **simulate the trajectory** of the particle for a long time. HMC is a large class of algorithms, and includes the **Langevin algorithms** and RWM as special cases.



## Challenges in HMC

>[!quote]
>One practical **impediment** to the use of Hamiltonian Monte Carlo is the need to select suitable values for the leapfrog stepsize, $\epsilon$, and the number of leapfrog steps, $L$, which together determine the length of the trajectory in fictitious time, $\epsilon L$. Most MCMC methods have parameters that need to be tuned, with the notable exception of Gibbs sampling when the conditional distributions are amenable to direct sampling. However, **tuning HMC is more difficult** in some respects than tuning a simple Metropolis method.
>
>-- Brooks, S., Gelman, A., Jones, G., & Meng, X.-L. (Eds.). (2011). _Handbook of Markov Chain Monte Carlo_ (1st edition). Chapman and Hall/CRC. pp 134



## Geometric Intepretation







-----------
##  Recommended Notes and References


- [[Markov Chain and Markov Process]]
- [[Detailed Balance Equation]]
- [[Time-Reversible Markov Chain]]


- [[Hamiltonian Function in Mechanic]]
- [[Hamiltonian Systems of Differential Equations]]
- [[Phase Space of Hamiltonian Systems of Differential Equations]]
- [[Markov Kernel with Invariant Measure via Measure Preserving Map]]

- [[Exponential Family of Distributions]]

- [[Markov Chain Monte Carlo Methods]]
- [[Monte Carlo Strategies in Scientific Computing by Liu]] pp 183 - 204
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 510 - 518
- Neal. 2011. “[MCMC Using Hamiltonian Dynamics](http://arxiv.org/abs/1206.1901).” In _Handbook for Markov Chain Monte Carlo_.
- Betancourt, M. (2018). _A Conceptual Introduction to Hamiltonian Monte Carlo_ (Methodology (Stat.ME) arXiv:1701.02434). arXiv. [https://doi.org/10.48550/arXiv.1701.02434](https://doi.org/10.48550/arXiv.1701.02434)
- Betancourt, M., Byrne, S., Livingstone, S., & Girolami, M. (2017). The geometric foundations of Hamiltonian Monte Carlo. _Bernoulli_, _23_(4A), 2257–2298. [https://doi.org/10.3150/16-BEJ810](https://doi.org/10.3150/16-BEJ810)
- Vishnoi, N. K. (2021). _An Introduction to Hamiltonian Monte Carlo Method for Sampling_ (arXiv:2108.12107). arXiv. [https://doi.org/10.48550/arXiv.2108.12107](https://doi.org/10.48550/arXiv.2108.12107) [[vishnoiIntroductionHamiltonianMonte2021]]



- Wikipedia [Metropolis-Hastings_algorithm](https://en.wikipedia.org/wiki/Metropolis%E2%80%93Hastings_algorithm)