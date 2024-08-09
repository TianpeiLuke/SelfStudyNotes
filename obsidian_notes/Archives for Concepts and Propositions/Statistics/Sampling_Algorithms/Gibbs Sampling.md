---
tags:
  - concept
  - statistics/monte_carlo_simulation
keywords:
  - gibbs_sampling
topics:
  - statistics/monte_carlo
name: Gibbs Sampling
date of note: 2024-07-04
---

## Concept Definition

>[!important]
>**Name**: Gibbs Sampling

>[!important] Definition
>Consider the task of sampling $X\in \mathbb{R}^{d}$ from joint probability density
>$$
> X = (X_{1} \,{,}\ldots{,}\,X_{d}) \sim p(x_{1}\,{,}\ldots{,}\,x_{d}).
>$$
>
>The **Systematic Scan Gibbs Sampling** is described as follows
>- *Require*: a set of *conditional probabilities* $\left\{ p(x_{i}\,|\,x_{j\neq i}),\, i=1\,{,}\ldots{,}\,d \right\}$
>- *Initialize* configurations $(X_{1}^{(0)} \,{,}\ldots{,}\,X_{d}^{(0)}).$
>- For $t= 1\,{,}\ldots{,}\,T$:
>	- For $i=1 \,{,}\ldots{,}\,d$:
>		- *Sample* and *Replace* the **coordinate variable** $X_{i}^{(t)}$ given all *sampled components* from previous iterations according to the **conditional probability**. $$X_{i}^{(t)} \sim p\left( x_{i}\,\Big|\, X_{1}^{(t)} \,{,}\ldots{,}\,X_{i-1}^{(t)},\, X_{i+1}^{(t-1)}  \,{,}\ldots{,}\, X_{d}^{(t-1)}\right)$$ 


>[!important]
>The **Random Scan Gibbs Sampling** is described as follows
>- *Require*: a set of *conditional probabilities* $\left\{ p(x_{i}\,|\,x_{j\neq i}),\, i=1\,{,}\ldots{,}\,d \right\}$
>- *Initialize* configurations $(X_{1}^{(0)} \,{,}\ldots{,}\,X_{d}^{(0)}).$
>- For $t= 1\,{,}\ldots{,}\,T$:
>	- *Randomly select* a coordinate index $i\in [d]$ with probability $$\Delta_{d} = \left( \alpha_{1} \,{,}\ldots{,}\, \alpha_{d}\right).$$
>	- *Sample* the corresponding **coordinate variable** $X_{i}^{(t)}$ given all *sampled components* from previous iterations according to the **conditional probability**. $$X_{i}^{(t)} \sim p\left( x_{i}\,\Big|\, X_{j\neq i}^{(t-1)}\right)$$ 

^655bf6


## Explanation


>[!important]
>The **most prominent feature** of Gibbs sampling is that the underlying Markov chain is constructed by composing a **sequence of conditional distributions (local factors)** along a set of **directions** (often along the coordinate axis). 


## Gibbs Sampling for Graphical Model

>[!important]
>Gibbs sampling naturally fit the structure of **probabilistic graphical model** since 
>- it only requires **local probabilistic models** or **factors** to generate each coordinate sample.
>- Also, the *order relation* in graph structure (esp. in Bayesian network) provides a direction for **scanning** in Gibbs sampling.

- [[Local Probabilistic Models]]
- [[Gibbs Sampling for Graphical Model]]





## Block Coordinate Descent

- [[Block Coordinate Descent Algorithm]]




-----------
##  Recommended Notes and References



- [[Metropolis-Hastings Algorithm]]
- [[Markov Chain and Markov Process]]
- [[Block Coordinate Descent Algorithm]]

- [[Markov Chain Monte Carlo Methods]]

- [[Gibbs Distribution]]


- [[All of Statistics A Concise Course by Wasserman]] pp 411 - 415
- [[Monte Carlo Statistical Methods by Robert]]
- [[Monte Carlo Strategies in Scientific Computing by Liu]] pp 129 - 151

- [[Probabilistic Graphical Models by Koller]] pp 506, 512
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 477 - 537
- [[Deep Learning by Goodfellow]] pp 590
- [[Deep Learning Foundations and Concepts by Bishop]] pp 429