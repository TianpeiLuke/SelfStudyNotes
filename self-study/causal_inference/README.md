# Causal Inference and Causal Analysis

## Books

***Introduction to Causal Inference - from a Machine Learning Perspective***, Brady Neal

***Elements of Causal Inference: Foundations and Learning Algorithms***, Jonas Peters, Dominik Janzing, and Bernhard Scholkopf

***Causality: Models, Reasoning and Inference***, Judea_Pearl, 2nd

***Design of Observational Studies***, P. R. Rosenbaum, 2nd ed, 2020 

***Causal Inference for Statistics, Social, and Biomedical Sciences: An Introduction***, Guido Imbens, Donald Rubin


## Table of Contents
- Fundamental of Causal Inference [pdf](./CI_1_causal_inference.pdf)
  	- Association Does Not Imply Causation
	- Potential Outcomes
		- Potential Outcomes and Individual Treatment Effects
		- The Fundamental Problem of Causal Inference
		- Average Treatment Effects and Causal Assumptions
			- Ignorability and Exchangeability
			- Conditional Exchangeability and Unconfoundedness
			- Positivity/Overlap and Extrapolation
			- No Interference, Consistency, and SUTVA
	- Structural Causal Models
	- Basic process in Causal Inference

- Causal Graphical Models [pdf](./CI_2_causal_graphical_models.pdf)
	- Directed Graphical Models
	- Causal Graphial Models
	- Structural Causal Models 
		- Cause-Effect models 
		- Intervention
		- Counterfactuals
		- Do-calculus
		- Truncated Factorization
	- The Principle of Independent Mechanisms
	- Controling Confounding Factor
		-  Back-Door Adjustment
		-  Collider Bias and Why to Not Condition on Descendants of Treatment
		-  Compare to Adjustment Formula

- Randomized Experiments [pdf](./CI_3_random_exp.pdf)
	- Association is Causation in Completely Randomized Experiments
		- Comparability and Covariate Balance
		- Exchangeability
		- No Backdoor Path
	- Causal Inference in Randomized Experiments
		- Hypothesis Testing
		- Attributable Effects

- Observational Studies [pdf](./CI_4_observ_studies.pdf)
	- Controlling Confounding Bias
		- The Back-Door Adjustment
		- The Front-Door Adjustment
		- Propensity Scores
	- Controlling Covariate Balance by Matching
		- Matching directly on Confounders
		- Greedy Matching by Nearest Neighbor
		- Optimal Pair Matching
		- Matching by Propensity Score
		- Accessing Balance
	- Unobserved Confounding
		- Bounds
			- No-Assumptions Bound
			- Monotone Treatment Response
			- Monotone Treatment Selection
			- Optimal Treatment Selection
		- Sensitivity Analysis

- Causal Estimations [pdf](./CI_5_causal_estimation.pdf)
	- Conditional Outcome Modeling
	- Inverse Probability Weighting 
	- Doubly Robust Methods

- Instrumental Variables [pdf](./CI_6_instrumental_variables.pdf)
	- What is an Instrument
	- Linear Setting
		- Binary Linear Setting
		- Continuous Linear Setting 
	- Nonparametric Identification of Local ATE
		- New Potential Notation with Instruments
		- Principal Stratification
		- Local ATE
	- Weak Instruments
