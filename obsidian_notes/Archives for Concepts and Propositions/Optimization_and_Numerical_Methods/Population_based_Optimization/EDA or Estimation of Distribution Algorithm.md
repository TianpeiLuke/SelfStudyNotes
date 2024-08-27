---
tags:
  - concept
  - optimization/theory
  - genetic_algorithm
  - evolutionary_algorithm
keywords:
  - eda_algorithm
  - estimation_of_distribution_algorithm
topics:
  - optimization/algorithm
  - evolutionary_algorithm
name: EDA or Estimation of Distribution Algorithm
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: EDA or Estimation of Distribution Algorithm

![[Evolutionary Algorithms#^ac42fa]]

![[Evolutionary Algorithms#^12072d]]

- [[Evolutionary Algorithms]]

>[!important] Definition
>**Estimation of distribution algorithms (EDA)** are based on the idea of replacing the creation of offspring by ‘standard’ variation operators (*recombination* and *mutation*) by a three-step process:
>- First a *graphical model* is chosen to represent the *current state* of the search in terms of the *dependencies* between variables (genes) describing a candidate solution.
>- Next the *parameters* of this model are estimated from the *current population* to create a *conditional probability distribution* over the variables.
>- Finally, offspring are created by *sampling this distribution*.

^ad5721


>[!important] Definition
>The **estimation of distribution algorithms (EDA)** generate *offsprings* based on the following steps:
>- *Initialize* population $\mathcal{S}_{0}$ with $K$ random *candidate solutions*;
>- For $t= 0,\,1\,{,}\ldots{,}\,$ until the *termination condition* is satisfied:
>	- **Compute** the **fitness** for each candidate $X_{t}^{i}$ in $\mathcal{S}_{t}$, $$f(X_{t}^{i})$$
>	- **Select** a *subpopulation* $\mathcal{S}_{t}^{(s)}$ based on the *fittest* subset of the current population. $$\mathcal{S}_{t}^{(s)} = \left\{ X_{t}^{i}: f(X_{t}^{i}) \ge f(X_{t}^{(m)}) \right\}$$ where $$f(X_{t}^{(1)})  \,{\ge}\ldots{\ge}\, f(X_{t}^{(K)})$$
>	- **Model Selection**: 
>		- Create a *graph* $G = (V, E)$ based on dependencies in distribution $\mathcal{P}_{t}^{(s)}$
>	- **Model Fitting**: 
>		- Create a **bayesian network** $\mathcal{B} = (G, \mathcal{P}_{t}^{(s)})$ with graph $G$ and distribution $\mathcal{P}_{t}^{(s)}$ estimated from the subpopulation  $\mathcal{S}_{t}^{(s)}$
>	- **Model Sampling**:
>		- **Generate** a set of $K$ candidates $\mathcal{C}$ according to the learned *bayesian network* $\mathcal{B}$
>	- Choose the *offspring population* as the generated candidates $$\mathcal{S}_{t+1} = \mathcal{C}$$

- [[Probabilistic Graphical Models]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[Gibbs Sampling for Graphical Model]] 
- [[Maximum Likelihood Estimation of Bayesian Network]]


## Explanation

### Model Selection

>[!info]
>**Model selection** is the critical element in using a PGM approach to data modelling (in our case modelling a population in an EDA). In essence, it amounts to finding the *appropriate structure* to capture the *conditional (in)dependencies between variables*. In the context of genetics, and also of evolutionary computation, this process is also known as the “**Linkage Learning**” problem
>
>--  [[Introduction to Evolutionary Computing by Eiben]] pp 115

- [[I-Map and Independence Assertion]]

>[!quote]
>Historically the pattern of research in this area has progressed via permitting increasing complexity for the types of structural dependencies examined. The earliest univariate algorithms such as **PBIL** \[35\] assumed variables behaved independently. The second generation of EDAs such as **MIMIC** \[59\] and **BMDA** \[337\] selected structures from the possible pairwise interactions, and current methods such as **Bayesian Optimization algorithm (BOA)** \[336\] select structures from the set of all trees of some prespecified maximum size.
>
>-- [[Introduction to Evolutionary Computing by Eiben]] pp 115


>[!quote]
>Most of the discussion above has tacitly assumed **discrete combinatorial problems** and the models fitted have been **Bayesian networks**. For continuous variable problems a slightly different approach is needed to measure and describe probabilities, which is typically based on normal (Gaussian) distributions.
>
>-- [[Introduction to Evolutionary Computing by Eiben]] pp 115


>[!quote]
>It is straightforward to use more expressive probability models that capture dependencies between the parameters (these are known as **building blocks** in the EA literature). For example, in the case of real-valued parameters, we can use a multivariate Gaussian, $p(x) = N (x|\mu, \Sigma).$ The resulting method is called the **estimation of multivariate normal algorithm** or **EMNA**, [LL02]. (See also Section 6.7.5.)
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 305



>[!quote]
>We can also use **deep generative models** to represent the distribution over good candidates. For example, [CSF16] use *denoising autoencoders* and NADE models (Section 22.2), [Bal17] uses a DNN regressor which is then inverted using gradient descent on the inputs, [PRG17] uses *RBMs* (Section 4.3.3.2), [GSM18] uses *VAEs* (Section 21.2), etc. Such models might *take more data to fit* (and therefore more function calls), but can potentially model the probability landscape more faithfully. (Whether that translates to better optimization performance is not clear, however.)
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 305 - 306

- [[Variational Auto-Encoder]]
- [[Restricted Boltzmann Machine]]
- [[Auto-Encoder]]





-----------
##  Recommended Notes and References


- [[Gibbs Sampling for Graphical Model]] 
- [[Probabilistic Graphical Models]]
- [[Maximum Likelihood Estimation]]

- [[Population-based Incremental Learning]]
- [[Genetic Algorithms]]
- [[Evolutionary Algorithms]]
- [[Derivative-Free Optimization]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 298 - 307
- [[Introduction to Evolutionary Computing by Eiben]] pp 113 - 116