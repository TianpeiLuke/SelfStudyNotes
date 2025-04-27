---
tags:
  - concept
  - machine_learning/algorithms
  - deep_learning/algorithms
  - deep_learning/regularization
  - early_stopping
keywords:
  - early_stopping
topics:
  - deep_learning/regularization
name: Early Stopping for Deep Learning
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Early Stopping for Deep Learning

>[!important] Definition
>The **early stopping** is a regularization technique that allows the training *terminates* when *no validation error is improved* (after some time) and return the *parameters with best performance* by far.

>[!important] Definition
>The **early stopping meta-algorithm** is described as follow
>- *Require*: $n$ as the *number of steps* **between evaluations**
>- *Require*: $p$ as the **patience**, i.e the number of steps to *observe* worsening validation set error *before* termination
>- *Require*: initial parameters $\theta_{0}$
>- Initialize: 
>	- $$\theta \leftarrow \theta_{0},\; \theta^{*} \leftarrow \theta$$
>	- $$i \leftarrow 0, \;i^{*}\leftarrow i,\; j\leftarrow 0, \; v \leftarrow \infty$$
>- While $j < p$:
>	- Update $\theta$ via training algorithm *for $n$ steps*
>	- Update step $$i \leftarrow i+ n$$
>	- Update **validation error** $$v' \leftarrow \text{Evaluate}(\theta, \mathcal{X}_{val})$$
>	- If $v' < v$,  the **validation error is improved**:
>		- **Reset counter** $$j \leftarrow 0$$
>		- Update the **best candidate** as $$\theta^{*} \leftarrow \theta$$
>		- Update the **training steps** corresponds to the best candidate $$i^{*} \leftarrow i$$
>		- Update the **smallest validation error** $$v^{*} \leftarrow v$$
>	- Else
>		- Keep counting $$j \leftarrow j + 1$$
>- **Terminate** when the number of unimproved steps is beyond the *patience*
>	- *Return*: 
>		- the best candidate parameter $\theta^{*}$, 
>		- and the corresponding training steps $i^{*}$


>[!info]
>This is the **hill climbing greedy search**.

- [[Tabu Search]]
- [[Greedy Search and Hill Climbing]]


## Explanation

>[!quote]
>When training large models with *sufficient representational capacity* to **overfit the task**, we often observe that training error decreases steadily over time, but validation set error begins to rise again. See figure 7.3 for an example of this behavior, which occurs reliably.
>
>![[validation_early_stopping.png]]
>
>This means we can obtain a model with *better validation set error* (and thus, hopefully better test set error) by returning to the parameter setting at the point in time with the **lowest validation set error**. Every time the error on the validation set *improves*, we **store a copy** of the model parameters. When the training algorithm terminates, we return these parameters, *rather than the latest parameters*. The algorithm **terminates** when *no parameters* have improved over the **best recorded** validation error for some pre-specified number of iterations. This procedure is specified more formally in algorithm 7.1.  
>
>This strategy is known as **early stopping**. It is probably the most commonly used form of regularization in deep learning. Its popularity is due to both its effectiveness and its simplicity.
>
>-- [[Deep Learning by Goodfellow]] pp 239 - 240

- [[Bias-Complexity Tradeoff and Overfitting]]

### Regularization

>[!quote]
>*Early stopping* is an **unobtrusive form of regularization**, in that it requires almost no change in the underlying training procedure, the objective function, or the set of allowable parameter values. This means that it is easy to use early stopping without damaging the learning dynamics. This is in contrast to **weight decay**, where one must be careful not to use too much weight decay and *trap* the network in a *bad local minimum* corresponding to a solution with pathologically small weights.
>
>-- [[Deep Learning by Goodfellow]] pp 241

- [[Weight Decay for Deep Learning]]

>[!quote]
>Bishop (1995a) and Sjöberg and Ljung (1995) argued that *early stopping* has the effect of **restricting the optimization procedure** to a **relatively small volume of parameter space** in the neighborhood of the initial parameter value $\theta_{0}$, as illustrated in figure 7.4. 
>
>More specifically, imagine taking $\tau$ optimization steps (corresponding to $\tau$ training iterations) and with learning rate $\epsilon$ We can view the product  $\epsilon \tau$ as a **measure of effective capacity**. Assuming the gradient is bounded, **restricting** both the **number of iterations** and the **learning rate** limits the volume of parameter space reachable from θo. In this sense, $\epsilon \tau$  behaves as if it were the reciprocal of the coefficient used for *weight decay*.
>
>-- [[Deep Learning by Goodfellow]] pp 243

![[early_stop_regularization.png]]



### Limitations and Mitigations

>[!quote]
>Early stopping **requires a validation set**, which means some training data is not fed to the model. To best exploit this extra data, one can perform extra training after the initial training with early stopping has completed. In the second, extra training step, all the training data is included.
>- One strategy (algorithm 7.2) is to **initialize the model again** and **retrain on all the data**. In this second training pass, we train for the same number of steps as the early stopping procedure determined was optimal in the first pass. There are some **subtleties** associated with this procedure. For example, there is not a good way of knowing whether to *retrain* for the same number of *parameter updates* or the same number of *passes* through the dataset. On the second round of training, each pass through the dataset will require *more parameter updates* because the training set is bigger.
>- Another strategy for using *all the data* is to **keep the parameters** obtained from the first round of training and then **continue training**, but now using **all the data**. At this stage, we now no longer have a guide for when to stop in terms of a number of steps. Instead, we can *monitor the average loss function* on the validation set and continue training until it falls below the value of the training set objective at which the early stopping procedure halted. This strategy *avoids the high cost* of retraining the model from scratch **but is not as well behaved**. For example, the objective on the validation set may not ever reach the target value, so this strategy is not even guaranteed to terminate.
>  
>-- [[Deep Learning by Goodfellow]] pp 241 - 242  









-----------
##  Recommended Notes and References


- [[Tikhonov Regularization in Optimization and Learning]]
- [[Regularized Loss Minimization]]
- [[Artificial Neural Network and Deep Learning]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 239 - 243, 413
- [[Deep Learning Foundations and Concepts by Bishop]] pp 266