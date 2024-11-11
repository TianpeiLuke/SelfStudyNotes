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
>Define the **loss function** as $$J(\theta) := v_{\pi(\theta)}(x_{0}) \quad \text{or} \quad J(\theta) := \mathbb{E}_{ \pi }\left[  v_{\pi(\theta)}(X) \right]$$ which is the the *true value* under $\pi_{\theta}$.
>- Note that the *state-value function* can be obtained via the *action-value function* $$v_{\pi(\theta)}(x) = \sum_{a\in \mathcal{A}(x)}\,\pi(a\,|\,x, \theta)\,q_{\pi(\theta)}(x, a) =  \mathbb{E}_{ A\sim \pi(\cdot|x, \theta) }\left[q_{\pi(\theta)}(x, A)  \right]$$
>- $\mu$ is the *invariant distribution* of (*ergodic*) MDP, i.e. $$\mu(x) = \lim_{ t \to \infty } K^{t}(s, x), \quad \forall s$$
>- The policy is given by an *exponential soft-max function* $$\pi(a\,|\,x, \theta) := \text{softmax}(h(x, a, \theta)) := \frac{\exp(h(x, a, \theta))}{\sum_{b\in \mathcal{A}(x)}\exp(h(x, b, \theta))}$$ where the *preference function* can be defined as a linear function of some *feature vectors* $$h(x, a, \theta) = \left\langle  \theta\,,\,f(x, a)    \right\rangle$$
>
>The **REINFORCE** algorithm is based on the following equation for the *gradient of expected value functions* $$\begin{align*}\nabla_{\theta}\, J(\theta) &:= \nabla_{\theta}\,\mathbb{E}_{ X\sim \mu }\left[\mathbb{E}_{ A\sim \pi(\cdot|x, \theta) }\left[q_{\pi(\theta)}(X, A)  \right] \right]  \\[10pt] &=\mathbb{E}_{ X\sim \mu }\left[\mathbb{E}_{ A\sim \pi(\cdot|x, \theta) }\left[q_{\pi(\theta)}(X, A)\;\nabla_{\theta}\,\log \pi(A\,|\,X, \theta) \right] \right] \\[10pt] &= \mathbb{E}_{ \pi(\theta) }\left[ G\;\nabla_{\theta}\,\log \pi(A |\,X, \theta)  \right] \end{align*}$$
>- where the action-value function $q_{\pi(\theta)}$ is replaced by *expected returns* $$q_{\pi(\theta)}(X, A) = \mathbb{E}_{ \pi(\theta) }\left[  G\,|\,X, A \right]$$
>- The **REINFORCE** algorithm use the **Monte Carlo estimation** to approximate the gradient of objective. 

>[!important] Definition
>In particular, at iteration $t$, the **REINFORCE update** is given by
>$$
> \begin{align}
> \theta_{t+1} &\leftarrow \theta_{t} + \alpha \;G_{t}\nabla_{\theta}\,\log \pi(A_{t} |\,X_{t}, \theta), 
> \end{align}
>$$  
>where 
>- $G_{t}$ is the *sample returns* $$G_{t} := \sum_{\tau > t}\gamma^{\tau}R_{\tau}$$ under the policy $\pi$ following the sequence $$(X_{t}, A_{t}, R_{t+1}, X_{t+1}, A_{t+1}, \ldots)$$ in an episode.  
>
>**REINFORCE** is a **Monte Carlo policy gradient method**, since the algorithm will *not update the policy* until the *end of each episode*, in order to obtain the sample return $G_{t}$. 


^25c7fb

- [[Value Function and Bellman Equation for MDP]]
- [[Returns and Goals of Reinforcement Learning]]
- [[Markov Decision Process]]
- [[Policy Gradient Algorithm]]
- [[Softmax Function and Log-Sum-Exp Function]]
- [[Linear Temporal Difference Learning]]
- [[Ergodic Markov Chain and Asymptotic of Transition Kernel]]

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

### All-Action Method

