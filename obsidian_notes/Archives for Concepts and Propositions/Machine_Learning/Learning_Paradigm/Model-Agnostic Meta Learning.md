---
tags:
  - concept
  - machine_learning/strategy
  - meta_learning
  - model_agnostic_meta_learning
  - maml
keywords:
  - meta_learning
  - model_agnostic_meta_learning
  - maml
topics:
  - machine_learning_strategy
name: Model-Agnostic Meta Learning
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Model-Agnostic Meta Learning

>[!important] Definition
>**Model‑Agnostic Meta‑Learning (MAML)** is a **gradient‑based meta‑learning framework** whose goal is to find a single set of model parameters that can be _rapidly_ adapted to many different tasks with only a few gradient steps and a small amount of data. 
>- It is called _model‑agnostic_ because it places only one requirement on the base model: its *loss must be differentiable* with respect to its parameters. 
>- Architecture, activation functions, output type, and even learning domain (supervised, reinforcement learning, etc.) are otherwise unconstrained.

- [[Meta Learning]]
- [[Transfer Learning]]
- [[Domain Adaptation]]
- [[Continual Learning]]


### Algorithm

>[!info]
> - **Inner loop** (task‑level): learn quickly _within_ the task – small data, high plasticity.
>     
> - **Outer loop** (meta‑level): learn slowly _across_ tasks – extracts transferable structure.


