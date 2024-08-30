---
tags:
  - concept
  - evolutionary_computation
  - optimization
keywords:
  - evolutionary_computation
  - diversity
  - population management
topics:
  - evolutionary_computation
name: Diversity Maintenance for Evolutionary Computation
date of note: 2024-08-29
---

## Concept Definition

>[!important]
>**Name**: Diversity Maintenance for Evolutionary Computation

![[Evolutionary Computation Algorithms#^ac42fa]]

![[Evolutionary Computation Algorithms#^12072d]]

>[!quote]
>**Multimodality** is a typical aspect of the type of problems for which EAs are often employed, either in attempt to locate the global optimum (particularly when a local optimum has the largest basin of attraction), or to identify a number of high–fitness solutions corresponding to various local optima. ... it is probably desirable to use solutions from niches with *broader peaks* rather than from a sharp peak. This is because the latter may be *overfitted* (that is, *overly specialised*) to the current fitness function and may not be as good once the fitness function is refined.
>
>The *population-based nature* of EAs holds out much promise for identifying **multiple optima**, however, in practice the finite population size, when coupled with recombination between any parents (known as **panmictic mixing**) leads to the phenomenon known as **genetic drift** and eventual convergence around *one optimum*.
>
>-- [[Introduction to Evolutionary Computing by Eiben]] pp 91

>[!quote]
>A number of mechanisms have been proposed to aid the use of EAs on *multimodal problems*. These can be broadly separated into two camps: **explicit approaches**, in which specific changes are made to operators in order to **preserve diversity**, and **implicit approaches**, in which a framework is used that permits, but *does not guarantee*, the preservation of diverse solutions. Before describing these it is useful to clarify exactly what we mean by ‘**diversity**’ and ‘**space**’.
>
>-- [[Introduction to Evolutionary Computing by Eiben]] pp 92

>[!important] Definition
>so we can define a number of spaces within which the evolutionary algorithms operate:
>- **Genotype Space**: We may perceive the set of *representable solutions* as a genotype space and define some *distance metrics*. This can be a natural distance metrics in that space (e.g., the **Manhattan distance**) or based on some fundamental *move operator*.
>- **Phenotype Space**: This is the end result: a *search space* whose structure is based on distance metrics between solutions. The neighbourhood structure in this space may bear little relationship to that in the genotype space according to the complexity of the *representation–solution mapping*.
>- **Algorithmic Space**: This is the equivalent of the geographical space on which life on Earth has evolved. Effectively we are considering that the *working memory* of the EA, that is, the **population** of *candidate solutions*, can be structured in some way.

### Fitness Sharing

>[!important] Definition
>The **fitness sharing scheme** is based upon the idea that the number of individuals within a *given niche* is controlled by *sharing* their fitness immediately *prior to selection*, in an attempt to allocate individuals to niches in *proportion* to the *niche fitness*.
>
>Consider a pair of individuals $x_{i}$ and $x_{j}$ within the population $\mathcal{S}$. Let $$d(x_{i}, x_{j})$$ be a *metric distance* between $x_{i}$ and $x_{j}.$ For instance, the *Hamming distance* between binary representations.
>
>The **fitness** for individual $x_{i}$ is **adjusted** as
>$$
>\widetilde{f}(x_{i}) = \frac{f(x_{i})}{\sum_{j}h\left( d(x_{i}, x_{j}) \right) }
>$$
>where the function $h$ is called the **sharing function**
>$$
>h(d) = \left\{ \begin{array}{ll}1 - \left( \dfrac{d}{\sigma_{\text{share}}} \right)^{\alpha} & \text{ if }d\le \sigma_{\text{share}} \\[5pt] 0 & \text{ otherwise} \end{array}  \right. 
>$$
>- $\alpha >0$ controls the shape of the sharing function
>- $\sigma_{\text{share}} >0$ controls the **share radius**, i.e. all individuals in $\sigma_{share}$-ball $\mathcal{B}_{d}(x_{i}; \sigma_{share})$ are considered as sharing the same niche.
>  
>In  parent selection, we use the **fitness proportional selection**.

- [[Weighted Hamming Distance]]
- [[Metric Topology and epsilon-ball]]
- [[Parent Selection for Evolutionary Computation]]

### Crowding

>[!important] Definition
>The **crowding algorithm** was first suggested in De Jong’s thesis as a way of *preserving diversity* by ensuring that new individuals **replaced similar members** of the population.
>
>When a new offspring is inserted into the population, 
>- a number of members (called the **crowding factor**) of the *parent population* are *chosen at random*, and 
>- then the *offspring* replaces the **most similar** of those *parents*.


- [[Population Management Models for Evolutionary Computation]]

>[!important] Definition
>The **deterministic crowding algorithm** suggested an improvement over crowding algorithm. 
>
>- The parent population is *randomly paired*. 
>- Each pair produces *two offspring* via recombination. 
>- These offspring are *mutated* and then evaluated. 
>- The **four pairwise distances** between *offspring and parents* are calculated. 
>- Each offspring then **competes for survival** in a **tournament** with **one parent**, so that the intercompetition distances are *minimised*. 
>	- In other words, denoting the parents as $p$, the offspring as $o$, and using the subscript to indicate tournament pairing, $$d(p_{1} , o_{1}) + d(p_{2} , o_{2}) < d(p_{1} , o_{2}) + d(p_{2} , o_{1}).$$

- [[Parent Selection for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]

>[!info]
>The net result of all this is that **offspring tend to compete for survival with the most similar parent**, so subpopulations are *preserved in niches* but their size does not depend on fitness; rather it is equally distributed amongst the peaks available.

![[deterministic_crowding_ea.png]]



## Explanation





-----------
##  Recommended Notes and References


- [[Evolutionary Computation Algorithms]]
- [[Population Management Models for Evolutionary Computation]]
- [[Parent Selection for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]


- [[Introduction to Evolutionary Computing by Eiben]] pp 92 - 94