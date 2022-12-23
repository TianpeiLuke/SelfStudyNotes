# Probabilistic Graphical Models

## Books

***Graphical Models, Exponential Families, and Variational Inference***, Martin J. Wainwright and Michael I. Jordan

***Probabilistic Graphical Models Principles and Techniques***, Daphone Koller, Nir Friedman

***Information Theory, Inference, and Learning Algorithms***, David J. C. Mackay

## Table of Contents

- Probabilistic Graphical Models [pdf](./GM_1_prob_graphical_models.pdf)
  - Introductions
  - Probabilistic Graphical Models
    - Directed Graphical Models (Bayesian Networks)
    - Undirected Grapical Models (Markov Networks)
    - Factor Graph Representation
    - Notes
    - Representation of Factors 
      - Tabular Representation 
      - Function approximation
  - Conditional independence
  - Examples
    - Ising Models (Binary Markov Random Field)
    - Gaussian Graphical Models (GGM)
    - Hidden Markov Chain (HMM)
    - Conditional Random Field (CRF)
    - Latent Dirichlet allocation (LDA)
    - Restricted Boltzmann machine (RBM)
 
- Exponential Families and Variational Representation [pdf](./GM_2_exp_fam_inference.pdf)
  - Definitions
  - Exponential family via maximum entropy
    - Maximum Entropy Estimation
    - Properties of Log-Partition Function
    - Conjugate Duality: Maximum Likelihood and Maximum Entropy
    - Challenges in High Dimensional Setting
    - Primal-Dual Formulation of KL Divergence

- Inference in Tabular-Based Graphical Models [pdf](./GM_3_inference_tab.pdf)
  - Inference in Graphical Models
  - Inference for Tabular-Based Graphical Models
  - Exact Marginal Inference on Tree-Structure Model
    - Sum-product Belief Propagation
    - Factor Graph Message Passing
    - Bellman Equation in Log-Space
  - Exact Mode Inference on Tree-Structure Model 
  - Junction Tree Representation

- Variational Inference in Exponential Family Graphical Models [pdf](./GM_4_variational_inference_exp.pdf)
  - Approximate Inference via Variational Methods
  - Belief Propagation for Exponential Families
    - Approximate Marginal Polytope via Pseudo-Marginal Distributions
    - Bethe Entropy Approximation
    - Sum-Product for Bethe Variational Problem
    - Reparameterization
  - Expectation Propagation
  - Mean Field Approximation
    - Tractable Families
    - Mean Field Lower Bound and the Problem Formulation
    - Variational Representation of Mean Field
    - Naive Mean Field Algorithms
    - Nonconvexity of Mean Field

- Parameter Estimation in Graphical Models [pdf](./GM_5_param_est.pdf)
  - Parameter Estimation in Fully Observed Models
  - Parameter Estimation in Partially Observed Models
    - Exact EM Algorithm in Exponential Families
    - Variational EM
    - Variational Bayes