>[!important] Algorithm
>Let a *distribution of tasks* be denoted by $p(\mathcal{T})$. 
>- A task $\mathcal{T}\sim p(\mathcal{T})$ provides two data sets:
>	-  **support (adaptation) set**:  $$D^{\text{sup}}_{\mathcal{T}}=\bigl\{(x^{\text{sup}}_j,y^{\text{sup}}_j)\bigr\}_{j=1}^{N_s}$$
>	- **query (validation) set**: $$D^{\text{qry}}_{\mathcal{T}}=\bigl\{(x^{\text{qry}}_k,y^{\text{qry}}_k)\bigr\}_{k=1}^{N_q}$$
>- Define **meta-parameters** $\theta$ corresponding to a model $f_\theta$ that are *shared* across tasks
>
>The **Model-Agnostic Meta Learning (MAML)** algorithm can be described as following:
>- *Require*: 
>	- *task distribution* $p(\mathcal{T})$, 
>	- task-level learning rate $\alpha$, 
>	- meta-level learning rate $\beta$
>	- *meta-parameter* $\theta$ that shared across tasks
>- Initialization
>	- State Initialise meta‑parameters $\theta$
>- While not converged (**meta-training loop**)
>	- **Sample** a mini-batch $$\{\mathcal{T}_i\}_{i=1}^B \sim p(\mathcal{T})$$
>	- For each task $\mathcal{T}_{i}$ in the mini-batch 
>		- **Inner-Loop Adaption** The learner performs $K$ *gradient steps* on the support set $\theta$ as 
>			- $$\theta^{(0)}_{\mathcal{T}_{i}} = \theta$$
>			- For $k=0,\dots,K-1$, $$\theta^{(k+1)}_{\mathcal{T}_{i}} =  \theta^{(k)}_{\mathcal{T}_{i}} -\;\alpha\,\nabla_{\theta}\mathcal{L}\bigl(f_{\theta^{(k)}_{\mathcal{T}_{i}}}, D^{\text{sup}}_{\mathcal{T}_{i}}\bigr)$$
>			- $\alpha$ is the *(task‑level) learning rate*.
>			- After $K$ steps we obtain the *task‑adapted parameters* $$\theta'_{\mathcal{T}_{i}}=\theta^{(K)}_{\mathcal{T}_{i}}.$$
>		- Compute **query loss** $$\mathcal{L}_i^{\text{qry}} = \mathcal{L}\bigl(f_{\theta'_{\mathcal{T}_{i}}}, D^{\text{qry}}_{\mathcal{T}_i}\bigr)$$
>	- **Meta Update**:
>		- The **meta‑objective** aggregates query losses of the adapted models: $$\mathcal{L}_{\text{meta}}(\theta)= \mathbb{E}_{\mathcal{T}\sim p(\mathcal{T})}\Bigl[\mathcal{L}\bigl(f_{\theta'_{\mathcal{T}}}, D^{\text{qry}}_{\mathcal{T}}\bigr)\Bigr].$$
>		- Update the meta-parameters via gradient step $$\theta \leftarrow \theta - \beta\,\nabla_{\theta}\, \mathcal{L}_{\text{meta}}(\theta) = \theta - \beta \nabla_{\theta}\,\left(\frac{1}{B}\sum_{i=1}^{B}\mathcal{L}_i^{\text{qry}}\right).$$
>- *Output*
>	- the meta parameters $\theta$
>- **Meta-Testing**
>	- Given an unseen task $\mathcal{T}_{\text{new}}$,  adapt with $K$ inner steps on its support set and evaluate on its query set:
>		- $$\theta'_{\text{new}} = \theta - \alpha\,\nabla_{\theta} \mathcal{L}\bigl(f_{\theta}, D^{\text{sup}}_{\text{new}}\bigr),$$
>	- The inference result given by $$\hat{y}=f_{\theta'_{\text{new}}}(x_{\text{new}}).$$

^f8b278

- [[Gradient Descent Algorithm]]


### Meta Objective

>[!info]
>Note that since each task-specific parameter is updated from the meta-parameters, we can view the *inner adaptation* step as a *deterministic function* that maps the *meta parameters* $\theta$ to *task-specific parameters* $\theta_{i}$
>$$
>\text{Adapt}_{\alpha, K}(\cdot\,;\, D_{\mathcal{T}_{i}}^{\text{sup}}):\; \theta \to \theta_{i}(\theta)
>$$
>so the meta-objective function is given by
>$$
>\mathcal{J}(\theta) := \frac{1}{B}\sum_{i=1}^{B}\mathcal{L}_i^{\text{qry}} = \frac{1}{B}\sum_{i=1}^{B}\mathcal{L}\bigl(\theta_{i}(\theta), D^{\text{qry}}_{\mathcal{T}_i}\bigr)
>$$
>where for $K=1$, the $\theta_{i}(\theta)$ is given by
>$$\theta_{i}(\theta) =  \theta -\;\alpha\,\nabla_{\theta}\mathcal{L}\bigl(\theta, D^{\text{sup}}_{\mathcal{T}_{i}}\bigr)$$

>[!important]
>The *objective* of **MAML** can be formulated as 
>$$
>\theta^{*} = \arg\min_{\theta}\;\mathbb{E}_{ \mathcal{T}\sim p(\mathcal{T}) }\left[  \mathcal{L}_{\mathcal{T}}\left(U_{k}(\theta\,;\,\mathcal{T})\right) \right]
>$$
>where
>- $p(\mathcal{T})$ is a distribution over tasks
>- $\mathcal{L}_{\mathcal{T}}$ is the task-specific loss for parameters $\theta$
>- $U_{k}(\theta; \mathcal{T})$ is the $k$-step gradient descent on $\mathcal{L}_{\mathcal{T}}$


### Computation of Hyper-Gradient

>[!important]
>Define
>- *task-specific gradient (w.r.t. meta-parameter)* $$g_i = \nabla_{\theta}\mathcal{L}_{\mathcal T_i}\!\bigl(\theta;D^{\text{sup}}_{\mathcal T_i}\bigr),$$
>- and *task-specific Hessian (w.r.t. meta-parameter)* $$H_i = \nabla^{2}_{\!\theta}\mathcal{L}_{\mathcal T_i}\!\bigl(\theta;D^{\text{sup}}_{\mathcal T_i}\bigr).$$
>
>For the single‑step inner loop 
>$$\begin{align*}
>\nabla_{\theta}\mathcal{J}(\theta) &= \frac{1}{B}\sum_{i=1}^{B} \nabla_{\theta}\mathcal{L}_{\mathcal{T}_i}\!\bigl(\theta_i(\theta);D^{\text{qry}}_{\mathcal T_i}\bigr)\\
>&=\frac{1}{B}\sum_{i=1}^{B} \left( \frac{ \partial \theta_{i} }{ \partial \theta } \right)\, \nabla_{\theta_{i}}\mathcal{L}_{\mathcal{T}_i}\!\bigl(\theta_i(\theta);D^{\text{qry}}_{\mathcal T_i}\bigr) \\
>&=\frac{1}{B}\sum_{i=1}^{B} \bigl(I - \alpha H_i\bigr)\, \nabla_{\theta_{i}}\mathcal{L}_{\mathcal{T}_i}\!\bigl(\theta_i(\theta);D^{\text{qry}}_{\mathcal T_i}\bigr).
>\end{align*}$$ 
>- where $$\theta_{i} = \theta - \alpha\,g_i$$
>- Dropping $\alpha H_i$ yields the **first‑order MAML** / **Reptile approximation**.

>[!important]
>The **Meta Update** 
>$$\theta \leftarrow \theta - \beta\,\nabla_{\theta}\mathcal{J}(\theta)$$



## Explanation

- [[Few-Shot Learning and Zero-Shot Learning]]

>[!quote]
>“Learn an **initialisation** that is already *pointing in the right direction* for *every task* you care about, so that one or two gradient nudges get you the rest of the way.”

>[!info]
>Because the approach makes **no architectural assumptions**, it can be plugged into anything from image classifiers to sequence transformers to contextual‑bandit policies

### Key characteristics

|Aspect|MAML property|
|---|---|
|**Agnosticism**|Works with _any_ differentiable model (CNNs, Transformers, policies, regressors, bandit routers …)|
|**Two time‑scales**|_Inner loop_ adapts parameters to a task; _outer loop_ updates the shared initialisation ϕ\phiϕ so adaptation is effective across tasks|
|**Data efficiency**|After meta‑training, new tasks need only a handful of labelled examples and a few gradient steps|
|**Single set of weights**|Unlike memory‑based meta‑learners, MAML does not store separate per‑task parameters; adaptation happens on‑the‑fly from ϕ\phiϕ|
|**Variants**|Second‑order MAML (exact Hessian), First‑order MAML / Reptile (Hessian term dropped), Meta‑SGD, ANIL, Probabilistic MAML, etc.|




-----------
##  Recommended Notes and References

- [[Contrastive Learning]]
- [[Distribution Shift in Transfer Learning]]

- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 749 - 750
- [[Deep Learning by Goodfellow]]