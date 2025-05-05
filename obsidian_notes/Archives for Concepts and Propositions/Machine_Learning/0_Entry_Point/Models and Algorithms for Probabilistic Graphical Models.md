---
tags:
  - entry_point
  - concept
  - machine_learning/theory
  - machine_learning/models
  - machine_learning/metrics
  - statistics/concentration_inequality
  - math/stochastic_process
keywords: 
topics:
  - machine_learning_theory
  - machine_learning_models
  - concentration_inequality
  - stochastic_process
  - machine_learning_metrics
  - machine_learning_algorithm
name: 
date of note: 2024-06-01
---

## List of Concepts

### Conditional Independence 

- [[Conditional Independence]]
- [[Probabilistic Graphical Models]]
- [[I-Map and Independence Assertion]]
- [[Confounding in Conditional Independence]]

### Graphical Model Representation

#### Bayesian Network 

- [[Bayesian Network on Directed Acyclic Graph]]
- [[D-Separation in Bayesian Network]]
- [[Soundness and Faithfulness of D-Separation in Bayesian Net]]
- [[I-Equivalence between Two Graphs]]
- [[Minimal I-Map]]
- [[Perfect Map for Independence Assertions]]
- [[Statistical Equivalence between Graphical Models]]
- [[Bayesian Network Distribution to Graph]]
- [[Local Probabilistic Models]]

#### Markov Network

- [[Gibbs Distribution]]
- [[Markov Network on Undirected Graph]]
- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Reduced Markov Networks]]
- [[Separation in Markov Network]]
- [[Positive Distribution]]
- [[Soundness and Faithfulness of Separation in Markov Net]]
- [[Hammersley-Clifford Theorem]]
- [[Markov Blanket and Local Markov Independence]]
- [[Markov Network Distribution to Graph]]

#### Comparison

- [[Bayesian Network and Markov Network Comparison]]
- [[Bayesian Network as Markov Network]]

#### Graphical Model with Continuous Variables

- [[Challenges on Graphical Model with Continuous Variables]]


#### Graphical Model with Continuous Variables

- [[Challenges on Graphical Model with Continuous Variables]]

#### Dynamic Bayesian Network

- [[Dynamic Bayesian Network]]
- [[State-Observation Models]]
	- [[Linear Dynamic System]]
	- [[State Space Models and Nonlinear Dynamic System]]
- [[Statistical Prediction Filtering and Smoothing for State Observation Model]]
- [[Bayesian Filtering and Smoothing Equations for State Observation Models]]

- [[Autoregressive Models]]
- [[Recurrent Neural Network]]
- [[Hidden Markov Model]]
- [[Kalman Filter Discrete-Time]]
- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]


### Chordal Graph, Clique Tree

- [[Chordal Graph and Triangulation]]
- [[Cluster Graph and Family Preservation]]
- [[Clique Tree and Graph and Running Intersection Property]]
- [[Clique Tree Construction]]

### Exponential Family and Graphical Model

- [[Exponential Family of Distributions]]
- [[Generalized Linear Models]]
- [[Log-Partition Function of Exponential Family]]
- [[Fisher Information for Exponential Family]]
- [[Information Projection and Moment Projection]]

- [[Maximum Likelihood Estimation of Exponential Family]]
- [[Maximum Likelihood Estimation of Generalized Linear Models]]

- [[Maximum Entropy Learning of Exponential Family]]
- [[Convex Conjugate of Log-Partition Function of Exponential Family]]

- [[Exponential Family and Convex Duality]]
- [[Exponential Family as Probabilistic Graphical Model]]

- [[Softmax Function and Log-Sum-Exp Function]]

### Examples

- [[Canonical Form of Gaussian Graphical Model]]
- [[Naive Bayes Model]]
	- [[Multinomial Naive Bayes Model]]
- [[Hidden Markov Model]]
- [[Kalman Filter Discrete-Time]]
- [[Recurrent Neural Network]]
- [[Conditional Random Field]]
- [[Latent Dirichlet Allocation]]
- [[Restricted Boltzmann Machine or RBM]]
- [[Ising Model]]
- [[Markov Logic Network for Probabilistic First-Order Logic]]
- [[Constraint Satisfaction Problem or CSP]]
- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]

### Exact Inference for Graphical Model

- [[Conditional Probability Query of Graphical Model]]
- [[Complexity of Exact Marginal and Conditional Inference in Bayes Net]]

#### Exact Inference via Variable Elimination

- [[Sum-Product Variable Elimination]]
- [[Rule-based Variable Elimination in Graphical Model]]

#### Message Passing in Clique Trees

