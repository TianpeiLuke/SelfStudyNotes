---
tags:
  - concept
  - statistics/monte_carlo_simulation
keywords:
  - metropolis_hastings_algorithm
  - markov_chain_monte_carlo
topics:
  - statistics/monte_carlo
name: Metropolis-Hastings Algorithm
date of note: 2024-07-04
---

## Concept Definition

>[!important]
>**Name**: Metropolis-Hastings Algorithm

![[Gibbs Measure and Energy-based Model#^bfb840]]

### Metropolis Algorithm

![[Markov Transition Kernel and Transition Function#^8dc85c]]


>[!important]
>A **proposal function** or **proposal distribution** $K: \mathcal{X}\times \mathcal{X} \to \mathbb{R}_{+}$ is defined by a *conditional probability density function*. That is, 
>- For every $x\in \mathcal{X}$, $K(x, \cdot)$ is a *probability density function*.
>- For every $y\in \mathcal{X}$, $K(\cdot, y)$ is a *measurable function*.
>  
>In other word, $$K(x, y) = p(y | x).$$  

^f61703

- [[Conditional Probability]]


>[!important] Definition
>Consider the task of sampling from a Gibbs distribution
>$$
>\pi(x) = \frac{1}{Z}\exp \left( - E(x) \right)
>$$
>where the partition function $$Z = \int\exp \left( - E(x) \right) dx.$$
>
>The **Metropolis Algorithm** is described as below:
>- *Initialize* configuration $X_{0}$
>- For $t=1 \,{,}\ldots{,}\,$
>	- **Generate** $Y$ given $X_{t}$, according to a **symmetric proposal function** $p(\cdot|\cdot)$, where $$p(x|y) = p(y|x).$$ That is, $$Y \sim  p(y \,|\, X_{t})$$
>	- Compute the **difference** in **energy**  $$\Delta E := E(Y) - E(X_{t})$$
>	- Generate a **uniform** random variable $U\in \mathcal{U}[0,1]$.
>		- **Accept** $X_{t+1} =Y$ if $$U \le \frac{\pi(Y)}{\pi(X_{t})} := \exp \left( - \Delta E \right);$$
>		- **Otherwise** accept $X_{t+1} = X_{t}$

^1aef3a

- [[Gibbs Measure and Energy-based Model]]
- [[Markov Transition Kernel and Transition Function]]
- [[Detailed Balance Equation]]
- [[Accept-Reject Sampling]]

### Metropolis-Hastings Algorithm

>[!important] Definition
>The **Metropolis-Hastings (MH) Algorithm** is described as below:
>- *Initialize* configuration $X_{0}$
>- For $t=1 \,{,}\ldots{,}\,$
>	- **Generate** a random sample $Y$ given $X_{t}$ according to **proposal function** $p(\cdot|X_{t})$, i.e. $$Y \sim p(y\,|\,X_{t})$$
>	- Compute the **Hastings ratio**  $$r(X_{t}, Y) := \frac{\pi(Y)\;p(X_{t} \,|\, Y)}{\pi(X_{t})\;p(Y \,|\, X_{t})}$$
>	- **Metropolis Rejection**: Generate a **uniform** random variable $U\in \mathcal{U}[0,1]$.
>		- **Accept** $X_{t+1} = Y$ if $$U \le \min\{1, \; r(X_{t}, Y)\};$$
>		- **Otherwise** accept $X_{t+1} = X_{t}$

^f582b7

## Explanation

>[!info]
>If the proposal function is **symmetric**, i.e. $$K(x, y) = K(y, x),$$ then the *Metropolis-Hastings Algorithm* is equivalent to the *Metropolis Algorithm.*
>
>$$
>r(X_{t}, Y) = \frac{\pi(Y)K(Y, X_{t})}{\pi(X_{t})K(X_{t}, Y)} =  \frac{\pi(Y)K(X_{t}, Y)}{\pi(X_{t})K(X_{t}, Y)}   =  \frac{\pi(Y)}{\pi(X_{t})} 
>$$

>[!info]
>In [[Hamiltonian Monte Carlo]], the proposal function $K(x, y)$ is defined by a **system of differential equations**.


## Markov Chain from Metropolis-Hastings Algorithm

>[!important] Proposition
>Let $(X_t)_t$ be the chain produced by the **Metropolis-Hastings** algorithm.
>- Denote $p(y|x)$ as the *proposal function.*
>- Denote $\alpha(x, y)$ as the acceptance threshold induced by the *Hastings ratio*. $$\alpha(x, y) = \min\left\{1,\,  \frac{\pi(Y)\;p(X_{t} \,|\, Y)}{\pi(X_{t})\;p(Y \,|\, X_{t})}  \right\} $$
>- Let $\mathcal{X}$ be the domain of Markov chain. 
>
>Then
>- the **Markov transition kernel** of the chain is $$A(x, y) := p(y\,|\,x)\,\alpha(x, y).$$
>- If $\mathcal{X}$ is *connected*, the chain  $(X_{t})$ is **irreducible**. 
>- If the **proposal function** $p(y|x)$ is positive, i.e. $$p(y|x) >0,\, \forall x, y\in \mathcal{X},$$ then the chain $(X_{t})$ is **positive recurrent**.
>- If $(X_{t})_{t}$ is **$\pi$-irreducible**, then $(X_{t})_{t}$ is **Harris recurrent.**

- [[Irreducibility of Markov Chain]]
- [[Positive Recurrent Markov Chain]]


### Detailed Balance Equation

>[!important] Theorem
>Let $(X_t)_t$ be the chain produced by the **Metropolis-Hastings** algorithm. 
>
>For every *conditional distribution* $p(y|x)$, whose support includes $\mathcal{X}$,
> 
>- the **kernel** of the chain satisfies the **detailed balance condition** with $\pi$. Specifically, the *kernel* of the chain $(X_{t})_{t}$ is $$A(x, y) := p(y\,|\,x)\,\alpha(x, y)$$
>  And the following **detailed balance equation holds**  for any $x, y\in \mathcal{X}$
>  $$
>  \begin{align*}
>  \pi(x)\,A(x, y) &= \pi(x)\,p(y\,|\,x)\,\alpha(x, y)\\ 
>  &= \pi(x)\,p(y\,|\,x)\,\min\left\{ 1, \frac{\pi(y)\;p(x \,|\, y)}{\pi(x)\;p(y \,|\, x)} \right\} \\[5pt] 
>  &= \min\left\{  \pi(y)\;p(x \,|\, y), \, \pi(x)\,p(y\,|\,x)   \right\}\\[5pt]
>  &= \pi(y)\,A(y, x)
>  \end{align*}
>  $$
>- $\pi$ is a **invariant measure** of the chain.
>

- [[Invariant Measure and Stationary Distribution]]
- [[Detailed Balance Equation]]

## Reversible Chain

>[!important] Proposition
>The Markov chain $(X_{t})$ from the **Metropolis-Hastings** algorithm is **time-reversible** with invariant measure $\pi$

- [[Time-Reversible Markov Chain]]


## Special MH Algorithms

- [[Random Walk Metropolis-Hastings]]


## Gibbs Sampling

- [[Gibbs Sampling]]



-----------
##  Recommended Notes and References


- [[Markov Chain Monte Carlo Methods]]
- [[Markov Chain and Markov Process]]





- [[All of Statistics A Concise Course by Wasserman]] pp 411
- [[Monte Carlo Statistical Methods by Robert]]
- [[Monte Carlo Strategies in Scientific Computing by Liu]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 477 - 537
- [[Deep Learning by Goodfellow]]
- [[Deep Learning Foundations and Concepts by Bishop]] pp 429

- [[Probabilistic Graphical Models by Koller]] pp 516

- Wikipedia [Metropolis-Hastings_algorithm](https://en.wikipedia.org/wiki/Metropolis%E2%80%93Hastings_algorithm)