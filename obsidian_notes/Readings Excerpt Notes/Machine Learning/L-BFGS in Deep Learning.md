---
tags:
  - excerpt
  - reddit
  - optimization/algorithm
  - deep_learning
aliases: 
title: L-BFGS in Deep Learning
topics:
  - deep_learning
  - optimization/algorithm
url: https://www.reddit.com/r/MachineLearning/comments/4bys6n/lbfgs_and_neural_nets/
date of note: 2024-07-05
---

## Quote Summary

>[!quote]
>I've been doing a little bit of reading on optimization (from Nocedal's book) and have some questions about the prevalence of SGD and variants such as Adam for training neural nets.
> 
> L-BFGS and other quasi-Newton methods have both theoretical and [experimentally verified (PDF)](http://machinelearning.wustl.edu/mlpapers/paper_files/ICML2011Le_210.pdf) faster convergence. Are there any good reasons training with L-BFGS is much less popular (or at least talked about) than SGD and variants? For the deep learning practitioners, have you ever tried using L-BFGS or other quasi-Newton or conjugate gradient methods?
> 
> In a similar vein, has anyone experimented with doing a line search for optimal step size during each gradient descent step? A little searching found nothing more recent than earlier 1990's.
> 
> edit: Thanks for all the responses. Sounds like **high memory usage** from L-BFGS + **adequate performance** from with SGD with tricks is the reason that L-BFGS isn't typically used. There was a little more focus on the 2011 Stanford paper I referenced than I intended, so I'm going to share some more recent studies on **stochastic quasi-Newton optimization** for anyone interested:
> 
> - [http://arxiv.org/abs/1311.2115](http://arxiv.org/abs/1311.2115) - sped up convergence on > 1 million parameter net
>     
> - [http://arxiv.org/abs/1511.01169](http://arxiv.org/abs/1511.01169) - trained RNN on a few different datasets. Never used more than 10 gradient memory vectors, had mixed results with performance similar to Adam when using ReLU and superior when using tanh.
>     
> - [http://arxiv.org/abs/1401.7020](http://arxiv.org/abs/1401.7020) - impressive convergence speed and nice framework, but only applied algorithm to convex problems

- Reference link  [L-BFGS and neural nets](https://www.reddit.com/r/MachineLearning/comments/4bys6n/lbfgs_and_neural_nets/)




*******
## Related Notes

- [[Adam over L-BGFS in Deep Learning]]


- [[Limited Memory BFGS]]
- [[BFGS Algorithm]]
- [[Adam Algorithm]]
- [[Stochastic Gradient Descent Algorithm]]

- [[Deep Learning by Goodfellow]]
