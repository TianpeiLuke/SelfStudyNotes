# Reinforcement Learning

## Books

***Reinforcement Learning: An Introduction***, Richard S. Sutton and Andrew G. Barto, 2nd Edition

***Markov Decision Processes: Discrete Stochastic Dynamic Programming***, Martin L. Puterman


## Table of Content

- Summary [pdf](./0_intro_terminology.pdf)

- Tabluar-Based Methods
  - Multi-Armed Bandit Problem [pdf](./1_multiarm_bandit.pdf)
    - Exploration and Exploitation
    - Action-Value Methods
    - Nonstationary Problem
    
  - Markov Decision Process (MDP) [pdf](./2_mdp.pdf)
    - Goal and Rewards
    - Average Rewards
    - Bellman Equation
    - Optimal Policy and Optimal Value Function, Bellman optimality equations

  - Dynamic Programming [pdf](./3_dp_policy_eval_control.pdf)
    - Policy Evaluation (Prediction)
    - Policy Iteration (Control)
    - Value Iteration
    - Generalized Policy Iteration
  
  - Monte Carlo Methods [pdf](./4_monte_carlo_methods.pdf)
    - Monte Carlo Methods for Prediction
    - Monte Carlo Methods for Control
    - On-Policy and Off-Policy Learning Without Exploring Starts
    - Off-Policy Monte Carlo Control

  - Temporal-Difference Learning [pdf](./5_td_learning.pdf)
    - Temporal-Difference Prediction 
    - Temporal-Difference Control 
      - SARSA
      - Q-Learning 
      - Expected SARSA
 
  - Planning and Learning with Tabular Methods [pdf](./6_planning_tab.pdf)
    - Models and Planning
    - Dyna: Integrated Planning, Acting, and Learning
 
- Function Approximation
  - On-policy Prediction with Function Approximation [pdf](./7_fun_approx_on_policy.pdf)
    - Value-Function Approximation as Supervised Learning
    - Stochastic Gradient and Semi-Gradient Methods
    - Linear Methods 
    - Value Function Approximation via Artificial Neural Networks

  - Control with Function Approximation [pdf](./8_fun_approx_on_policy_control.pdf)
    - Episodic Semi-Gradient Control
    - Average Rewards as New Problem Setting for Continuing Tasks
 
  - Policy Gradient Methods [pdf](./9_policy_grad_methods.pdf)
    - Value-based methods vs. Policy-based methods
    - Policy Approximation 
    - The Policy Gradient Theorem
    - REINFORCE: Monte Carlo Policy Gradient
    - Actor-Critic Methods
