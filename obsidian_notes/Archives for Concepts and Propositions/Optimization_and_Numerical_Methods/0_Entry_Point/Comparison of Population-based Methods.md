---
tags:
  - entry_point
  - concept
  - population_based_methods
  - evolutionary_computation
keywords: 
topics: 
name: 
date of note: 2024-08-26
---

## Concept Definition


|                                                                                                        | **Representation**                                                                                                               | **Recombination**                           | **Mutation**                                                     | **Parent Selection**                                               | **Survival Selection**                                                               | Speciality                                                                                                                 |
| ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- | ---------------------------------------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| Genetic Algorithm (**GA**)<br><br>[[Genetic Algorithms]]                                               | *Bit*-strings                                                                                                                    | 1-Point *crossover*                         | Bit flip                                                         | **Fitness proportional** - implemented by *Roulette Wheel*         | Generational                                                                         |                                                                                                                            |
| Evolutionary Strategy (**ES**)<br><br>[[Evolutionary Strategies]]                                      | Real-valued vectors                                                                                                              | *Discrete* or *intermediary*                | **Gaussian perturbation**                                        | Uniform random                                                     | **Deterministic elitist replacement** by $(\mu, \lambda)$ or $(\mu + \lambda)$<br>   | *Self-adaptation* of mutation step sizes                                                                                   |
| Evolutionary Programming (**EP**)<br><br>[[Evolutionary Programming]]                                  | Real-valued vectors                                                                                                              | *None*                                      | **Gaussian perturbation**                                        | *Deterministic* (each parent creates one offspring via mutation)   | **Probabilistic** $(\mu + \lambda)$                                                  | *Self-adaptation* of mutation step sizes (in meta-EP)                                                                      |
| Genetic Programming (**GP**)<br><br>[[Genetic Programming]]<br>                                        | **Tree structures**                                                                                                              | **Exchange of subtrees**                    | *Random change* in trees                                         | **Fitness proportional**                                           | **Generational replacement**                                                         |                                                                                                                            |
| Learning Classifier Systems (LCS)                                                                      | **tuple** of (<br> **condition**,<br> **action**,<br> **payoff**,<br> **accuracy**)<br><br>conditions use $\{0,1, \#\}$ alphabet | *One-point crossover* on conditions/actions | **Binary/ternary resetting** as appropriate on action/conditions | **Fitness proportional** with sharing within environmental niches  | *Stochastic*, inversely related to number of rules covering same environmental niche | Each reward received updates *predicted payoff and accuracy* of rules in relevant action sets by *reinforcement learning*. |
| Differential Evolution (DE)<br><br>[[Differentiable Cross-Entropy Method]]<br><br><br>                 | Real-valued vectors                                                                                                              | Uniform *crossover*                         | **Differential mutation**                                        | *Uniform random selection* of the 3 necessary vectors              | **Deterministic elitist replacement** (parent vs. child)                             |                                                                                                                            |
| Particle Swarm Optimization (PSO)<br><br>[[Particle Swarm Optimization]]<br>                           | Real-valued vectors                                                                                                              | **None**                                    | Adding **velocity vector**                                       | **Deterministic** (each parent creates one offspring via mutation) | **Generational** (offspring replace parents)                                         |                                                                                                                            |
| Estimation of Distribution algorithm (EDA) <br><br>[[EDA or Estimation of Distribution Algorithm]]<br> | Discrete or Real-valued vectors                                                                                                  | None                                        | None<br> <br>                                                    | **Fitness proportional**                                           | Generational                                                                         | Replace recombination and mutation with (**model selection**, **model estimation**, **model sampling**)                    |

- [[Parent Selection for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]
- [[Introduction to Evolutionary Computing by Eiben]] pp 99 - 118




## Explanation





-----------
##  Recommended Notes and References

- [[Genetic Algorithms]]
- [[Genetic Programming]]
- [[Evolutionary Strategies]]
- [[Evolutionary Programming]]
- [[Particle Swarm Optimization]]




- [[Introduction to Evolutionary Computing by Eiben]] pp 113 - 116