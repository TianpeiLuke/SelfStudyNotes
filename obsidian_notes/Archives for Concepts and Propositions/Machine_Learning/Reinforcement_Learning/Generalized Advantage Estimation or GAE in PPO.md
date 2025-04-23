---
tags:
  - concept
  - machine_learning/algorithms
  - proximal_policy_gradient
  - ppo
  - reinforcement_learning/algorithm
  - deep_learning/large_language_models
keywords:
  - reinforcement_learning
  - proximal_gradient_algorithm
topics:
  - reinforcement_learning/algorithm
  - deep_learning/large_language_models
name: Generalized Advantage Estimation or GAE in PPO
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Generalized Advantage Estimation or GAE in PPO

![[Temporal Difference lambda Algorithm#^1134a1]]


>[!important] Definition
>Define the **TD residual**
> 
> $$\delta_t = r_t + \gamma V_\theta(s_{t+1}) - V_\theta(s_t),$$
> 
>then *smooth* it:
> 
> $$\hat A_t^{\text{GAE}(\gamma,\lambda)} =\sum_{l=0}^{T-t-1} (\gamma\lambda)^l\,\delta_{t+l}.$$
> 
> Returns for *value‑loss* are reconstructed as  
> $$R_t = \hat A_t + V_\theta(s_t).$$

- [[lambda-Return and Compound Update]]
- [[Temporal Difference Learning]]
- [[Temporal Difference lambda Algorithm]]



## Explanation

>[!quote]
>GAE says: “_Start with the fresh TD error $\delta_t$. Propagate the ‘surprise’ forward, but damp it by $\gamma\lambda$ each step so old information matters less._”  
>
> This delivers a **smooth yet informative** learning signal that lets PPO take larger, safer gradient steps—crucial for stable performance in both continuous‑control tasks (e.g., MuJoCo) and large‑scale RLHF/LLM fine‑tuning.


### Why PPO + GAE works well

| Component                                | Effect                                                                                                   |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Exponential tail** $(\gamma\lambda)^l$ | Blends information from multiple horizons; high‑variance Monte‑Carlo terms are down‑weighted.            |
| **Single extra hyper‑parameter λ**       | Provides a _knob_ to trade bias vs. variance without changing the underlying objective.                  |
| **Advantage normalisation**              | PPO often **centres and scales** $\hat A_t$ in each batch (zero mean, unit std) to stabilise updates.    |
| **Compatible with clipping**             | GAE delivers per‑timestep advantages that plug directly into PPO’s clipped ratio loss $L^{\text{CLIP}}$. |

### Backward Recursion implementation

```python
# pseudocode (PyTorch‑style)
advantages = torch.zeros_like(rewards)
last_adv = 0.0
for t in reversed(range(T)):
    nonterminal = 1.0 - dones[t]        # 0 if episode ended
    delta = rewards[t] + gamma * values[t+1] * nonterminal - values[t]
    last_adv = delta + gamma * lmbda * nonterminal * last_adv
    advantages[t] = last_adv
returns = advantages + values[:-1]      # target for value‑loss

```

## Compare with Eligibility Trace

>[!quote]
>GAE _uses the same exponential weighting idea_ that underlies eligibility traces, but in practice it is **not implemented with an online eligibility‑trace variable**. Instead, PPO (and other actor–critic methods) typically compute GAE _after_ a rollout by running one backward pass through the trajectory buffer. So the mechanism is conceptually similar, yet operationally different.

### Operational difference

| TD(λ) **eligibility‑trace loop**                                                                         | GAE **post‑rollout pass**                                                                                                                                       |
| -------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| While acting, keep an eligibility vector $e_t$​ *in memory* and *update* critic parameters *every step*. | Collect $T$ steps first; then run a _reverse_ loop to accumulate $\hat A_t$​ *without ever storing or updating* an eligibility variable during data collection. |
| Fully online, suitable for tabular or small function approximators.                                      | *Mini‑batch friendly*; matches PPO’s paradigm of _first gather, then optimise_ many epochs with SGD.                                                            |

- [[Eligibility Traces]]


### Line Up Conceptually

| Element                                   | Eligibility trace in TD(λ)                              | Exponential tail in GAE                                                      |
| ----------------------------------------- | ------------------------------------------------------- | ---------------------------------------------------------------------------- |
| **Recency weighting**                     | Factor $\lambda$ discounts older *signals*.             | The term $(\gamma\lambda)^l$ discounts older *TD residuals*.                 |
| Running “**trace**” expressed recursively | $$e_t = \gamma\lambda e_{t-1} + \nabla_\theta V(s_t).$$ | $$\hat A_t = \delta_t + \gamma\lambda\hat A_{t+1}.$$​ **computed backwards** |
| Goal                                      | Update **value** parameters online.                     | Produce a **batch advantage** for the policy (and returns for the critic).   |

>[!info]
>Mathematically, you can view GAE as applying a *$\lambda$‑weighted* eligibility trace to the _TD residuals_ $\delta_t$​. 
>- But the trace is collapsed into a single formula that you evaluate later, not maintained step‑by‑step during interaction.


## Compare with $\text{TD}(\lambda)$

| Aspect                                      | **TD(λ)**                                                                                                | **GAE(γ, λ)**                                                                                                                    |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **Primary goal**                            | Estimate / update the **value function** $V^{\pi}$.                                                      | Produce a **low‑variance advantage estimate** $\hat A_t$​ for _policy‑gradient_ methods.                                         |
| **Quantity mixed across nnn-step horizons** | $n$-step _value_ (or return) targets.                                                                    | nnn-step _temporal‑difference (TD) residuals_ $\delta_t$​.                                                                       |
| **Typical use‑case**                        | - Value‑based RL (TD(0), SARSA $\lambda$, eligibility traces), <br>- actor–critic for the _critic_ only. | - **Actor–critic** algorithms that need advantages (PPO, A3C, IMPALA, RLHF fine‑tuning of LLMs).                                 |
| **Computation**                             | Forward eligibility‑trace update or backward λ\lambdaλ-return formula.                                   | Single backward recursion that exponentially smooths TD errors.                                                                  |
| **Bias–variance knob**                      | - $\lambda \in [0,1]$ <br>- $\lambda = 0 \to$TD(0); <br>- $\lambda = 1\to$ Monte‑Carlo<br>               | Same λ range, but effect acts on advantage _residuals_ rather than raw returns—often yields lower variance for policy gradients. |
| **Output handed to optimiser**              | New target / gradient for $V_{\theta}$​.                                                                 | Advantage vector $\hat A_t$​ **and** returns $$R_t = \hat A_t + V_{\theta}(s_t).$$                                               |
| **Requires value baseline?**                | No—the algorithm _is_ the value estimator.                                                               | Yes—GAE subtracts the baseline $V_\theta(s_t)$ inside every $\delta_t$​.                                                         |
|                                             |                                                                                                          |                                                                                                                                  |
|                                             |                                                                                                          |                                                                                                                                  |

- [[Actor-Critic Algorithm]]
- [[Actor-Critic Algorithm with Eligibility Traces]]


### Key conceptual differences

> [!important]
>1. **What is being averaged?**
>     
>     - $\text{TD}(\lambda)$ blends **returns** of different horizons;
>         
>     - $GAE$ blends **TD errors (advantages)**, which are already baseline‑subtracted.  
>         - The latter generally has lower variance when fed into a policy‑gradient.
>         
> 1. **Where does the result go?**
>     
>     - $\text{TD}(\lambda)$  directly updates the **critic**; the actor sees only the new $V_\theta$.
>         
>     - $GAE$ provides the **actor’s gradient signal** _and_ a target for critic regression.
>         
> 1. **Baseline dependence.**
>     
>     - $\text{TD}(\lambda)$ can work with a tabular or function‑aprox baseline but does not rely on subtracting it explicitly.
>         
>     - $GAE$ _requires_ $V_\theta$ to compute $\delta_t$.
>         
> 1. **Compatibility with clipping / trust‑region tricks.**  
>     - GAE’s per‑timestep advantages slot cleanly into PPO’s clipped objective, whereas TD(λ) would need an extra subtraction step to create advantages.

- [[Temporal Difference lambda Algorithm]]



-----------
##  Recommended Notes and References


- [[Reinforcement Learning An Introduction by Sutton]]


- [[Proximal Policy Optimization or PPO Algorithm]]
- [[Preference Alignment for LLM]]
- [[Supervised Fine-Tuning or Instruction Fine-Tuning of LLM]]
- [[Supervised Fine-Tuning and Preference Alignment for LLM]]

- **“Proximal Policy Optimization Algorithms.”** J. Schulman et al., arXiv 1707.06347 (2017).
- **“Trust Region Policy Optimization.”** J. Schulman et al., ICML 2015.
