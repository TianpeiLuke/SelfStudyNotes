---
tags:
  - concept
  - math/stochastic_process
keywords:
  - time-homogeneous_markov_process
topics:
  - stochastic_process
name: Time-Homogeneous Markov Process
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Time-Homogeneous Markov Chain

>[!important] Definition
>A Markov process $(X_{t})$ is said to have **stationary transition probability function** $p$ if 
>$$
>p(s, x, t, A) = p(0, x, t-s, A).
>$$
>
>We say that the Markov process with stationary transition probability function is **time-homogeneous**, or **temporally homogeneous**.
>
>Let
>$$
>\mathcal{P}_{x} := \mathcal{P}_{x,0}, \quad  \mathbb{E}_{x}[\cdot] := \mathbb{E}\left[\cdot | X_{0} = x\right], \quad p(t, x, A) := p(0, x, t, A), \quad \mathscr{F}_{t} := \mathscr{F}_{t}^{0} 
>$$
>We shall denote the **time-homogeneous Markov process** by $(\Omega, \mathscr{F}, \mathscr{F}_{t}, X_{t}, \mathcal{P}_{x})$.

- [[Markov Transition Kernel and Transition Function]]
## Explanation

>[!important]
>For **time-homogeneous Markov process**, we can set $s=0$, i.e.
>$$
>\mathcal{P}_{x} := \mathcal{P}_{x,0}, \quad  \mathbb{E}_{x}[\cdot] := \mathbb{E}\left[\cdot | X_{0} = x\right], \quad p(t, x, A) := p(0, x, t, A), \quad \mathscr{F}_{t} := \mathscr{F}_{t}^{0} 
>$$
>
>$$
> \mathbb{E}_{x}\left[ f(X_{t}) \right]  := \mathbb{E}\left[f(X_{t}) | X_{0} = x\right] = \int_{\mathcal{X}}p(t, x, dy)f(y).
>$$
>
>The **weak Markov property** takes the form
>$$
> \mathbb{E}\left[ f(X_{t+h}) | \mathscr{F}_{t}^{0}\right] = \mathbb{E}\left[ f(X_{h}) | X_{0} = X_{t}\right], \quad \text{ a.s.}
>$$
>
>The **strong Markov property** takes the form
>$$
> \mathbb{E}\left[ f(X_{\tau + h}) | \mathscr{F}_{\tau}^{0}\right] = \mathbb{E}\left[ f(X_{h}) | X_{0} = X_{\tau}\right], \quad \text{ a.s.}
>$$
>where $\tau$ is stopping time.

- [[Markov Chain and Markov Process]]
- [[Strong Markov Property]]

## Semi-Group

>[!important] Definition
>The **semi-group** associated with time-homogeneous Markov process is given by
>$$
>\left( T_{t}\,f \right)(x) :=  \int_{\mathcal{X}}p(t, x, dy)f(y)
>$$

- [[Semigroup associated with Transition Function]]


## Infinitesimal Generator

>[!important] Definition
>Let $(X_{t})$ be a *time-homogeneous Markov Process*.
>
>The **(infinitesimal) generator** $\mathcal{A}$ of $X_{t}$ is a linear operator $\mathcal{A}: \mathcal{D}_{\mathcal{A}}(x) \to \mathcal{D}_{\mathcal{A}}(x)$ defined by 
>$$
>\begin{align*}
>\left( \mathcal{A}f \right) &:= \lim_{ t \to 0_{+} }   \frac{T_{t}\,f  - f}{t}.
>\end{align*}
>$$
>
>Denote $\mathcal{D}_{\mathcal{A}}$ be the space of all functions  $f: \mathbb{R}^n \to \mathbb{R}$ that *the limit exists for all* $x\in \mathbb{R}^n$.

^925c5c

- [[Infinitesimal Generator of Markov Process]]



-----------
##  Recommended Notes and References


- [[Time Homogeneous Diffusion and SDE]]
- [[Stationary Process]]
- [[Semigroup associated with Transition Function]]
- [[Infinitesimal Generator of Markov Process]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]]