>[!important] Definition
> Based on *policy gradient theorem*, we can compute the **gradient of objective** exactly using 
> - the *value function* $q_{\pi}$, 
> - the *on-policy distribution* $\mu$ and 
> - the *gradient of policy function* $\nabla_{\theta}\,\log \pi(a\,|\,x, \theta)$. 
> 
>In practice, we can **sample the state sequence** $X_{t}$ under the policy $\pi$. 
>- In expectation, samples of $X_{t}$ replace the *steady state distribution* $\mu$ since when MDP is *stationary*, the distribution of state does not change over time.
>
>Thus we have 
>$$
> \begin{align*}
> \nabla_{\theta}\mathcal{R}(\theta) &=  \sum_{s}\mu_{\pi}(x)\,\sum_{a}\,\nabla_{\theta}\pi(a\,|\,x,\, \theta)\;q_{\pi}(x, a) \\[5pt]
> &= \mathbb{E}_{ X_{t}\sim \mu_{\pi} }\left[  \sum_{a} \nabla_{\theta}\pi(a\,|\,X_{t},\, \theta)\;q_{\pi}(X_{t}, a)  \right] 
> \end{align*}
>$$  
>
>And we can develop the *stochastic gradient ascent algorithm* as 
>$$
> \begin{align}
> \theta_{t+1} &\leftarrow \theta_{t} + \alpha\,\sum_{a \in \mathcal{A}(X_{t})} \nabla_{\theta}\pi(a\,|\,X_{t},\, \theta)\;\hat{q}(X_{t}, a)
> \end{align}
>$$  
>where we replace $q_{\pi}$ by its estimate $\hat{q}$. 
>- This algorithm is called **all-actions method**, because its update involves *all of the actions*, is promising and deserving of further study.

### REINFORCE Algorithm 

>[!info] 
> The all-actions method need to scan the *entire action space*, which is not efficient. 
> 
>We consider replace the expectation with the *sample action* $A_{t}$ from *policy* $\pi$.
>$$
> \begin{align*}
> \nabla_{\theta}\mathcal{R}(\theta)  &= \mathbb{E}_{ \pi }\left[   \sum_{a} \nabla_{\theta}\pi(a\,|\,X_{t},\, \theta)\;q_{\pi}(X_{t}, a) \right]\\[5pt]
> &= \mathbb{E}_{ \pi }\left[\sum_{a}\pi(a\,|\,X_{t},\, \theta)\frac{\nabla_{\theta} \pi(a\,|\,X_{t},\, \theta)}{\pi(a\,|\,X_{t},\, \theta)}q_{\pi}(X_{t}, a) \right] \\[5pt]
> &= \mathbb{E}_{ \pi }\left[q_{\pi}(S_{t}, A_{t}) \frac{\nabla_{\theta} \pi(A_{t}\,|\,X_{t},\, \theta)}{\pi(A_{t}\,|\,X_{t},\, \theta)} \right] \\[5pt]
> &= \mathbb{E}_{ \pi }\left[G_{t}\frac{\nabla_{\theta} \pi(A_{t}\,|\,X_{t},\, \theta)}{\pi(A_{t}\,|\,X_{t},\, \theta)}  \right] \\[8pt]
> &= \mathbb{E}_{ \pi }\left[G_{t} \nabla_{\theta}\log\pi(A_{t}|X_{t}, \theta) \right]
> \end{align*}
>$$  
>where
>- the second last equation holds by replacing the *action-value function* by the *sample returns*  since  $$q_{\pi}(s, a)= \mathbb{E}_{ \pi }\left[  G_{t} \,|\, X_{t}=s, A_{t}=a \right].$$ 
>- The last equation holds by chain rule $$\nabla_{\theta}\log\pi(A_{t}|X_{t}, \theta) = \frac{\nabla_{\theta} \pi(A_{t}\,|\,X_{t},\, \theta)}{\pi(A_{t}\,|\,X_{t},\, \theta)}.$$ 
>- In computation, the $\nabla_{\theta}\log\pi(A_{t}|X_{t}, \theta)$ is **numerically more stable** to compute vs. the directly ratio.

