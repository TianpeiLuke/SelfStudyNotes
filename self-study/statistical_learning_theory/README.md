# Statistical Learning Theory and Machine Learning Algorithms

## Books

### Statistical Learning Theory

***Understanding Machine Learning: From Theory To Algorithms***, Shalev-Shwartz S., Ben-David S.

***Foundations of Machine Learning***, Mehryar Mohri, Afshin Rostamizadeh, Ameet Talwalkar

***A Probabilistic Theory of Pattern Recognition***, Devroye, Gyorfi, Lugosi

### Machine Learning Algorithms

#### Kernel Methods

***Learning With Kernels Support Vector Machines, Regularization, Optimization, And Beyond***, Bernhard Schölkopf, Alexander J. Smola

***Gaussian Process for Machine Learning***, C.E. Rasmussen, C.K.I. Williams

#### Boosting

***Boosting: Foundations and Algorithms***, Robert E Schapire, Yoav Freund

## Table of Contents

### Statistical Learning Theory

- Basic Concepts of Statistical Learning [pdf](./SL_lecture1_Fundamentals.pdf)
  - Concepts, Definitions and Assumptions
    - Categories of Machine Learning Fields 
    - Data, Concept Class, Hypothesis Class
    - Deterministic and Stochastic Scenario
    - Generalization Error
    - Empirical Risk Minimization
    - Bayes Error
    - Approximation Error, Estimation Error and Bias-Complexity Tradeoff
    - Realizability Assumption
  - Consistency, Universal Consistency
  - No-Free-Lunch Theorem
  - Development Paths of Learning Algorithms

- Probably Approximately Correct (PAC) Learning [pdf](./SL_lecture2_ERM_PAC.pdf)
  - PAC Learning
    - Definitions
    - Generalization Bound for Finite Hypothesis Class
  - Agnostic PAC Learning
    - Definitions
    - Uniform Convergence
  - PAC Learning vs. Universal Consistency
  

- Radmatcher Complexity and VC-Dimension [pdf](./SL_lecture3_VC_Dimension.pdf)
  - Radmatcher Complexity, Symmetrization
  - VC-Dimension
  - Growth Number, Sauer's Lemma
  - Generalization Bound via Radmatcher Complexity, Growth Number and VC-Dimension
  - Fundamental Theorem of PAC Learning
  - Examples of Hypothese Class with Finite or Infinite VC Dimension

- Non-Uniform Learning and Structural Risk Minimization [pdf](./SL_lecture4_Nonuniform_PAC.pdf)
  - Non-Uniform Learning
  - Characterization of Non-Uniform Learning
  - Strctural Risk Minimization
  - Minimal Description Length

### Machine Learning Models
- k-Nearest Neighbor [pdf](./AL_kNN.pdf)
  - The Classification Rule
  - Asymptotic Analysis
    - Asymptotic Convergence of K-Nearest Neigbhor Distance 
    - Stone’s Lemma 
    - Stone’s Theorem, Universal Consistency of k-NN Classification Rule
  - Non-Asymptotic Analysis
    - Generalization Bounds for k-NN Rules
    - Curse of Dimensionality  

- Reproducing Kernel Hilbert Space [pdf](./AL_reproducing_kernel.pdf)
  - Reproducing Kernel Hilbert Space
    - Definition via Evaluation Functional
    - Construction via Positive Definite Kernel
    - Construction via Kernel Integral Operator
    - Construction via Feature Map
  - Machine Learning Applications
    - Empirical Risk Minimization with Regularization in RKHS
    - Representer Theorem

- Gaussian Process for Machine Learning
