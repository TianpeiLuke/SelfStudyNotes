---
tags:
  - llm/training
  - reward
aliases: 
date of note: 2024-02-02
---

Direct Preference Optimization replaces the state-of-the-art Reinforcement Learning with Human Feedback

RLHF: 
- Supervised fine-tuning (SFT): 
- Reward modeling phase: to fit a reward model with human preference
- Apply RL to optimize the language model policy without drifting far from original model

RLHF too complex for ST, training multiple LLMs, sampling from LM policies, 

___Brdley-Terry (BT) Model ranking model__: 

$$ p(i \prec j) = \frac{\exp(r_i)}{\exp(r_i) + \exp(r_j)}$$

BT model can be generalized to multiple item ranking as the ___Plackett-luce ranking model___: 
$$
p(\pi) = \prod_{j=1}^{K}\frac{\exp(r_{\pi(j)})}{\sum_{t=1}^{K}\exp(r_{\pi(t)})}
$$ where $\pi = (\pi(1), \ldots, \pi(K)) \in \Pi$ is an arbitrary permutation ordering of $(1, \ldots, K)$


logistic \sigma

DPO directly optimzie the reward maximization with KL divg
DPO use theoretical preference ranking model such as BT ranking
DPO change of variables to define the preference loss as function of policy
DPO optimize the policy with binary cross entropy

RL objective optmization has close-form solution; max-entropy solution
re-arrange the solution as 

reward function = policy function ratio + extra term

extra term cancelled in ranking since we use (reward new - reward old)

=> DPO objective =  linear term + KL divergence



Reference:
1. Rafailov, R., Sharma, A., Mitchell, E., Ermon, S., Manning, C. D., & Finn, C. (2023). Direct preference optimization: Your language model is secretly a reward model. _arXiv preprint arXiv:2305.18290_.