>[!important] Definition
>The **REINFORCE algorithm** for *episodic task*  is described as follows:
>- *Require*: parameterized policy function $\pi(a|x, \theta)$
>- *Require*: step size $\alpha >0$
>- *Require*: reward discount factor $\gamma\in (0,1)$
>- Initialize $\theta^{(0)}$
>- For **episode** $k=1\,{,}\ldots{,}\,$
>	- Generate an **entire episode** following **policy** $\pi(\cdot|\cdot, \theta)$ i.e. $$\left(X_{0}, A_{0}, R_{1}, X_{1}\,{,}\ldots{,}\,X_{T-1}, A_{T-1}, R_{T}\right)$$
>	- For $t=0\,{,}\ldots{,}\,T-1$
>		- Accumulate **expected sample returns** via **Monte Carlo estimator** $$G_{t} = \sum_{s=t+1}^{T}\gamma^{s-t-1}\,R_{s}$$
>		- Update the **policy parameter** via *Monte Carlo estimator* 
>		  $$\theta \leftarrow \theta + \alpha\,\gamma^{t}\,G_{t}\,\nabla \log \pi(A_{t}\,|\,X_{t};\; \theta)$$

- [[Episodic and Continuing Task in Reinforcement Learning]]


## Explanation

>[!important]
>- Like many Monte Carlo methods, REINFORCE is **unbiased** but have **high variance** and **slow learning**. 
>- As a stochastic gradient method, REINFORCE has **good theoretical convergence** properties. 
>	- By construction, the expected update over an episode is in the *same direction* as the *performance gradient*. 
>	- This **assures an improvement** in *expected performance* for sufficiently small $\alpha$, and convergence to a **local optimum** under standard stochastic approximation conditions for decreasing $\alpha$.  


|                              | **Value-based Policy** $$\pi(x) = \arg\max_{a} q(x, a)$$                                                                                                                                                         | **Parameterized Policy** $$\pi(a ; x,  \theta)$$                                                     |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Sample Return**            | - [[Monte Carlo Control with Exploring Starts]]<br>- [[Monte Carlo Prediction for Value Estimation]]                                                                                                             | - [[REINFORCE Algorithm for Monte Carlo Policy Gradient]]<br>- [[REINFORCE Algorithm with Baseline]] |
| **Bootstrapping / TD Rrror** | - [[Temporal Difference Learning]]<br>- [[SARSA Algorithm and On-Policy Temporal Difference Control]]<br>- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]<br>- [[Expected SARSA Algorithm]] | - [[Actor-Critic Algorithm]]                                                                         |

>[!important]
>The REINFORCE update has some **appealing properties**: 
>- Each **increment** is *proportional* to the *product* of a return $G_t$ and a vector, the **gradient** of the **log-probability** of taking the sample action. $$\Delta \theta \propto G_{t}\;\nabla \log \pi(A_{t}\,|\,X_{t}; \theta)$$
>	- This vector is the direction in parameter space that *most increases* the **probability** of **repeating the action** $A_t$ on **future visits** to state $X_t$. 
>- The update increases the parameter vector in this direction **proportional to the return**, and **inversely proportional** to the **action probability**. $$\Delta \theta \propto R_{t}\; \quad \Delta \theta \propto \frac{1}{\pi(A_{t}\,|\,X_{t}; \theta)}$$ 
>	- The former $$\Delta \theta \propto R_{t}$$  makes sense because it causes the parameter to *move most* in the *directions* that **favor** *actions* that yield the **highest return**. (**Exploitation**)
>	- The latter $$\Delta \theta \propto \frac{1}{\pi(A_{t}\,|\,X_{t}; \theta)}$$  makes sense because *otherwise* actions that are **selected frequently** are **at an advantage** (the updates will be more often in their direction) and might win out even if they do not yield the highest return. (**Exploration**)

^2e06da

- [[Exploration and Exploitation Tradeoff]]




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
