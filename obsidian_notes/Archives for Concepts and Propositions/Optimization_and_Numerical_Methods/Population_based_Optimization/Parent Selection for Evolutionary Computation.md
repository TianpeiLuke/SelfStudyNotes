---
tags:
  - concept
  - evolutionary_computation
keywords:
  - fitness_proportional_selection
  - evolutionary_algorithm
topics:
  - evolutionary_algorithm
  - evolutionary_computation
name: Parent Selection for Evolutionary Computation
date of note: 2024-08-27
---

## Concept Definition

>[!important]
>**Name**: Parent Selection for Evolutionary Computation

![[Evolutionary Computation Algorithms#^ac42fa]]

![[Evolutionary Computation Algorithms#^12072d]]

![[Evolutionary Computation Algorithms#^8340f3]]

- [[Evolutionary Computation Algorithms]]

### Truncation Selection

>[!important] Definition
>Consider the maximization problem $$\max_{x} f(x)$$
>
>In the **truncation selection** mechanism,  a parent $i$ is selected from the top $\lambda$ *fittest members* in the population $\mathcal{S}$ i.e. $$\mathcal{S}^{(s)} := \left\{ x^{(1)} \,{,}\ldots{,}\, x^{(\lambda)}\right\} $$ where 
>$$
>f(x^{(1)}) \,{\ge}\ldots{\ge}\, f(x^{(\lambda)}) \,{\le}\ldots{\ge}\, f(x^{(\mu)})
>$$

- [[Greedy Heuristic Algorithms]]
### Fitness Proportional Selection

>[!important] Definition
>Consider the maximization problem $$\max_{x} f(x)$$
>
>In the **fitness proportional selection (FPS)** mechanism,  an individual $i$ in parent population $\mathcal{S}$ is selected based on the *absolute value of its fitness*, i.e. $$P(i) = \frac{f(x_{i})}{\sum_{j=1}^{\mu}f(x_{j})}$$ 

- [[Genetic Algorithms]]
- [[Genetic Programming]]

>[!info]
>there are some problems with this selection mechanism: 
>- **Outstanding individuals take over the entire population very quickly**. This tends to *focus* the search process, and makes it less likely that the algorithm will thoroughly *search* the space of possible solutions, where better solutions may exist. This phenomenon is often observed in *early generations*, when many of the randomly created individuals will have *low fitness*, and is known as **premature convergence**.
>- When **fitness values are all very close** together, there is almost **no selection pressure**, so selection is *almost uniformly random*, and having a slightly better fitness is not very ‘useful’ to an individual. Therefore, later in a run, when some convergence has taken place and the worst individuals are gone, it is typically observed that the *mean population fitness* only increases very *slowly*.
>- The mechanism behaves differently if the fitness function is **transposed** (*translation operation* on fitness function would shift the distribution).

- [[Exploration and Exploitation Tradeoff]]

>[!important] Definition
>To avoid the second two problems with FPS, a procedure known as **windowing** is often used. 
>$$P(i) = \frac{f(x_{i}) - \beta_{t} }{\sum_{j=1}^{\mu} (f(x_{j}) - \beta_{t})}$$ 
>- The simplest approach is just to subtract the value of the *least-fit member* of the current population $\mathcal{S}_{t}$ by setting $$\beta_{t} = \min_{y\in \mathcal{S}_{t}} f(y).$$
>- This value may fluctuate quite rapidly, so one alternative is to use a **running average over the last few generations**.

>[!important] Definition
>Another well-known approach is **sigma scaling** where the fitness function is replaced by 
>$$
>f'(x) := \max\left\{ 0,  f(x) - \left( \mu_{f} - c\,\sigma_{f} \right) \right\} 
>$$
>where $\mu_{f}$ and $\sigma_{f}$ are *mean and standard deviation* of fitness values in population $\mathcal{S}_{t}$ and $c$ is a constant.

### Ranking Selection

>[!important] Definition
>Consider the maximization problem $$\max_{x} f(x)$$
>Assume that we *rank* the individuals in population with size $\mu$ based on $f(x)$ in *ascending order*, where the *best candidate* ranked $\mu-1$ and the *worst* ranked $0$.
>
>In **ranking selection**, the probability of an individual is selected in parent population is based on its *rank in the population*. 
>
>The mapping from rank to probability can be done in many ways:
>- **Linear ranking scheme** parameterized by number $\xi\in (1, 2]$ choose the individual $i$ with probability $$P(i) = \frac{2-\xi}{\mu} + 2i\frac{\left( \xi -1 \right)}{(\mu - 1)}$$ This is via **linear interpolation**: 
>	- for $i=0$, i.e. the worst individual, the second term of selection probability $0$
>	- for $i= \mu-1$, i.e. the best candidate, the selection probability is highest.
>- **Exponential ranking scheme** choose the individual $i$ with probability $$P(i) = \frac{1}{c}\left( 1 - e^{-i} \right)$$ where $c$ is the normalization factor.

### Roulettle Wheel Algorithm

>[!info]
>In an ideal world, the mating pool of parents taking part in recombination would have exactly the *same proportions* as this *selection probability distribution*. This would mean that the number of any given individual would be given by its selection probability, multiplied by the size of the mating pool. However, in practice this is not possible because of the finite size of the population. 

![[Roulettle Wheel Algorithm to Resample from CDF#^a9dfe5]]

- [[Roulettle Wheel Algorithm to Resample from CDF]]

### Uniform Parent Selection

>[!important] Definition
>The probability of an individual $i \in [\mu]$ is selected to enter the mating pool is 
>$$P(i) = \frac{1}{\mu}.$$

- [[Differential Evolution Algorithm]]

### Tournament Selection

>[!important]
>In certain situations, for example, if the *population size* is very large, or if the *population is distributed* in some way (perhaps on a parallel system), obtaining the knowledge of fitness $$f(x),\; \forall x\in \mathcal{S}$$ is either highly time consuming or at worst impossible. Furthermore, both methods assume that fitness is a *quantifiable measure* (based on some explicit objective function to be optimised), which *may not* be valid.
>
>In these situations, we may not be able to quantify the value of fitness, but we can **compare any two of them.**

>[!important] Definition
>**Tournament selection** is an operator with the useful property that 
>- it does *not require any global knowledge* of the population, 
>- *nor a quantifiable measure* of quality. 
>  
>Instead it only relies on an **ordering relation** that can compare and rank any two individuals.

- [[Strict Partial Order Relation]]

>[!important] Definition
>Consider the maximization problem $$\max_{x} f(x)$$
>
>The **tournament selection** is described as below:
>- *Require*: the parent population with size $\mu$ $$\mathcal{S} := \left\{ x_{1} \,{,}\ldots{,}\, x_{\mu}\right\} $$
>- *Require*: the size of *resampled population* (i.e. **mating pool size**) $\lambda$ 
>- $\mathcal{M} = \emptyset$
>- For $k=1 \,{,}\ldots{,}\,\lambda$:
>	- Select a batch of $m$ individuals in $\mathcal{S}$ *randomly* **with or without replacement** $$\mathcal{S}^{(m)} := \left\{ x^{(1)} \,{,}\ldots{,}\,x^{(m)} \right\} $$
>	- **Compare** these $m$ individuals and **select** the **best** of them $$x^{(i)} = \arg\max_{j=1\,{,}\ldots{,}\,m}f(x^{(j)})$$
>	- Add the best individual  to the mating pool $$\mathcal{M} \leftarrow \mathcal{M} \cup \left\{ x^{(i)} \right\}$$
>- *Return*: $\mathcal{M}$

>[!info]
>Because *tournament selection* looks at **relative** rather than absolute fitness, it has the same properties as **ranking schemes** in terms of invariance to *translation and transposition* of the fitness function.

>[!info]
>The probability that an individual will be selected as the result of a tournament depends on four factors, namely:
>- Its **rank in the population**. Effectively this is estimated *without the need for sorting* the whole population. 
>- The **tournament size** $m$. The larger the tournament, the greater the chance that it will contain members of above-average fitness, and the less that it will consist entirely of low-fitness members. Thus the probability of selecting a high-fitness member increases, and that of selecting a low-fitness member decreases, as $m$ is increased. Hence we say that **increasing $m$ increases the selection pressure**.
>- The **probability** $p$ that the *most fit member* of the tournament is selected. Usually this is $1$ (**deterministic tournaments**), but **stochastic versions** are also used with $p<1$. Since this makes it more likely that a less-fit member will be selected, decreasing $p$ will decrease the selection pressure.
>- Whether individuals are chosen **with or without replacement**. In the second case, with *deterministic tournaments*, the $m-1$ least-fit members of the population can never be selected, since the other member of the tournament will be fitter. However, if the tournament candidates are picked *with replacement*, it is always possible for even the least-fit member of the population to be selected, since with probability $1/\mu_{k} > 0$ all tournament candidates will be copies of that member.

>[!info]
>since *$\lambda$ tournaments are required to produce $\lambda$ selections*, it suffers from the same problems as the *roulette wheel algorithm*, in that the outcomes can show a high variance from the theoretical probability distribution.


>[!quote]
>Despite this drawback, tournament selection is perhaps the **most widely used selection operator** in some EC dialects (in particular, Genetic Algorithms), due to its extreme simplicity and the fact that the selection pressure is easy to control by varying the tournament size k.
>
>-- [[Introduction to Evolutionary Computing by Eiben]] pp 86


## Explanation





-----------
##  Recommended Notes and References


- [[Population Management Models for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]
- [[Evolutionary Computation Algorithms]]
- [[Comparison of Population-based Methods]]
- [[Derivative-Free Optimization]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 302
- [[Introduction to Evolutionary Computing by Eiben]] pp 80 - 87