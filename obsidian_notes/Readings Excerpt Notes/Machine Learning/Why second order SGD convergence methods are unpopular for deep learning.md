---
tags:
  - excerpt
  - deep_learning
  - optimization/algorithm
aliases: 
title: Why second order SGD convergence methods are unpopular for deep learning?
topics:
  - deep_learning
  - optimization/algorithm
url: https://stats.stackexchange.com/questions/394083/why-second-order-sgd-convergence-methods-are-unpopular-for-deep-learning
date of note: 2024-07-05
---

## Quote Summary

>[!question]
> It seems that, especially for deep learning, there are dominating very simple methods for optimizing SGD convergence like ADAM - nice overview: [http://ruder.io/optimizing-gradient-descent/](http://ruder.io/optimizing-gradient-descent/)
> 
> They **trace only single direction** - discarding information about the remaining ones, they **do not try to estimate distance from near extremum** - which is suggested by gradient evolution (→0→0 in extremum), and could help with the crucial choice of step size.
> 
> Both these missed opportunities could be exploited by second order methods - trying to locally model parabola in simultaneously multiple directions (not all, just a few), e.g. near saddle attracting in some directions, repulsing in the others. Here are some:
> 
> - L-BFGS: [http://aria42.com/blog/2014/12/understanding-lbfgs](http://aria42.com/blog/2014/12/understanding-lbfgs)
> - TONGA: [https://papers.nips.cc/paper/3234-topmoumoute-online-natural-gradient-algorithm](https://papers.nips.cc/paper/3234-topmoumoute-online-natural-gradient-algorithm)
> - K-FAC: [https://arxiv.org/pdf/1503.05671.pdf](https://arxiv.org/pdf/1503.05671.pdf)
> - saddle-free Newton: [https://arxiv.org/pdf/1406.2572](https://arxiv.org/pdf/1406.2572)
> - my second order local parametrization: [https://arxiv.org/pdf/1901.11457](https://arxiv.org/pdf/1901.11457)
> 
> But still first order methods dominate (?), I have heard opinions that second order just don't work for deep learning (?)
> 
> There are mainly 3 challenges (any more?): **inverting Hessian**, **stochasticity** of gradients, and handling **saddles**. All of them should be resolved if locally modelling parametrization as parabolas in a few promising directions (I would like to use): update this parametrization based on calculated gradients, and perform proper step based on this parametrization. This way extrema can be in updated parameters - no Hessian inversion, slow evolution of parametrization allows to accumulate statistical trends from gradients, we can model both curvatures near saddles: correspondingly attract or repulse, with strength depending on modeled distance.
> 
> **Should we go toward second order methods for deep learning?**
> 
> Why is it so difficult to make them more successful than simple first order methods - could we **identify these challenges** ... resolve them?
> 
> As there are many ways to realize second order methods, which seems the most promising?
> 
> Update: Overview of SGD convergence methods including 2nd order: [https://www.dropbox.com/s/54v8cwqyp7uvddk/SGD.pdf](https://www.dropbox.com/s/54v8cwqyp7uvddk/SGD.pdf)
> 
> Update: There are criticized huge 2nd order methods, but we can work on the opposite end of cost spectrum: make tiny steps from successful 1st order methods, like just cheap [online parabola model](https://arxiv.org/abs/1907.07063) in single direction e.g. of momentum method for smarter choice of step size - are there interesting approaches for such 2nd order enhancement of 1st order methods?

>[!answer] 
>> Should we go toward second order methods for deep learning?
> 
> TL;DR: No, especially now when the pace of innovation is slowing down, and we're seeing less new architectural innovations, and more ways to train what are basically just *copies of existing architectures*, on larger datasets (see OpenAI's GPT-2).
> 
> **First**, without even getting to second order, it's worth mentioning that in Deep Learning you *don't even use (mini-batch) gradient descent* to the fullest of its potential (i.e., you *don't perform line search*), because the optimization step in line search would be very costly.
> 
> **Second**, second order methods are:
> 
> - way more *complex*, i.e., harder to implement without *bugs*. DL systems are increasingly becoming a small part of huge data processing pipelines. Introducing further complexity and brittleness in a complex system is only wise if the gains largely *offset the risks*. I'll argue below that they don't.
> - harder to optimize for *distributed computing on heterogeneous hardware*, which is becoming more and more common. See how much work was required in order to make K-FAC work on distributed (**non** heterogeneous) systems, and performances are still no better than the best first-order methods: [https://arxiv.org/pdf/1811.12019.pdf](https://arxiv.org/pdf/1811.12019.pdf). Instead, if just switching to distributed computing makes my first-order method as fast as, or faster, than second-order methods, I don't see the reason to use a more complicated optimization algorithm.
> - way more *expensive* in terms of *iteration* **cost** (not number) **and** *memory occupation*, thus they introduce a considerable overhead. Current architectures (GPUs) are more *memory-bound* that *computation-bound*. As explained very well [here](https://stats.stackexchange.com/questions/320082/why-not-use-the-third-derivative-for-numerical-optimization), the increase in iteration cost and memory occupation is steeper, the more high-dimensional the problem is. Optimization in Deep Learning is arguably one of the **most** *high-dimensional optimization problems*, so it's not clear that second order methods would have a clear advantage in terms of computational _time_ (not iteration count, which is not what we really care about) wrt first-order methods.
> - another issue with Deep Learning optimization are **saddle points**. It's becoming abundantly clear that *"bad" local minima* are not an issue in Deep Learning, but *saddle points* are. [Newton's method does have a tendency to be attracted to saddle points](https://stats.stackexchange.com/a/301728/58675). If I remember correctly, **Hessian approximating** methods such as K-FAC don't have this issue, but I think the proof depends on the type of architecture, making the use of such methods brittle.
> - they don't fix the problems which make practitioners waste most of their time. Dead or saturated units are not solved by K-FAC, but by better initialization schemes, so that's what we should focus on, e.g., Fixup: [https://arxiv.org/abs/1901.09321](https://arxiv.org/abs/1901.09321)
> - another issue with second order methods is that for *most common loss functions*, it's easy to use mini-batches to get an estimator which converges to the actual gradient. It is much more complicated to build a *sampling-based estimator* for the **approximation** to the **inverse of the Hessian**. In other words, second order methods introduce a lot of *complexity and extra memory occupation*, but _stochastic_ second order methods introduce _even more_ complexity. Contrast that with stochastic _first order_ methods, where the algorithm is just slightly more complicated than that of deterministic first order methods.
> - finally, they have a lot of moving parts, which are difficult to tune up in the best way. Your same paper leaves a lot of details to be specified. Do we need even more extra hyperparameters, or do we need robust optimization methods? Keep in mind that in Deep Learning, as explained very well by Shai Shalev-Shwartz, when something goes wrong, it's very difficult to understand how to fix it [https://www.youtube.com/watch?v=1nvf_DBnsxo](https://www.youtube.com/watch?v=1nvf_DBnsxo) and more hyperparameters don't help in that respect.





*******

## Related Notes

- [[L-BFGS in Deep Learning]]
- [[Adam over L-BGFS in Deep Learning]]


- [[Limited Memory BFGS]]
- [[BFGS Algorithm]]
- [[Adam Algorithm]]
- [[Stochastic Gradient Descent Algorithm]]

- [[Deep Learning by Goodfellow]]