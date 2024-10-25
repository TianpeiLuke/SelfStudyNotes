---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/book
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
keywords:
  - reinforce_algorithm
topics:
  - reinforcement_learning/algorithm
name: REINFORCE Algorithm for Monte Carlo Policy Gradient
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: REINFORCE Algorithm for Monte Carlo Policy Gradient

![[Value Function and Bellman Equation for MDP#^e3c917]]

![[Value Function and Bellman Equation for MDP#^f9fda7]]

>[!important] Definition
>Let  $\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}\,,\, p_{t}(\cdot|x, a)\,,\, r_{t}(x, a)\}$ be a *Markov decision process* and $v_{\pi}(x)$ is the *state-value function* under policy $\pi_{\theta}$, which is parameterized by $\theta$.
>
>Define the **loss function** as $$J(\theta) := v_{\pi_{\theta}}(x_{0})$$ which is the the *true value* under $\pi_{\theta}$.
>- Note that the *state-value function* can be obtained via the *action-value function* $$v_{\pi_{\theta}}(x) = \sum_{a\in \mathcal{A}(x)}\,\pi(a\,|\,x, \theta)\,q_{\pi_{\theta}}(x, a) =  \mathbb{E}_{ A\sim \pi(\cdot|x, \theta) }\left[q_{\pi_{\theta}}(x, A)  \right]$$
>- The policy is given by an *exponential soft-max function* $$\pi(a\,|\,x, \theta) := \text{softmax}(h(x, a, \theta)) := \frac{\exp(h(x, a, \theta))}{\sum_{b\in \mathcal{A}(x)}\exp(h(x, b, \theta))}$$ where the *preference function* can be defined as a linear function of some *feature vectors* $$h(x, a, \theta) = \left\langle  \theta\,,\,f(x, a)    \right\rangle$$
>- The **REINFORCE** algorithm approximate the *gradient of expected value functions* $$\begin{align*}\nabla_{\theta}\, J(\theta) &:= \nabla_{\theta}\,\mathbb{E}_{ A\sim \pi(\cdot|x, \theta) }\left[q_{\pi_{\theta}}(x_{0}, A)  \right] \\[10pt] &=\mathbb{E}_{ A\sim \pi(\cdot|x, \theta) }\left[q_{\pi_{\theta}}(x_{0}, A)\;\nabla_{\theta}\,\log \pi(A\,|\,x_{0}, \theta) \right]\end{align*}$$
>  

- [[Value Function and Bellman Equation for MDP]]
- [[Markov Decision Process]]
- [[Policy Gradient Optimization]]
- [[Softmax Function and Log-Sum-Exp Function]]
- [[Linear Temporal Difference Learning]]

### REINFORCE as Monte Carlo Estimator of Gradient

>[!important] Definition
>The **REINFORCE** algorithm computes the *gradient of expected function* with respect to parameters 
>$$
>\begin{align*}
>\nabla_{\theta}\;\mathcal{L}(\theta) := \nabla_{\theta}\;\mathbb{E}_{ \theta }\left[  f(X) \right]
>\end{align*}
>$$  
>via *Monte Carlo method*. 
>
>In particular, 
>$$
>\begin{align*}
>\nabla_{\theta}\;\mathbb{E}_{ \theta }\left[  f(X) \right] &= \nabla_{\theta}\;\int f(x)\, p(x; \theta)\,dx \\[5pt]
>&= \int f(x)\, \nabla_{\theta}\,p(x; \theta)\,dx \\[5pt]
>&= \int f(x)\, \frac{1}{p(x; \theta)} \nabla_{\theta} p(x; \theta)\; p(x; \theta)dx \\[5pt]
>&= \int f(x)\, \nabla_{\theta}\,\log p(x; \theta)\;p(x; \theta)dx \\[5pt]
>&= \mathbb{E}_{ \theta }\left[\,f(X)\,\nabla_{\theta}\,\log p(X; \theta)\, \right]
>\end{align*}
>$$
>since $$\nabla_{\theta} \log p(x; \theta) = \frac{1}{p(x; \theta)} \nabla_{\theta} p(x; \theta) $$
>
>Thus the **REINFORCE** approximate the *gradient of expected function* via samples from $$X^{(s)} \sim p(x;\theta)$$ and the *gradient* is approximated as
>$$
>\begin{align*}
>\nabla_{\theta}\;\mathbb{E}_{ \theta }\left[  f(X) \right] &=  \mathbb{E}_{ \theta }\left[\,f(X)\,\nabla_{\theta}\,\log p(X; \theta)\, \right] \\[5pt]
>&\approx \frac{1}{N} \sum_{s=1}^{N}f(X^{(s)})\,\nabla_{\theta}\,\log p(X^{(s)}; \theta)
>\end{align*}
>$$

- [[Likelihood Function]]
- [[Log-Likelihood Score Function]]
- [[Cross-Entropy Loss Function]]
- [[Monte Carlo and Applications]]

## Explanation



## Other Gradient Computation Method

- [[Automatic Differentiation]]
- [[Back-Propagation Algorithm]]
- [[Back-Propagation Through Time]]




-----------
##  Recommended Notes and References


- [[REINFORCE Algorithm with Baseline]]
- [[Returns and Goals of Reinforcement Learning]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 326 - 329
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 265, 1137, 1148
