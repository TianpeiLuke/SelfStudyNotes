---
tags:
  - concept
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
keywords:
  - policy_function_approximation
topics:
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
name: Policy Parameterization and Policy Function Approximation
date of note: 2024-11-10
---

## Concept Definition

>[!important]
>**Name**: Policy Parameterization and Policy Function Approximation

![[Markov Decision Process#^a1e9de]]

![[Markov Decision Process#^63a761]]

![[Markov Decision Process#^1d9419]]

![[Markov Decision Process#^56b9a5]]

![[Markov Decision Process#^67062c]]

### Discrete Action Space

>[!important] Definition
> When $\mathcal{A}$ is **finite discrete**, and $s \in \mathcal{S}$, we can ues the **soft-max function** to *approximate the policy distribution*
>$$ 
> \begin{align}
> \pi(a \,|\,s, \theta) &= \frac{\exp \left(h(s, a, \theta)\right)}{\sum_{a'}\exp\left(h(s, a', \theta)\right)} \\[8pt]
> \end{align}
>$$  
>- It assumes that the random action is selected based on **multinomial distribution** $$A \sim \text{multinomial}\left(\exp(h,a,\theta),\, a\in \mathcal{A}\right)$$
>- The function $h(s, a, \theta)$ defines the **preferences** of some *actions*. 
>- This kind of *policy parameterization* is called  **soft-max in action preferences**. 
>  
>The **gradient** of *softmax policy function*  is given by
>$$ 
> \begin{align}
>\log \pi(a \,|\,s, \theta) &= h(s, a, \theta) -  \log \sum_{a'}\exp\left(h(s, a', \theta)\right) \\[8pt]
> \nabla_{\theta} \log \pi(a \,|\,s, \theta)&= \nabla_{\theta}h(s, a, \theta) - \mathbb{E}_{ A \sim \pi(a\,|\,s,\, \theta) }\left[ \nabla_{\theta} h(s, A, \theta) \right]  \\[8pt]
> &= \nabla_{\theta}h(s, a, \theta) - \sum_{a'}\pi(a'\,|\,s,\, \theta)\,\nabla_{\theta}h(s, a', \theta) \nonumber\\[8pt]
> &= \text{sample }\nabla_{\theta}h(s, a, \theta)\text{ with action} -  \text{policy action mean of }\nabla_{\theta}h(s, A, \theta) \nonumber
> \end{align}
>$$  
>

^5693ea

- [[Exponential Family of Distributions]]
- [[Log-Likelihood Score Function]]
- [[Multinomial Distribution]]
- [[Softmax Function and Log-Sum-Exp Function]]
- [[Markov Decision Process]]


>[!info]
>We can define the preference as **linear functions** with respect to some features:
>$$
> \begin{align*}
> h(s, a, \theta) &:=  \left\langle  \theta\,,\,\Phi(s, a) \right\rangle  \\[5pt]
> \nabla_{\theta}\,h(s, a, \theta)  &= \Phi(s,a)
> \end{align*}
>$$  
>where 
>- $\Phi(s, a):= [\phi_{k}(s, a)]$ can be any *feature representation* we discussed in lecture 8, for instance, **tile coding** on state on fixed action and stacked multiple actions. 
>
>Combining with *softmax gradient formula* above, we can see that the gradient of log of $\pi$ can be easily represented as the **difference** between the **sample (mean)** of *state-action feature* for specific action $\phi(s, a)$ and the **policy mean** of *state-action feature* over all actions 
>
>$$\Phi(s, a) - \mathbb{E}_{ A\sim \pi(\cdot|s, \theta) }\left[ \Phi(s, A) \right].$$

- [[Linear Temporal Difference Learning]]
- [[Generalized Linear Models]]

### Continuous Action Space

> [!important] Definition
> When $\mathcal{A} \subset \mathbb{R}$ is **continuous space**,  and $s \in \mathcal{S}$,  we use the **Gaussian distribution** to *approximate the policy*
> $$
> \begin{align}
> \pi(a \,|\,s, \theta) &= \frac{1}{\sqrt{2\pi}\sigma(s, \theta_{\sigma})}\;\exp \left(- \frac{\left(a - \mu(s, \theta_{\mu})\right)^2}{2\sigma^2(s, \theta_{\sigma})} \right)
> \end{align}
>$$ 
> where $\theta = [\theta_{\mu}, \theta_{\sigma}]$, and 
>$$ 
> \begin{align*}
> h(s, a,\theta) &= -\frac{(a - \mu(s, \theta_{\mu}))^2}{2\sigma^2(s, \theta_{\sigma})}\\[5pt]
> \mu(s, \theta_{\mu}) &= \left\langle  \theta_{\mu}\,,\, \phi_{\mu}(s)   \right\rangle \\[5pt]
> \sigma(s, \theta_{\sigma}) &= \exp(\left\langle  \theta_{\sigma}\,,\, \phi_{\sigma}(s)   \right\rangle)
> \end{align*}
>$$ 
>- $\phi_{\mu}$ and $\phi_{\sigma}$ are the feature maps. 
>- It assumes that the random action is selected based on **Gaussian distribution** $$A \sim \mathcal{N}(a\;|\; \mu(s, \theta_{\mu}),\; \sigma^2(s, \theta_{\sigma}))$$
>
>The **gradient** of the *Gaussian policy function* is given by 
>$$
> \begin{align}
> \log \pi(a \,|\,s, \theta)  &= -\frac{(a - \mu(s, \theta_{\mu}) )^2}{2\sigma^2(s, \theta_{\sigma})} - \log \sigma(s, \theta_{\sigma}) + \frac{1}{2}\log{2\pi} \\[8pt]
> \nabla_{\theta} \log \pi(a \,|\,s, \theta) &= \nabla_{\theta}\,h(s, a,\theta) - \mathbb{E}_{ A\sim \pi(a\,|\,s, \theta) }\left[  \nabla_{\theta}\,h(s, A,\theta) \right]  \\[8pt]
> &= \text{sample of }\nabla_{\theta}\,h(s, a,\theta) -  \text{policy action mean of }\nabla_{\theta}\,h(s, A,\theta) \nonumber
> \end{align}
>$$ 

^ba05ca

- [[Gaussian Random Vector]]
- [[Exponential Family of Distributions]]
- [[Log-Likelihood Score Function]]
- [[Markov Decision Process]]

>[!info]
> Note that
> $$
> \begin{align*}
> \nabla_{\theta_{\mu}}\log \pi(a \,|\,s, \theta)  &= \frac{1}{\sigma^2(s, \theta_{\sigma})}\left(a - \mu(s, \theta_{\mu})\right) \nabla_{\theta_{\mu}}\mu(s, \theta_{\mu}) \\[5pt]
> &= \frac{1}{\sigma^2(s, \theta_{\sigma})}\left(a - \mu(s, \theta_{\mu})\right)\; \phi_{\mu}(s) \\[5pt]
> \nabla_{\theta_{\sigma}}\log \pi(a \,|\,s, \theta)  &=(a - \mu(s, \theta_{\mu}))^2 \frac{1}{\sigma^3(s, \theta_{\sigma})}\,\nabla_{\theta_{\sigma}}\sigma(s, \theta_{\sigma})  - \frac{1}{\sigma(s, \theta_{\sigma})}\,\nabla_{\theta_{\sigma}}\sigma(s, \theta_{\sigma})  \\[5pt]
> &= \left(\frac{(a - \mu(s, \theta_{\mu}))^2- \sigma^2(s, \theta_{\sigma})}{\sigma^3(s, \theta_{\sigma})}\right)\;\nabla_{\theta_{\sigma}}\sigma(s, \theta_{\sigma})  \\[5pt]
> &=  \left(\frac{(a - \mu(s, \theta_{\mu}))^2- \sigma^2(s, \theta_{\sigma})}{\sigma^3(s, \theta_{\sigma})}\right)\;\sigma(s, \theta_{\sigma})\;\phi_{\sigma}(s) \\[5pt]
> &= \left(\frac{(a - \mu(s, \theta_{\mu}))^2}{\sigma^2(s, \theta_{\sigma})} - 1\right)\; \phi_{\sigma}(s) 
> \end{align*}
>$$ 





## Explanation

>[!info]
>- One  **advantage** of *parameterizing policies* according to the **soft-max in action preferences** is that the *approximate policy* can approach a *deterministic policy*, 
>	- whereas with **$\epsilon$-greedy action selection** over action values there is always an $\epsilon$ probability of selecting a *random action*. 
>	- Of course, one could *select* according to a **soft-max distribution** based on action values, but this alone would not allow the policy to approach a **deterministic policy**. 
>	- Instead, the *action-value estimates* would converge to their corresponding *true values*, which would *differ by a finite amount*, translating to specific probabilities other than $0$ and $1$. 
>	- **Action preferences** are different because they do not approach specific values; instead they are driven to produce the \emph{\textbf{optimal stochastic policy}}. If the optimal policy is \emph{\textbf{deterministic}}, then the preferences of the optimal actions will be driven infinitely higher than all suboptimal actions (if permitted by the parameterization).
>
>- A **second advantage** of parameterizing policies according to the **soft-max in action preferences** is that 
>	- it enables the selection of actions with *arbitrary probabilities*. 
>		- In problems with significant function approximation, the **best approximate policy** may be **stochastic**. 
>		- For example, in card games with imperfect information the optimal play is often to do two different things with specific probabilities, such as when bluffng in Poker. 
>	- **Action-value methods** have *no natural way* of finding **stochastic optimal policies**, whereas policy approximating methods can. 

- [[epsilon-Greedy Algorithm]]
- [[Value Function and Bellman Equation for MDP]]
- [[Policy Iteration Algorithm]]




-----------
##  Recommended Notes and References




- [[Tabular Representation and Function Approximation RL]]
- [[Reinforcement Learning]]

- [[Reinforcement Learning An Introduction by Sutton]]