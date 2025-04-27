---
tags:
  - concept
  - machine_learning/models
  - deep_learning/discriminative_models
  - max_pooling
  - average_pooling
  - convolutional_neural_network
  - cnn
keywords:
  - max_pooling_deep_learning
topics:
  - deep_learning/discriminative_models
  - deep_learning/network_block
name: Pooling for Deep Learning
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Pooling for Deep Learning

### Max Pooling 

>[!quote]
>**Pooling** has similarities to using a convolutional layer in that an array of units is arranged in a grid, with each unit taking input from a receptive field in the previous feature map layer. Again, there is a choice of *filter size* and of *stride length*. The difference, however, is that the output of a pooling unit is a *simple, fixed function* of its inputs, and so there are **no learnable parameters in pooling**.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 297

^409d21

>[!important] Definition
>Let $I$ be an *feature map tensor* with $c$ channels.
>
>The **max pooling** with **receptive field** size $k\times k$ has values given by 
>$$
>C[i, j, s] = \max_{l \in [i: i+k-1], \; m\in [j: j+k-1]} I[l, m, s], \quad s=1\,{,}\ldots{,}\,c
>$$

^f4bdf0

>[!important] Definition
>The **average pooling** with **receptive field** size $k\times k$ has values given by 
>$$
>C[i, j, s] = \sum_{l \in [i: i+k]}\sum_{m\in [j: j+k]} I[l, m, s], \quad s=1\,{,}\ldots{,}\,c
>$$

>[!info]
>- Pooling is usually applied to *each channel* of a feature map **independently**.
>- We can also apply pooling **across multiple channels** of a feature map, which gives the network the potential to learn other invariances beyond simple translation invariance.

![[max_pooling.png]]

>[!important] 
>Same as convolution, the *dimensionality of output* of **pooling** with 
>- kernel size $k$, 
>- padding $p$ and 
>- *stride* $s$ 
>- for a feature map tensor $n\times m\times c$ 
>
>is 
>$$ \left( \left\lfloor \frac{n + 2p - k}{s} \right\rfloor + 1 \right)   \times  \left( \left\lfloor  \frac{m + 2p - k}{s} \right\rfloor + 1 \right) \times c$$

### Downsampling

>[!quote]
>As well as building in some *local translation invariance*, **pooling** can also be used to **reduce the dimensionality** of the representation by **down-sampling** the feature map. 
>- Note that using **strides greater than** $1$ in a convolutional layer also has the effect of **down-sampling** the feature maps.



### Pooling in CNN

>[!quote]
>A typical layer of a convolutional network consists of three stages (see figure 9.7). 
>
>- In the first stage, the layer performs several **convolutions** in parallel to produce a set of linear activations. 
>
>- In the second stage, each linear activation is run through a nonlinear activation function, such as the *rectified linear activation function*. This stage is sometimes called the **detector stage**. 
>- In the third stage, we use a **pooling function** to modify the output of the layer further.
>  
>-- [[Deep Learning by Goodfellow]] pp 330  

![[pooling_cnn.png]]

## Explanation

### Compare to Convolution

>[!quote]
>The **advantage** of a convolutional layer compared to using a linear layer is that the *weights of the kernel* are **shared** *across locations* in the input. Thus if a pattern in the input shifts locations, the corresponding output activation will also shift. This is called **shift equivariance**. 
> 
> In some cases, we want the output to be the same, no matter where the input pattern occurs; this is called **shift invariance**, and can be obtained by using a **pooling layer**, which computes the maximum or average value in each local patch of the input. (Note that pooling layers have no free (learnable) parameters.) Other forms of invariance can also be captured by neural networks (see e.g., [CW16; FWW21]).
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 626

>[!quote]
>A convolutional layer encodes **translation equivariance**, whereby if a small patch of pixels, representing the receptive field of a hidden unit, is moved to a different location in the image, the associated outputs of the feature map will move to the corresponding location in the feature map. This is valuable for applications such as *finding the location of an object* within an image. 
>
>For other applications, such as classifying an image, we want the output to be **invariant to translations** of the input. In all cases, however, we want the network to be able to learn hierarchical structure in which complex features at a particular level are built up from simpler features at the previous level. 
>- In many cases the **spatial relationship** between those *simpler features* will be important. For example, it is the relative positions of the eyes, nose, and mouth that help determine the presence of a face and not just the presence of these features in arbitrary locations within the image. However, small changes in the relative locations do not affect the classification, and we want to be invariant to such small translations of individual features. 
>
>This can be achieved using **pooling** applied to the *output of the convolutional layer.*
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 297

- [[Convolutional Filters]]






-----------
##  Recommended Notes and References

- [[Equivariance of Estimator]]
- [[Convolutional Neural Network]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 626
- [[Deep Learning by Goodfellow]] pp 330
- [[Deep Learning Foundations and Concepts by Bishop]] pp 296
- [[Foundations of Computer Vision by Torralba]] 