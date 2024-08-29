---
tags:
  - concept
  - evolutionary_computation
keywords:
  - survival_selection
  - evolutionary_computation
topics:
  - evolutionary_computation
  - optimization
name: Survivor Selection for Evolutionary Computation
date of note: 2024-08-27
---

## Concept Definition

>[!important]
>**Name**: Survivor Selection for Evolutionary Computation

>[!important] 
>The **survivor selection mechanism** is responsible for managing the process of *reducing the working memory* of the EA from a set of $\mu$ *parents* and $\lambda$ *offspring* to a set of $\mu$ individuals forming the *next generation*. In principle, any of the mechanisms introduced for **parent selection** could be also used for selecting survivors. However, over the history of EC a number of special survivor selection strategies have been suggested and are widely used.

### Age-based Replacement

>[!important] Definition
>The basis of the **age-based replacement schemes** is that the *fitness* of individuals is *not taken into account* during the selection of which individuals to replace in the population. Instead, they are designed so that each individual *exists* in the population for the *same number* of EA iterations.

>[!info]
>This does not preclude the possibly that *copies* of highly-fit individuals might persist in the population, but for this to happen they must be chosen *at least once* in the selection phase and then survive the recombination and mutation stages *without being modified*.

>[!info]
>In **steady-state population management model**, when $\lambda=1$, it is the same form of **First-In-First-Out (FIFO)** queue.

 - [[Population Management Models for Evolutionary Computation]]

### Fitness-based Replacement

>[!info]
>A wide number of strategies *based on fitness* have been proposed for choosing which $\mu$ of the $\mu$ *parents* $+ \lambda$ *offspring* should go forward to the next generation.


>[!important] Definition
>In the **replace worst (GENITOR) scheme**, 
>- the *worst* $\lambda$ among the total $\mu$ members of population  are selected for *replacement*.
>- Note that $\lambda < \mu$

>[!info]
>Although this can lead to very *rapid improvements* in the *mean population fitness*, it can also lead to *premature convergence* as the population tends to rapidly focus on the fittest member.

- [[Genetic Algorithms]]

>[!important] Definition
>In the **elitism scheme**,
>- a *trace* is kept of the current fittest member (called the **elite**), and it is *always kept* in the population.
>- if it is chosen in the group to be *replaced*, and none of the *offspring* being inserted into the population has *equal or better fitness*, then it is kept and one of the offspring is discarded.

>[!info]
>This scheme is commonly used in conjunction with *age-based* and *stochastic fitness-based* replacement schemes, to prevent the loss of the current fittest member of the population.

- [[Differential Evolution Algorithm]]


>[!important] Definition
>In the **round-robin tournament scheme**,
>- pairwise tournament competitions are held in round-robin format, where *each* individual is evaluated against *$q$ others randomly* chosen from the *merged* parent and offspring populations.
>- For each comparison, a “*win*” is assigned if the individual is *better* than its opponent. 
>- After finishing all tournaments, the $\mu$ individuals with the *greatest number of wins* are selected.

- [[Parent Selection for Evolutionary Computation#Tournament Selection]]
- [[Evolutionary Programming]]
- [[Contrastive Learning]]


>[!important] Definition
>In **$(\mu +\lambda)$ scheme**,  
>- the set of offspring and parents are *merged* and *ranked* according to (estimated) fitness
>- then the *top* $\mu$ is kept to form *a new generation*.

>[!info]
>This strategy can be seen as a **generalisation** of 
>- the *GENITOR method* $(\mu > \lambda)$ and
>- the *round-robin tournament* in Evolutionary Programming $(\mu = \lambda)$.  

- [[Evolutionary Programming]]
- [[Evolutionary Strategies]]

>[!important] Definition
>In **$(\mu ,\lambda)$ scheme**,  
>- $\lambda$ children are *created* from a population of $\mu$ *parents* where  $\lambda > \mu$.
>- This method works on a **mixture** of *age* and *fitness*.
>	- The *age* component means that *all the parents are discarded*, so no individual is kept for more than one generation.
>	- The *fitness* component comes from the fact that the $\lambda$ *offspring* are *ranked* according to the fitness, and the best $\mu$ form the *next generation*.

- [[Evolutionary Strategies]]

>[!info]
>In [[Evolutionary Strategies]], $(\mu ,\lambda)$ scheme is generally **preferred** over $(\mu +\lambda)$ scheme
>- The $(\mu ,\lambda)$  *discards all parents* and is therefore in principle able to leave (small) local optima. This may be advantageous in a multimodal search space with many local optima.
>- If the fitness function is not fixed, but *changes in time*, the $(\mu +\lambda)$ selection preserves *outdated solutions*, so it is not able to follow the moving optimum well.
>- $(\mu +\lambda)$ selection hinders the *self-adaptation mechanism* used to adapt strategy parameters





## Explanation





-----------
##  Recommended Notes and References


- [[Population Management Models for Evolutionary Computation]]
- [[Parent Selection for Evolutionary Computation]]
- [[Evolutionary Computation Algorithms]]
- [[Comparison of Population-based Methods]]
- [[Derivative-Free Optimization]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 302
- [[Introduction to Evolutionary Computing by Eiben]] pp 88 - 90