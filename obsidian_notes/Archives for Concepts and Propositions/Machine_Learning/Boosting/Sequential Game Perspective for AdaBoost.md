---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/boosting
keywords:
  - sequential_games
  - adaboost
  - game
topics:
  - boosting
name: Sequential Game Perspective for AdaBoost
date of note: 2024-07-29
---

## Concept Definition

>[!important]
>**Name**: Sequential Game Perspective for AdaBoost

### Setting for Two-Player Finite Game

>[!important] Definition
>Consider a **two-player normal-form finite game** 
>- a **row player**
>- a **column player**
>
>This game is represented by a matrix $$M = [M_{i,j}]$$
>where 
>- $M_{i,j}$ is the **loss** suffered by the *row player* if the *row player* chooses row $i$, and the *column player* chooses column $j$. 
>- the individual **row** and **column** are called **pure strategies**.
>- We assumed that each player can choose a **distribution** over the set of strategies. That is,
>	- The *row player* choose a **distribution** $P$ over the rows of $M$
>	- The *column player* choose a **distribution** $Q$ over the columns of $M$
>	- Both $P$ and $Q$ represents the **mixed strategy** 
>	- The **expected loss** is computed as $$M(P, Q) := \sum_{i,j}P(i)\,M_{i,j}\,Q(j) = P^{T}\,M\,Q$$
>	- In addition, if the *row* player choose a *distribution (mixed strategy)* and the *column* player choose a single column *(pure strategy)*, the *expected loss* is $$M(P, j) := \sum_{i}P(i)M_{i,j}= P^{T}M\,e_{j}$$ 
>	- Similarly, if the *column* player choose a *distribution (mixed strategy)* and the row player choose a single column *(pure strategy)*, the *expected loss* is $$M(i, Q) := \sum_{j}M_{i,j}Q(j) = e_{i}^T\,M\,Q$$
>  
>  


- [[Two-Player Finite Game and Matrix Representation]]
- [[Normal-Form Games]]
- [[Pure Strategies in Normal Form Game]]
- [[Mixed Strategy and Finite Strategy Sets]]
- [[Expected Payoff of Pure Strategy Against Mixed Strategy]]
- [[Sesquilinear Form]]

>[!important] Definition
>The goal of the game for two players are **complementary**:
>- The **row player** is to **minimize** the loss $$\min_{P}M(P, Q)$$
>- The **column player** is to **maximize** the loss $$\max_{Q}M(P, Q)$$
>- This game is a **zero-sum game**.

### Online Prediction as Repeated Game Play

- [[Online Learning Perspective for AdaBoost]]


### AdaBoost as Repeated Game Play

>[!important] Definition
>Consider the following definitions:
>- Define two players
>	- the **row player** is called the **(weak) learner**, who chooses a hypothesis $h\in \mathcal{H}$
>	- the **column player** is called the **booster**, who chooses a sample $x\in \mathcal{X}$
>- Assume the *finite hypothesis class* $|\mathcal{H}| < \infty$
>- Also assume that the *sample space* is *finite* $|\mathcal{X}| < \infty$
>- Let $M$ be the **error matrix** whose *rows* are indexed by the hypothesis $h\in \mathcal{H}$, and *columns* are indexed by the sample $x\in \mathcal{X}$. Thus $$M\in \{ 0 ,1 \}^{|\mathcal{H}| \times |\mathcal{X}|}: \quad M(h, x) = \mathbb{1}\{ h(x) \neq c(x) \}$$ where $c$ is the target class.
>- The **expected loss (payoff)** of *learner* choosing a hypothesis $h\in \mathcal{H}$ (i.e. a *pure strategy*) while the *booster* chooses a sample from a distribution $D$ (i.e. a *mixed strategy*) is defined as $$M(h, D) := \mathbb{E}_{D}\left[  \mathbb{1}\{ h(X) \neq c(X) \} \right]$$
>- The *goal* of **learner** is to choose a **pure strategy** $h$ to **minimize the expected loss** given that the **booster** choose a mixed strategy $D$ $$\min_{h}M(h, D)$$
>- The *goal* of **booster** is to choose a **mixed strategy** $D$ to **maximize the expected loss** given that the **learner** choose a pure strategy $h$ $$\max_{D}M(h, D)$$

