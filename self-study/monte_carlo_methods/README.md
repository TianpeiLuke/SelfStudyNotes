# Monte Carlo Sampling Methods

## Books 

***Monte Carlo Statistical Methods***, Christian P. Robert and George Casella

***Monte Carlo Strategies in Scientific Computing***, Jun S.Liu

***Handbook of Markov Chain Monte Carlo***, Steve Brooks, Andrew Gelman, Galin L. Jones, Xiao

***A Conceptual Introduction to Hamiltonian Monte Carlo***, Michael Betancourt

***An Introduction to Hamiltonian Monte Carlo Method for Sampling***, Nisheeth K. Vishnoi

***Calculus Of Variations***, I. M. Gelfand, S. V. Fomin


## Table of Contents
- Summary [pdf](./0_monte_carlo_sampling_summary.pdf)

- Fundamental of Monte Carlo Sampling Methods [pdf](./1_importance_sampling.pdf)
  - Why Monte Carlo ?
  - Random Variable Generation
  - Reject Sampling
  - Variance Reduction

- Importance Sampling [pdf](./1_importance_sampling.pdf)
  - Algorithm
  - Sequential Importance Sampling (SIS)
  - Nonlinear Filtering, Particle Filter (Sequential Importance Resampling)

- Introduction to Markov Chain Stochastic Process [pdf](./2_mc.pdf)
  - Markov Chain
    - Definitions
    - Hitting Time
  - Classification of States
    - Equivalence Class by Communication
    - Foster Theorem and Poke's Lemma
  - Limiting and Stationary Distribution 
    - Invariant Measure
    - Ergodicity
    - Mean Hitting Time Formula
  - Time-Reversible Markov Chain
  - Ergodic Theorem and Central Limit Theorem

- Markov Chain Monte Carlo Sampling Methods [pdf](./3_mcmc.pdf)
  - Basic Concept from Markov Chain
  - Markov Chain Monte Carlo
    - From Vanilla Monte Carlo to Markov Chain Monte Carlo
    - Metropolis-Hastings Algorithm
  - Special Metropolis-Hastings Algorithms
    - Random-Walk Metropolis-Hastings
    - Independence Metropolis-Hastings
    - Configurational Bias Monte Carlo

- Gibbs Sampling [pdf](./4_gibbs.pdf)
  - Drawbacks of Metropolis-Hastings Algorithms
  - Gibbs Sampling
    - Slice Sampling
    - Gibbs Sampling
    - The Hammersley-Cliffold Theorem
    - Partial Resampling
    - Probabilistic Structure of Two-Stage Gibbs Sampling Markov Chain
    - Theoretical Justifications
  - Gibbs Sampling as Metropolis-Hastings Algorithms
  - Metroplized Gibbs Sampling

- Hamiltonian Monte Carlo Methods [pdf](./5_hmc.pdf)
  - Calculus of Variations
    - Basic Theorems in Calculus of Variations 
    - Euler-Lagrangian Equations
    - Hamilton's Equations
    - Hamiltonian Dynamics and its Properties
  - Markov Chain Monte Carlo From Hamiltonian Dynamics
    - Monte Carlo in High Dimensional Space
    - Hamiltonian Monte Carlo
    - Idealized Hamiltonian Monte Carlo
    - The Natural Geometry of Phase Space
    - Properties of Hamiltonian Monte Carlo
    - Euclidean-Gaussian Kinetic Energies
  - Hamiltonian Monte Carlo in Practice
    - Symplectic Integrators
    - Correcting Errors for Symplectic Integrators 
  - Connection with Topology
  
- Monte Carlo Optimization Methods [pdf](./6_mc_optimzation.pdf)
  - Stochastic Optimization Problems
  - Stochastic Explortation
    - Gradient Methods, Stochastic Gradient Descent
    - Simulated Annealing
    - Simulated Tempering
  - Stochastic Approximation
    - EM Algorithm
    - Monte Carlo EM Algorithm
