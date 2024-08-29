---
tags:
  - concept
  - optimization/theory
  - genetic_algorithm
  - evolutionary_algorithm
keywords:
  - genetic_algorithm
topics:
  - optimization
  - evolutionary_algorithm
name: Genetic Algorithms
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: Genetic Algorithms

>[!important] 
>In a **genetic algorithm (GA)**, we use **mutation** and a particular **recombination** method based on **crossover**. 
>- To implement **crossover**, we assume each individual is represented as a vector of *integers or binary numbers*, by analogy to chromosomes. We pick a *split* point along the chromosome for each of the two chosen parents, and then *swap* the strings,

- [[Parent Selection for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]

>[!important] 
>GAs traditionally have a **fixed workflow**: 
>- given a population of $\mu$ individuals, **parent selection** fills an *intermediary population* of $\mu$, allowing *duplicates*. 
>- Then the intermediary population is **shuffled** to create *random pairs* and **crossover** is applied to each consecutive pair **with probability** $p_{c}$
>- and the children **replace** the parents immediately.
>- The new intermediary population undergoes **mutation** individual by individual, where each of the $l$ bits in an individual is modified by mutation *with independent probability* $p_m$.
>- The resulting intermediary population forms **the next generation** replacing the previous one entirely.


![[genetic_algorithm.png]]




## Explanation

>[!quote]
>despite its simplicity, the **SGA (Simple Genetic Algorithm)** is still widely used, not just for teaching purposes, and for benchmarking new algorithms, but also for relatively straightforward problems in which *binary representation* is suitable.
>
>-- [[Introduction to Evolutionary Computing by Eiben]] pp 100

## Crossover Operation

### One-Point Crossover

>[!important] Definition
>**One-point crossover** works by 
>- choosing a *random number* $r$ in the range $[1,l− 1]$ (with $l$ the *length* of the encoding), and 
>- then *splitting* both parents at this point and 
>- *creating* the two children by *exchanging the tails*

### n-Point Crossover

>[!important] Definition
>One-point crossover can easily be generalised to **$n$-point crossover**, where 
>- the chromosome is broken into *more than two segments* of contiguous genes, and 
>- the offspring are created by *taking alternative segments* from the parents. 
>- In practice this means choosing $n$ *random crossover points* in $[1,l−1]$

![[crossover_ga.png]]

### Uniform Crossover

>[!info]
>The previous two operators worked by dividing the parents into a number of sections of contiguous genes and reassembling them to produce offspring. In contrast to this, **uniform crossover** works by treating each gene *independently* and making a *random choice* as to *which parent* it should be inherited from.

>[!important] Definition
>In **uniform crossover**, 
>- a string of $l$ *random variables* from a uniform distribution over $[0,1]$ is generated. 
>- In each position, 
>	- if the value is *below a parameter* $p$ (usually 0.5), the gene is *inherited* from the first parent; 
>	- *otherwise* from the second. 
>- The second offspring is created using the *inverse mapping*.

## Mutation on Binary Representation

>[!important] Definition
>The most common **mutation operator** for binary encodings considers each gene *separately* and allows each bit to *flip* (i.e., from 1 to 0 or 0 to 1) with a small probability $p_{m}$. This is called the **$1$-bit flip mutation**.





-----------
##  Recommended Notes and References


- [[Genetic Programming]]
- [[Parent Selection for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]

- [[EDA or Estimation of Distribution Algorithm]]
- [[Evolutionary Computation Algorithms]]
- [[Derivative-Free Optimization]]


- [[Introduction to Evolutionary Computing by Eiben]] pp 14, 99, 104
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 298 - 307