- [[Finitely Repeated Games]]
- [[Characteristic Function of Set]]
- [[Generalization Error Bound for AdaBoost Finite Case]]
- [[AdaBoost Algorithm]]

>[!important] Definition
>The **AdaBoost Algorithm** can be formulated as a **repeated sequential two-player zero-sum game**. 
>
>In particular, 
>- For round $t= 1\,{,}\ldots{,}\,T$:
>	- the **booster** pass the *distribution* $D_{t}$ on $\mathcal{X}$ to *weak learner*
>	- the **weak learner** *choose* a hypothesis (i.e. a **pure strategy**) $h_{t}\in \mathcal{H}$ so that $$M(h_{t}, D_{t}) \le \frac{1}{2} - \gamma$$
>	- the **booster** 
>		- *observe* the **expected loss** $M(h_{t}, D_{t})$
>		- compute the **rate** $$\alpha_{t} = \frac{1}{2}\log \left( \frac{1 - M(h_{t}, D_{t}) }{M(h_{t}, D_{t}) } \right)$$
>		- *update* new distribution (**mixed strategy**) $D_{t+1}$ on $\mathcal{X}$ using the **exponential weighted average algorithm**. That is, for all $x\in \mathcal{X}$, $$D_{t+1}(x) = \frac{D_{t}(x)}{Z_{t}} \times \left\{\begin{array}{cc} e^{-\alpha_{t}}& \text{ if } M(h_{t}, x) = 0 \\ e^{\alpha_{t}}&\text{ if } M(h_{t}, x) = 1 \end{array}\right.$$ where $Z_{t}$ is the **partition function**
>- *Output*: 
>	- a **mixed strategy** $$\bar{P} = \sum_{t=1}^{T}\alpha_{t}\,h_{t}$$ over $\mathcal{H}$ based on a linear combination of previous pure strategies $\{ h_{t} \}$. 
>	- the *combined hypothesis* is  $$H = \text{sgn}(\bar{P}) := \text{sgn}\left(  \sum_{t=1}^{T}\alpha_{t}\,h_{t}\right).$$

- [[Weighted Majority Algorithm for Binary Loss]]
- [[Exponential Weighted Algorithm for Convex Loss]]
- [[Sequential Game of Perfect Information]]
- [[Partition Function for AdaBoost]]

## Explanation

>[!important]
>Let 
>- $$\bar{P} = \sum_{t=1}^{T}\alpha_{t}\,h_{t}$$
>- $$\bar{Q} = \sum_{t=1}^{T}D_{t}$$
>  
>Then 
>- $\bar{P}$ is an **approximate min-max strategy** $$\bar{P} \in \arg\min_{P\in \mathscr{P}_{\mathcal{H}}}\,\max_{x\in \mathcal{X}}M(P, x)$$  
>- $\bar{Q}$ is an  **approximate max-min strategy** $$\bar{Q} \in \arg\max_{Q} \min_{h\in \mathcal{H}}\,M(h, Q)$$  






-----------
##  Recommended Notes and References



- [[Mixed Strategy and Finite Strategy Sets]]
- [[Extensive-Form Game]]
- [[Sequential Game Play and Sequential Rationality]]
- [[Finitely Repeated Games]]


- [[AdaBoost Algorithm]]

- [[Exponential Weighted Algorithm for Convex Loss]]


- [[Foundations of Machine Learning by Mohri]] pp 137
- [[Boosting Foundations and Algorithms by Schapire]]  pp 157
- [[Game Theory An Introduction by Tadelis]]
- [[Prediction Learning and Games by Cesa-Bianchi]]