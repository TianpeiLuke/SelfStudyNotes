---
tags:
  - excerpt
  - deep_learning
  - optimization/algorithm
aliases: 
title: When training a neural network, why choose Adam over L-BGFS for the optimizer?
topics:
  - deep_learning
  - optimization/algorithm
url: https://scicomp.stackexchange.com/questions/34172/when-training-a-neural-network-why-choose-adam-over-l-bgfs-for-the-optimizer
date of note: 2024-07-05
---

## Quote Summary

>[!question]
> More specifically, when training a neural network, what reasons are there for choosing an optimizer from the family consisting of [stochastic gradient descent](https://en.wikipedia.org/wiki/Stochastic_gradient_descent) (SGD) and its extensions ([RMSProp](https://en.wikipedia.org/wiki/Stochastic_gradient_descent#RMSProp), [Adam](https://en.wikipedia.org/wiki/Stochastic_gradient_descent#Adam), etc.) instead of from the family of [Quasi-Newton methods](https://en.wikipedia.org/wiki/Quasi-Newton_method) (including limited-memory BFGS, abbreviated as L-BFGS)?
> 
> It is clear to me that some of the extensions of SGD, particularly RMSProp and Adam, store gradient information from previous iterates and use it to calculate the update for the next iterate. This is something they have in common with Quasi-Newton methods. However, the motivation behind storing the gradient information in the Adam method, for example, is unclear to me, whereas it is clear that in Quasi-Newton methods the motivation behind storing prior gradient information is to use it to construct an approximation to the Hessian (inverse).
> 
> I'm curious to understand:
> 
> - whether there are features of methods like Adam that make them particularly well-suited to machine learning applications;
> - whether these features enable them to outperform more conventional optimization methods like Quasi-Newton methods; and (ideally)
> - what is the general reasoning behind the update rule that these methods use.

>[!answer] 
>This topic has been discussed at some length on **Cross Validated** (aka _stats.stackexchange_) and **Reddit**:
> 
> 1. [_Why is Newton's method not widely used in machine learning?_](https://stats.stackexchange.com/questions/253632/why-is-newtons-method-not-widely-used-in-machine-learning) (see in particular Nick Alger's answer)
>     
> 2. [_Why use gradient descent with neural networks?_](https://stats.stackexchange.com/questions/181629/why-use-gradient-descent-with-neural-networks)
>     
> 3. [_L-BFGS and neural nets_](https://www.reddit.com/r/MachineLearning/comments/4bys6n/lbfgs_and_neural_nets/)
>     
> 4. [_Why second order SGD convergence methods are unpopular for deep learning?_](https://stats.stackexchange.com/questions/394083/why-second-order-sgd-convergence-methods-are-unpopular-for-deep-learning)
>     
> 5. [_How does the Adam method of stochastic gradient descent work?_](https://stats.stackexchange.com/questions/220494/how-does-the-adam-method-of-stochastic-gradient-descent-work)
>     
> 
> Other relevant references:
> 
> 1. Bottou et al., [_Optimization Methods for Large-Scale Machine Learning_](https://leon.bottou.org/publications/pdf/sirev-2018.pdf) (_SIAM Review_ 2018), in particular section 6 on second-order methods.
>     
> 2. Ian Goodfellow's [_Deep learning_](http://www.deeplearningbook.org/contents/optimization.html) book, chapter on optimization, section 8.6 (second-order methods).
>     
> 3. Quoc Le et al., [On optimization methods for deep learning](https://cs.stanford.edu/~acoates/papers/LeNgiCoaLahProNg11.pdf)
>     
> 4. Dauphin et al., [Identifying and attacking the saddle point problem in high-dimensional non-convex optimization](https://arxiv.org/abs/1406.2572)
>     
> 
> **TL;DR**: The jury is still out on second-order methods.





*******

## Related Notes

- [[L-BFGS in Deep Learning]]


- [[Limited Memory BFGS]]
- [[BFGS Algorithm]]
- [[Adam Algorithm]]
- [[Stochastic Gradient Descent Algorithm]]

- [[Deep Learning by Goodfellow]]