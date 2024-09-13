---
tags:
  - concept
  - statistics/monte_carlo_simulation
keywords:
  - sequential_importance_sampling
  - importance_sampling
topics:
  - statistics/monte_carlo
name: Sequential Importance Sampling
date of note: 2024-07-04
---

## Concept Definition

>[!important]
>**Name**: Sequential Importance Sampling

>[!important] Settings
>Consider a list of samples $(X_{1} \,{,}\ldots{,}\,X_{n})$ generated *sequentially* from some joint distribution $p$. 
>
>The **trial density** $g$ of $(X_{1} \,{,}\ldots{,}\,X_{n})$ can be *factorized sequentially* as
>$$
>g(x_{1} \,{,}\ldots{,}\,x_{n}) = g(x_{1})\,\prod_{k=1}^{n-1}g(x_{k+1} | x_{1} \,{,}\ldots{,}\,x_{k})
>$$
>by which we hope to obtain some information on *target density* $p$ while building up the trial density. The target density $p$ can also be factorized as
>$$
>p(x_{1} \,{,}\ldots{,}\,x_{n}) = p(x_{1})\,\prod_{k=1}^{n-1}p(x_{k+1} | x_{1} \,{,}\ldots{,}\,x_{k}).
>$$

- [[Probability Density Function of Random Variable]]
- [[State-Observation Models]]

>[!info]
>It is **nontrivial** to find a good trial distribution $g$ in high dimensional space. One of the most useful strategies in these problems is to *build up* the *trial density* **sequentially**.


>[!important] Definition
>The task is to *generate* a list of samples $(X_{1} \,{,}\ldots{,}\,X_{n})$ *sequentially* from some *target joint distribution* $p$. 
>
>The **Sequential Importance Sampling (SIS)** algorithm is described as below:
>- For $t=1 \,{,}\ldots{,}\,T$
>	- Generate sample from *conditional trial density* $$X_{t} \sim g(x_{t}| X_{1} \,{,}\ldots{,}\,X_{t-1})$$
>	- Compute the **incremental weight** $$u_{t} = \frac{p_t(X_{t})}{p_{t-1}(X_{1} \,{,}\ldots{,}\,X_{t-1}) \, g(x_t\,|\,X_{1} \,{,}\ldots{,}\,X_{t-1})}$$ where $p_{t}$ is a reasonable **approximation** of the **marginal** $p(x_{1} \,{,}\ldots{,}\,x_{t}).$ 
>		- Note that $p_t(x_{1} \,{,}\ldots{,}\,x_{t})$ only need to be known *up to a constant* and only serves as a *"guide"* to construction of whole samples. 
>	- Update **importance weight** $$w_{t} = w_{t-1}\,u_{t}$$
>
>- Output $$(w_{1}X_{1} \,{,}\ldots{,}\, w_{n}X_{n}) \sim p$$


## Explanation

>[!important]
>The **benefits** for using *sequential importance sampling* include:
> 
>- We can make use of the **characteristics** of **local factor** $p(x_{t}| x_{t-1} \,{,}\ldots{,}\, x_{1})$ in *target density* when designing trial density $g(x_{t}| x_{t-1} \,{,}\ldots{,}\, x_{1})$. An example is the **local Markov property** $$p(x_{t}| x_{t-1} \,{,}\ldots{,}\, x_{1}) = p(x_{t}|x_{t-1})$$ for probabilistic graphical models. By sequential sampling, we break the complex problem into smaller pieces.
> 
>- We can *stop* generating further components of $x$ if the **partial weights** $w_{k}$ that **derived** from the sequentially generated the *partial samples* $(x_{1} \,{,}\ldots{,}\, x_{k})$ are **too small**. We can also **reject sample** with *small weight* and *restart again*. This way we avoid wasting effort generating samples with little  effect on final estimation. This rejection process would introduce additional bias which should be corrected. [[Monte Carlo Statistical Methods by Robert]]
> 
>- The SIS algorithm is *attractive* since we can use a sequence of auxiliary distributions to construct more **efficient sampling algorithm**.
>





-----------
##  Recommended Notes and References

- [[Importance Sampling]]

- [[Particle Filter or Sampling-Importance-Resampling]]

- [[All of Statistics A Concise Course by Wasserman]]
- [[Monte Carlo Strategies in Scientific Computing by Liu]] pp 46
- [[Monte Carlo Statistical Methods by Robert]] pp 547

- [[Reinforcement Learning An Introduction by Sutton]]

- [[Probabilistic Graphical Models by Koller]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 541 - 542
- [[Deep Learning by Goodfellow]] pp 590
- [[Deep Learning Foundations and Concepts by Bishop]] pp 429