- [[Clique Tree and Graph and Running Intersection Property]]
- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Correctness of Belief Propagation for Clique Tree]]
- [[Clique Tree Calibration]]
- [[Clique Tree Invariant of Sum Product and Reparameterization of PGM]]
- [[Sum-Product Belief-Update Message Passing Algorithm for Clique Tree]]
- [[Belief Propagation and Belief Update Equivalence for Clique Tree]]
- [[Gaussian Belief Propagation]]


#### Exact Inference via Maximum Entropy Learning

- [[Maximum Entropy Learning]]
- [[Maximum Entropy Learning of Clique Tree PGM]]
- [[Marginal Polytope and Local Consistent Polytope]]
- [[Exponential Family as Probabilistic Graphical Model]]

#### Exact Inference in Temporal Models

- [[Bayesian Filtering and Smoothing Equations for State Observation Models]]
- [[Hidden Markov Model Inference via Forward-Backward Algorithm]]
- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]
- [[Kalman Filter Discrete-Time]]


#### Variational Inference on Clique Tree

- [[Energy Functional for Probabilistic Graphical Model]]
- [[Bethe Entropy Approximation and Factorized Energy Functional]]
- [[Bethe Variational Inference for Clique Tree]]
- [[Stationary Point of Bethe Variational Inference Problem]]
- [[Variational Inference for Clique Tree]]

### Approximate Inference for Graphical Model

- [[Maximum Entropy Learning for Approximate Inference in PGM]]

#### Approximation via Cluster Graph

- [[Cluster Graph and Family Preservation]]

- [[Loopy Belief Propagation Algorithm for Cluster Graph]]

#### Propagation with Approximate Message 

- [[Factorized Message for Approximate Belief Propagation]]
- [[Sum-Product Expectation Propagation Algorithm]]
- [[Sum-Product Belief-Update Expectation Propagation Algorithm]]
- [[Expectation Propagation and Exponential Family Messages]]
- [[Variational Inference Formulation of Expectation Propagation]]

#### Structured Variational Approximation

- [[Structured Variational Approximation]]
- [[Mean Field Approximation for PGM]]
- [[Mean Field Approximation for Exponential Family]]
- [[Mean Field Approximation for Gaussian Markov Random Field]]

### Sampling-based Approximate Inference 

- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Concepts and Algorithms for Monte Carlo Methods]]
- [[Markov Chain Monte Carlo Methods]]
- [[Metropolis-Hastings Algorithm]]
- [[Random Walk Metropolis-Hastings]]
- [[Gibbs Sampling]]
- [[Gibbs Sampling for Graphical Model]]

- [[Sequential Importance Sampling]]
- [[Particle Filter or Sampling-Importance-Resampling]]


### MAP Inference

- [[Maximum A Posteriori Probability Query of Graphical Model]]
- [[Complexity of Exact MAP Inference in Bayes Net]]
- [[Maximum Marginal of Factor in Graphical Model]]

#### Exact Inference via Variable Elimination

- [[Max-Product Variable Elimination]]

#### Message Passing in Clique Trees

- [[Max-Product Belief Propagation for Clique Tree]]
- [[Max-Product Belief Update for Clique Tree]]
- [[Clique Tree Invariant of Max-Product and Reparameterization]]
- [[Decoding Max-Marginal for Graphical Model]]

- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]

#### Graph Cut Method

- [[Graph Cut for MAP Inference in Graphical Model]]

### Gaussian Graphical Model

- [[Challenges on Graphical Model with Continuous Variables]]
- [[Canonical Form of Gaussian Graphical Model]]
- [[Independence in Gaussian Distribution]]
- [[Gaussian Bayesian Network]]
- [[Gaussian Graphical Model]]
- [[Gaussian Belief Propagation]]
- [[Mean Field Approximation for Gaussian Markov Random Field]]


- [[Inverse Covariance Estimation]]
- [[Partial Correlation]]
- [[Sparse Inverse Covariance Estimation for GGM with Known Structure]]
- [[Graph LASSO and Structured Learning in Gaussian Graphical Model]]
- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]

### Learning of Graphical Model

- [[Statistical Estimation Problem]]
- [[Maximum Likelihood Estimation of Bayesian Network]]
- [[EDA or Estimation of Distribution Algorithm]]


### Causal Graphical Model

- [[Concepts and Theorems in Causal Analysis and Causal Machine Learning]]
- [[Interventions in Causal Inference]]
- [[Counterfactual in Causal Inference]]
- [[Causal Graph]]
- [[Directed Connection in Causal Graph]]
- [[Structural Causal Models or SCMs]]



## Explanation




-----------
##  Recommended Notes and References

- [[Probabilistic Graphical Models by Koller]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]


- [[Artificial Intelligence Modern Approach by Russell]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]]
- [[Deep Learning Foundations and Concepts by Bishop]]

- Lecture
	- MIT Open Course [Algorithms for Inference Fall 2014](https://ocw.mit.edu/courses/6-438-algorithms-for-inference-fall-2014/)