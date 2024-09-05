---
tags:
  - concept
  - machine_learning/models
  - machine_learning/dynamic_system
  - probabilistic_graphical_models/sequential_models
  - statistics/signal_processing
keywords:
  - kalman_filter
topics:
  - machine_learning_models
  - machine_learning_theory
name: Kalman Filter Discrete-Time
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Kalman Filter Discrete-Time

![[Linear Dynamic System#^550f59]]


>[!important] Definition
>Assume *linear dynamic model* or *Gaussian state space model*
>- the *transition model* is defined by the *Gaussian distribution* $$\mathcal{P}(X_{t+1} | X_{t}, \,U_{t}) = \mathcal{N}(\,A(t) X_{t} + B(t) U_{t}\;;\;  \Sigma_{X}\,),$$
>- the *observation model* is defined by the *Gaussian distribution* $$\mathcal{P}(Y_{t} | X_{t},\, U_{t}) = \mathcal{N}(\,C(t) X_{t} + D(t) U_{t}\;;\;  \Sigma_{O}\,).$$
>
>The *discrete-time* **Kalman Filter** is an algorithm for posterior inference on *belief states* $$\mathcal{P}(X^{(t)}\,|\, O^{(1:t)},\, U^{(1: t)}) = \mathcal{N}(X^{(t)}\,|\, \mu_{t|t},\, \Sigma_{t|t})$$
>- $\mu_{t|s}$ is defined as the **posterior mean** of state given history observations $$\mu_{t|s} = \mathbb{E}\left[  X^{(t)}\;|\;O^{(1:s)},\, U^{(1: s)} \right]$$
>- $\Sigma_{t|s}$ is defined as the **posterior covariance** of state given history observations $$\Sigma_{t|s} = \mathbb{E}\left[  \left(X^{(t)} - \mu_{t|s}\right)\,\left(X^{(t)} - \mu_{t|s}\right)^{T}  \;|\;O^{(1:s)},\, U^{(1: s)} \right]$$

- [[Linear Dynamic System]]
- [[State-Observation Models]]

![[Bayesian Filtering and Smoothing Equations for State Observation Models#^1f4438]]


>[!important] Definition
>The *discrete-time* **Kalman filter** is described as the following:
>- *Require*: the *linear dynamic model* $$\left\{\begin{align*}X^{(t+1)} &= A(t)\,X^{(t)} + B(t)\,U^{(t)}  \\[5pt] O^{(t)} &= C(t)\,X^{(t)} + D(t)\,U^{(t)} \end{align*} \right.$$
>- *Require*: the *prior* for state and observation $$X^{(0)} \sim \mathcal{N}(0, \Sigma_{X}), \; O^{(0)} \sim \mathcal{N}(0, \Sigma_{O}).$$
>- For $t=1 \,{,}\ldots{,}\,T$:
>	- **Prediction Step**: compute the *conditional mean* and *conditional covariance* for $X^{(t)}$ given past *observations* $O^{(1: t-1)}$ and *inputs* $U^{(1:t)}$ $$\mathcal{P}(X^{(t)}\;|\;O^{(1: t-1)},\, U^{(1:t)}) := \mathcal{N}\left(X^{(t)}\;;\; \mu_{t|t-1},\, \Sigma_{t|t-1}\right)$$
>		- The **conditional mean** for *future states* is updated via $$\mu_{t|t-1} = A(t)\,\mu_{t-1|t-1} + B(t)\,U^{(t)}$$
>		- The **conditional covariance** for *future states* is updated via $$\Sigma_{t|t-1} = A(t)\,\Sigma_{t-1|t-1}\,A(t)^{T} + \Sigma_{X}$$
>	- **Update Step**: (also called the **measurement update step**) can be computed using *Bayes’ rule*, $$\mathcal{P}(X^{(t)}\,|\, O^{(1:t)},\, U^{(1: t)})  := \mathcal{N}(X^{(t)}\,|\, \mu_{t|t},\, \Sigma_{t|t})$$ The mean $\mu_{t|t}$ and covariance $\Sigma_{t|t}$ can be computed in the following steps
>		- The **conditional mean** of **predicted observation** at $t$ given state at $t$ and observations before $t$ $$\mu_{t:t-1}^{O} = C(t)\,\mu_{t|t-1} + D(t)\,U^{(t)}$$
>		- The **conditional covariance** of **predicted observation** at $t$ given state at $t$ and observations before $t$  $$\Sigma_{t:t-1}^{O} = C(t)\,\Sigma_{t|t-1}\,C(t)^{T} + \Sigma_{O}$$ 
>		- Compute the **Kalman gain matrix** $$K_{t} = \Sigma_{t|t-1}\,C(t)^{T}\,\left(\Sigma_{t:t-1}^{O}\right)^{-1}$$
>			- Note that *cross covariance matrix* between observation and state is denoted as $$\Sigma_{t}^{O,X}:= \Sigma_{t|t-1}\,C(t)^{T}$$
>			- In practice, we solve *a system of linear equations* $$(\Sigma_{t:t-1}^{O})^{T}\,K_{t}^{T}\, = (\Sigma_{t}^{O,X})^{T}$$
>		- Compute the *residual error*, called the **innovation term** $$e_{t} = O^{(t)} - \mu_{t:t-1}^{O}$$
>		- **Update** the **conditional mean** of current state given present and past observations $$\mu_{t|t} = \mu_{t|t-1} + K_{t}\,e_{t} = \mu_{t|t-1} + K_{t}\,\left(O^{(t)} - \mu_{t:t-1}^{O}\right)$$
>		- **Update** the **condition covariance** of current state given present and past observations $$\begin{align*}\Sigma_{t|t} &= \Sigma_{t|t-1} - K_{t}\,C(t)\,\Sigma_{t|t-1}  \\[5pt] &= \Sigma_{t|t-1} - K_{t}\,\Sigma_{t:t-1}^{O}\,K_{t}^{T}\end{align*}$$


- [[Bayesian Filtering and Smoothing Equations for State Observation Models]]
- [[Hidden Markov Model Inference via Forward-Backward Algorithm]]
- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]
- [[Gaussian Random Vector]]


## Explanation

>[!info]
>The **Kalman filter (KF)** is an algorithm for *exact Bayesian filtering* for *linear Gaussian state space models*.
>
>It is the Gaussian analog of the **Hidden Markov Model (HMM)**. 

>[!info]
>The posterior inference of Kalman filter follows the **dynamic programming algorithm**.


>[!info]
>To understand the update step intuitively, note that the **update** for the **latent mean**, $$\mu_{t|t} = \mu_{t|t-1} + K_{t} e_{t},$$ is the **predicted new latent mean** plus a **correction factor**, which is $K_{t}$ times the *error signal* $e_{t}$.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 360

>[!info]
>If $C(t) = I$, then $$K_{t} = \Sigma_{t|t-1}\,\left(\Sigma_{t:t-1}^{O}\right)^{-1};$$ in the scalar case, this becomes $$k_{t} = \frac{\Sigma_{t|t-1}}{\Sigma_{t:t-1}^{O}},$$ which is the **ratio** between the **variance of the prior** (from the dynamics model) and the **variance of the measurement**, which we can interpret as an **inverse signal to noise ratio (SNR)**.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 360

## Kalman Gain Matrix via Matrix Inversion

>[!important] 
>The **Kalman gain matrix** is defined as
>$$
>\begin{align*}
> K_{t} &= \Sigma_{t|t-1}\,C(t)^{T}\,\left(\Sigma_{t:t-1}^{O}\right)^{-1} \\[5pt]
> &= \Sigma_{t|t-1}\,C(t)^{T}\,\left[C(t)\,\Sigma_{t|t-1}\,C(t)^{T} + \Sigma_{O}\right]^{-1}
>\end{align*}
>$$
>
>Using the **matrix inversion formula**, we can reformulate the equation
>$$
>\begin{align*}
>K_{t} &= \Sigma_{t|t-1}\,C(t)^{T}\,\left[C(t)\,\Sigma_{t|t-1}\,C(t)^{T} + \Sigma_{O}\right]^{-1} \\[5pt]
>&= \left[\Sigma_{t|t-1}^{-1} +  C(t)^{T}\, \Sigma_{O}^{-1}\,C(t)\right]^{-1}C(t)^{T}\,\Sigma_{O}^{-1}
>\end{align*}
>$$
>
>We can maintain the inverse covariance matrix (**posterior precision**)
>- the update of *posterior precision* $$\Sigma_{t}^{-1} = \Sigma_{t|t-1}^{-1} +  C(t)^{T}\, \Sigma_{O}^{-1}\,C(t)$$
>- the update of *Kalman gain matrix* $$K_{t} = \Sigma_{t}\,C(t)^{T}\,\Sigma_{O}^{-1}$$

- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]


## Derivation

![[Marginal and Conditional Distribution of Gaussian#^70f047]]

- [[Marginal and Conditional Distribution of Gaussian]]
- [[Gaussian Random Vector]]
- [[Gaussian Graphical Model]]
- [[Gaussian Belief Propagation]]

>[!info]
>Consider the following **linear Gaussian system**
>$$
>\begin{align*}
> \mathcal{P}(X) &= \mathcal{N}(\mu_{X}; \Sigma_{X})\\[5pt]
> \mathcal{P}(O | X) &= \mathcal{N}(AX + b; \Sigma_{O|X})
>\end{align*}
>$$
>The **joint distribution** is 
>$$
>\mathcal{P}(X, O) = \mathcal{N}\left( \left[ \begin{array}{c} \mu_{X} \\[5pt] A\mu_{X} + b \end{array} \right]\;;\; \left[ \begin{array}{cc} \Sigma_{X} & \Sigma_{X}\,A^{T} \\[5pt] A\,\Sigma_{X} & A\,\Sigma_{X}\,A^{T} + \Sigma_{O|X} \end{array} \right]   \right)
>$$
>- Denote the *mean* of observation $\mu_{O} := A\mu_{X} + b$
>- Denote the *cross-covariance matrix* between *states* and *observations* $$\Sigma_{X,O} := \Sigma_{X}\,A^{T}$$
>- Denote the *covariance* for observation $$\Sigma_{O} = A\,\Sigma_{X}\,A^{T} + \Sigma_{O|X}$$
>
>The **posterior distribution** is
>$$
>\mathcal{P}(X | O) = \mathcal{N}\left( \mu_{X} + K\left(O - \mu_{O}\right)\;;\; \Sigma_{X} - K\, \Sigma_{O}\,K^{T} \right)
>$$
>where $$K := \Sigma_{X,O}\,\Sigma_{O}^{-1}$$

>[!info]
>The *joint distribution* of *states in two consecutive time* given all past observations is given by
>$$
>\begin{align*}
> &\mathcal{P}(X^{(t-1)},\,X^{(t)}\;|\; O^{(1: t-1)},\, U^{(1: t-1)} ) \\[5pt]
> &= \mathcal{P}\left(X^{(t)}\;|\; X^{(t-1)},\, U^{(t-1)}\right)\,\mathcal{P}\left(X^{(t-1)}\;|\; O^{(1: t-1)},\, U^{(1: t-1)}\right)  \\[5pt]
> &= \mathcal{N}\left(X^{(t)}\;|\; A\,X^{(t-1)} + B\,U^{(t-1)}\;;\; \Sigma_{X}  \right)\, \mathcal{N}\left(X^{(t-1)}\;|\; \mu_{t-1|t-1} ;\; \Sigma_{t-1|t-1}  \right) \\[5pt]
> &= \mathcal{N}\left( (X^{(t-1)}, X^{(t)})\;|\; \hat{\mu}; \hat{\Sigma} \right)
>\end{align*}
>$$
>where 
>$$
>\hat{\mu} = \left[ \begin{array}{c}\mu_{t-1|t-1} \\ A\,X^{(t-1)} + B\,U^{(t-1)} \end{array} \right], \quad \hat{\Sigma} = \left[\begin{array}{cc}\Sigma_{t-1|t-1} & \Sigma_{t-1|t-1}\,A^{T}\\ A\,\Sigma_{t-1|t-1} & A\,\Sigma_{t-1|t-1}\,A^{T} + \Sigma_{X} \end{array}  \right]  
>$$

>[!info]
>The *marginal predictive distribution* is given by
>$$
>\begin{align*}
>\mathcal{P}(X^{(t)}\;|\; O^{(1: t-1)},\, U^{(1: t-1)})&=  \mathcal{N}\left(X^{(t)}\;|\; A\,X^{(t-1)} + B\,U^{(t-1)}\,;\,  A\,\Sigma_{t-1|t-1}\,A^{T} + \Sigma_{X}  \right) \\
>&:= \mathcal{N}\left( X^{(t)}\;|\;  \mu_{t|t-1}\,;\, \Sigma_{t|t-1} \right)
>\end{align*}
>$$
>where
>$$
>\mu_{t|t-1} = A\,X^{(t-1)} + B\,U^{(t-1)}\;,\; \Sigma_{t|t-1} =  A\,\Sigma_{t-1|t-1}\,A^{T} + \Sigma_{X}.
>$$
>This is the result in **prediction step.**

>[!info]
>The *joint distribution* of *states* and *observations* at time $t$ is given by 
>$$
>\begin{align*}
> &\mathcal{P}(X^{(t)},\,O^{(t)} \;|\; O^{(1: t-1)},\, U^{(1: t)}) \\[5pt]
> &= \mathcal{P}\left(  O^{(t)} \;|\; X^{(t)},\, U^{(t)}\right)\,  \mathcal{P}\left(  X^{(t)} \;|\; O^{(1: t-1)},\, U^{(1: t-1)}\right) \\[5pt]
> &= \mathcal{N}\left( O^{(t)}\;|\; C\,X^{(t)} + D\,U^{(t)}\;;\; \Sigma_{O}  \right)\; \mathcal{N}\left(  X^{(t)} \;|\;  \mu_{t|t-1}\,;\, \Sigma_{t|t-1} \right)\\[5pt]
> &= \mathcal{N}\left( (X^{(t)},\,O^{(t)})\;|\; \bar{\mu}\;;\; \bar{\Sigma} \right) 
>\end{align*}
>$$
>where
>$$
>\bar{\mu} = \left[ \begin{array}{c}\mu_{t|t-1} \\ C\,X^{(t)} + D\,U^{(t)} \end{array} \right], \quad \bar{\Sigma} = \left[\begin{array}{cc}\Sigma_{t|t-1} & \Sigma_{t|t-1}\,C^{T}\\ C\,\Sigma_{t|t-1} & C\,\Sigma_{t|t-1}\,C^{T} + \Sigma_{O|X} \end{array}  \right]  
>$$
>and $$\mu_{t}^{O} :=  C\,X^{(t)} + D\,U^{(t)}\;, \; \Sigma_{t}^{O} := C\,\Sigma_{t|t-1}\,C^{T} + \Sigma_{O|X}.$$

>[!info]
>The *conditional distribution* of current state given past and present observations can be computed using the joint distribution above
>$$
>\begin{align*}
>\mathcal{P}\left( X^{(t)}\;|\; O^{(t)}, O^{(1: t-1)}, U^{(1: t)} \right) &:= \mathcal{N}\left(X^{(t)}\;|\; \mu_{t|t}\;;\;\Sigma_{t|t}  \right)
>\end{align*}
>$$
>where the conditional mean and conditional covariance are given by
>$$
>\begin{align*}
> \mu_{t|t} &= \mu_{t|t-1} + K\,\left( O^{(t)} - \mu_{t}^{O} \right) \\
> &= \mu_{t|t-1} + \Sigma_{t|t-1}\,C^{T}\left[ C\,\Sigma_{t|t-1}\,C^{T} + \Sigma_{O|X} \right]^{-1} \left( O^{(t)} -  C\,X^{(t)} - D\,U^{(t)} \right) \\[10pt]
> \Sigma_{t|t} &= \Sigma_{t|t-1} - K\,\Sigma_{O}\,K^{T}\\
> &= \Sigma_{t|t-1} - \Sigma_{t|t-1}\,C^{T}\left[ C\,\Sigma_{t|t-1}\,C^{T} + \Sigma_{O|X} \right]^{-1}\,C\,\Sigma_{t|t-1}
>\end{align*}
>$$
>which is the result in **update step**.
>
>Note that the **Kalman gain matrix** 
>$$
>\begin{align*}
>K &= \Sigma_{t|t-1}\,C^{T}\,\Sigma_{O}^{-1}\\[5pt] 
>&:= \Sigma_{t|t-1}\,C^{T}\,\left[ C\,\Sigma_{t|t-1}\,C^{T} + \Sigma_{O|X} \right]^{-1}
>\end{align*}
>$$


## Gaussian Graphical Model and Belief Propagation

>[!important]
>The Kalman filter derivation consists of three operations
>- **Joint distribution** or **Product operation**
>	- *joint* of $X^{(t)}$ and $X^{(t-1)}$ $$\mathcal{P}\left(X^{(t)}\;|\; X^{(t-1)},\, U^{(t-1)}\right)\,\mathcal{P}\left(X^{(t-1)}\;|\; O^{(1: t-1)},\, U^{(1: t-1)}\right)  \to \mathcal{P}(X^{(t-1)},\,X^{(t)}\;|\; O^{(1: t-1)},\, U^{(1: t-1)} )$$
>	- *joint* of $X^{(t)}$ and $O^{(t)}$ $$\mathcal{P}\left(  O^{(t)} \;|\; X^{(t)},\, U^{(t)}\right)\,  \mathcal{P}\left(  X^{(t)} \;|\; O^{(1: t-1)},\, U^{(1: t-1)}\right)  \to \mathcal{P}(X^{(t)},\,O^{(t)} \;|\; O^{(1: t-1)},\, U^{(1: t)})$$
>- **Marginalization** 
>	- *joint*  $(X^{(t)}, X^{(t-1)})$ to *marginal* $X^{(t)}$  $$\mathcal{P}(X^{(t-1)},\,X^{(t)}\;|\; O^{(1: t-1)},\, U^{(1: t-1)} )  \to \mathcal{P}(X^{(t)}\;|\; O^{(1: t-1)},\, U^{(1: t-1)})$$
>- **(Posterior) Conditioning** or **Reduction by evidence**
>	- *joint* $(X^{(t)}, O^{(t)})$ to conditional $(X^{(t)} | O^{(t)})$ $$\mathcal{P}(X^{(t)},\,O^{(t)} \;|\; O^{(1: t-1)},\, U^{(1: t)}) \to \mathcal{P}\left( X^{(t)}\;|\; O^{(t)}, O^{(1: t-1)}, U^{(1: t)} \right)$$
>	  
>In *Gaussian graphical model*, these are all standard operations of **canonical form**. Thus the Kalman filter can be seen as a special case of [[Gaussian Belief Propagation]].	  

- [[Canonical Form of Gaussian Graphical Model]]

## Kalman Filter based on Natural Parameters

![[Natural Parameter and Mean Parameter for Gaussian Distribution#^683466]]


>[!info]
>Instead of updating mean $\mu$ and covariance $\Sigma$, we can update the **natural parameters** of Gaussian $$\theta_{t|t} = \Sigma_{t|t}^{-1}\mu_{t|t}\;,\; \Theta_{t|t} = \Sigma_{t|t}^{-1}$$
>
>The corresponding technique is called the **information filter**.

- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]

>[!important] Definition
>The **Information Form Kalman Filtering** consists of two steps
>- **Prediction Step**: compute $$\mathcal{P}(X^{(t)}\;|\;O^{(1: t-1)},\, U^{(1:t)}) := \mathcal{N}\left(X^{(t)}\;;\; \theta_{t|t-1},\, \Theta_{t|t-1}\right)$$
>	- The **precision matrix** of $(X^{(t-1)}|X^{(t)})$  is given by $$M_{t} := \Theta_{t-1|t-1} + A(t)^{T}\Sigma_{X}^{-1}A(t)$$
>	- The **dual form** of **Kalman gain matrix** is $$J_{t} = \Sigma_{X}^{-1}A(t)\,M_{t}^{-1}$$
>	- The **precision (information) matrix** for predictive distribution is updated via the **marginalization** $$\begin{align*}\Theta_{t|t-1} &= \Sigma_{X}^{-1} - \Sigma_{X}^{-1}A(t)\,\left[  \Theta_{t-1|t-1} + A(t)^{T}\Sigma_{X}^{-1}A(t)\right]^{-1}\,A(t)^{T}\Sigma_{X}^{-1}\\[5pt] &= \Sigma_{X}^{-1} -  J_{t}A(t)^{T}\Sigma_{X}^{-1} \\[5pt] &= \Sigma_{X}^{-1} - J_{t}\,M_{t}\,J_{t}^{T}\end{align*}$$
>	- The first-order natural parameter for predictive distribution is updated via **marginalization**$$\theta_{t|t-1} = J_{t}\,\theta_{t-1 |t-1} + \Theta_{t|t-1}\left( B(t)U^{(t)} \right)$$
>- **Update Step** $$\mathcal{P}(X^{(t)}\,|\, O^{(1:t)},\, U^{(1: t)})  := \mathcal{N}(X^{(t)}\,|\, \theta_{t|t},\, \Theta_{t|t})$$
>	- The **information matrix** is updated via $$\Theta_{t|t} = \Theta_{t|t-1} + C(t)^{T}\,\Sigma_{O}^{-1}\,C(t)$$
>	- The first-order natural parameter is updated via $$\theta_{t|t} = \theta_{t|t-1} + C(t)^{T}\,\Sigma_{O}^{-1}\,\left( O^{(t)} - D(t)U^{(t)}\right)$$

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 366

>[!info]
>The *joint distribution* of *states in two consecutive time* given all past observations is given by
>$$
>\begin{align*}
> &\mathcal{P}(X^{(t-1)},\,X^{(t)}\;|\; O^{(1: t-1)},\, U^{(1: t-1)} ) \\[5pt]
> &= \mathcal{P}\left(X^{(t)}\;|\; X^{(t-1)},\, U^{(t-1)}\right)\,\mathcal{P}\left(X^{(t-1)}\;|\; O^{(1: t-1)},\, U^{(1: t-1)}\right)  \\[5pt]
> &= \mathcal{N}\left(X^{(t)}\;|\; \Sigma_{X}^{-1}\left( A\,X^{(t-1)} + B\,U^{(t-1)} \right)\;;\; \Sigma_{X}^{-1}  \right)\, \mathcal{N}\left(X^{(t-1)}\;|\; \theta_{t-1|t-1} ;\; \Theta_{t-1|t-1}  \right) \\[5pt]
> &= \mathcal{N}\left( (X^{(t-1)}, X^{(t)})\;|\; \theta_{t-1,t|t-1}\;;\; \Theta_{t-1,t|t-1} \right)
>\end{align*}
>$$
>where 
>$$
>\begin{align*}
>\theta_{t-1,t|t-1} &= \left[ \begin{array}{c}\theta_{t-1|t-1} - A(t)^{T}\,\Sigma_{X}^{-1}\left( B(t)U^{(t)} \right) \\ \Sigma_{X}^{-1}\left( B(t)U^{(t)} \right)  \end{array} \right] \\[5pt] 
>\Theta_{t-1,t|t-1} &= \left[\begin{array}{cc}\Theta_{t-1|t-1} + A(t)^{T}\,\Sigma_{X}^{-1}\,A(t) & -A(t)^{T}\,\Sigma_{X}^{-1}\\ -\Sigma_{X}^{-1}\,A(t) & \Sigma_{X}^{-1} \end{array}  \right]  
>\end{align*}
>$$
>We can derive the result $$\mathcal{P}\left(  X^{(t)} \;|\; O^{(1: t-1)},\, U^{(1: t-1)}\right) := \mathcal{N}\left(  X^{(t)} \;|\;  \theta_{t|t-1}\,;\, \Theta_{t|t-1} \right)$$ based on  **marginalization** formula.

- [[Canonical Form of Gaussian Graphical Model]]

>[!info]
>The *joint distribution*
>$$
>\begin{align*}
> &\mathcal{P}(X^{(t)},\,O^{(t)} \;|\; O^{(1: t-1)},\, U^{(1: t)}) \\[5pt]
> &= \mathcal{P}\left(  O^{(t)} \;|\; X^{(t)},\, U^{(t)}\right)\,  \mathcal{P}\left(  X^{(t)} \;|\; O^{(1: t-1)},\, U^{(1: t-1)}\right) \\[5pt]
> &= \mathcal{N}\left( O^{(t)}\;|\;\Sigma_{O}^{-1}\left(C\,X^{(t)} + D\,U^{(t)}\right) \;;\; \Sigma_{O}^{-1}  \right)\; \mathcal{N}\left(  X^{(t)} \;|\;  \theta_{t|t-1}\,;\, \Theta_{t|t-1} \right)\\[5pt]
> &= \mathcal{N}\left( (X^{(t)},\,O^{(t)})\;|\; \theta_{x,y|t}\;;\;\Theta_{x,y|t}\right) 
>\end{align*}
>$$
>where
>$$
>\begin{align*}
>\theta_{x,y|t} &= \left[ \begin{array}{c}\theta_{t|t-1} - C(t)^{T}\,\Sigma_{O}^{-1}\left( D(t)U^{(t)} \right) \\ \Sigma_{O}^{-1}\left( D(t)U^{(t)} \right)  \end{array} \right] \\[5pt] 
>\Theta_{x,y|t} &= \left[\begin{array}{cc}\Theta_{t|t-1} + C(t)^{T}\,\Sigma_{O}^{-1}\,C(t) & -C(t)^{T}\,\Sigma_{O}^{-1}\\ -\Sigma_{O}^{-1}\,C(t) & \Sigma_{O}^{-1} \end{array}  \right]  
>\end{align*}
>$$
>
>The conditional distribution
>$$
>\begin{align*}
>\mathcal{P}\left( X^{(t)}\;|\; O^{(t)}, O^{(1: t-1)}, U^{(1: t)} \right) &:= \mathcal{N}\left(X^{(t)}\;|\; \theta_{t|t}\;;\;\Theta_{t|t}  \right)
>\end{align*}
>$$
>where
>$$
>\theta_{t|t} = \theta_{t|t-1} + C(t)^{T}\,\Sigma_{O}^{-1}\left( O - D(t)U^{(t)} \right)
>$$
>and
>$$
>\Theta_{t|t}  = \Theta_{t|t-1} + C(t)^{T}\,\Sigma_{O}^{-1}\,C(t) 
>$$

- [[Marginal and Conditional Distribution of Gaussian]]



-----------
##  Recommended Notes and References


- [[Kalman Filter Continuous-Time]]
- [[Extended Kalman Filter]]
- [[Linear Dynamic System]]
- [[BFGS Algorithm]]


- [[Hidden Markov Model]]
- [[Sequential Importance Sampling]]

- [[Gaussian Graphical Model]]
- [[Brownian Motion Wiener Process]]
- [[Gaussian Process]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 359 - 364
- [[Probabilistic Graphical Models by Koller]] pp 211 - 212
- [[Deep Learning Foundations and Concepts by Bishop]] pp 515
- [[Artificial Intelligence Modern Approach by Russell]]