---
tags:
  - concept
  - machine_learning/models
  - deep_learning/discriminative_models
  - deep_learning/architecture
  - deep_learning/models
keywords:
  - convolutional_filter
  - translation_invariance
  - equivarience
topics:
  - deep_learning/network_block
  - deep_learning/algorithm
  - deep_learning/discriminative_models
name: Convolutional Filters
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Convolutional Filters

### Convolution Operation

 ![[Convolution Operation#^a2007d]]
- [[Convolution Operation]]

>[!important] Definition
>The **convolution** between $f$ and $K$ is given by $$s(t) = (f*K)(t) = \int f(x)\,K(t - x)\,dx$$
>- The first argument $f$ is called the **input** of convolution
>- The *second argument* $K$ is called the **kernel** of convolution.
>- The *output* is referred as the **feature map.**

- [[Reproducing Kernel of RKHS]]

### Digital Convolution

>[!important] Definition
>Let $I[j, k]$ be $(j,k)$ position of image and $K$ be a **filter** with values $K(l,m)$.
>
>The **feature map** $C$ has values given by 
>$$
>C[j, k] = \sum_{l}\sum_{m}I[j+l, k+m]\,K[l, m]
>$$
>- This feature map is the result of **convolution**, referred as $$C = I * K.$$
>- Strictly speaking, this is actually **cross-correlation operation.** In deep learning, the cross-correlation and convolution operations are not distinguished.

>[!important] Definition
>The **two-dimensional convolution operation** between $I$ and $K$ is given by 
>$$
>C[j,k] = (I*K)[j,k] = \sum_{l}\sum_{m}\,I[l, m]\,K[j - l, k - m]
>$$
>or equivalently,
>$$
>C[j,k] = (K*I)[j,k] = \sum_{l}\sum_{m}\,I[j - l, k - m]\,K[l, m]
>$$



![[convolution_filter.png]]

### Translation Equivariance

>[!quote]
> The units of the hidden layer form a **feature map** in which all the units *share the same weights*. Consequently if a *local patch* of an image produces a particular response in the unit connected to that patch, then the *same set* of pixel values at a different location will produce the *same response* in the corresponding **translated location** in the feature map. 
> - This is an example of **equivariance**. 
> 
>We see that the connections in this network are **sparse** in that most connections are absent. Also, the values of the weights are **shared** by *all the hidden units*, as indicated by the colours of the connections. This transformation is an example of a **convolution**.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 292

>[!quote]
>The **advantage** of a convolutional layer compared to using a linear layer is that the *weights of the kernel* are **shared** *across locations* in the input. Thus if a pattern in the input shifts locations, the corresponding output activation will also shift. This is called **shift equivariance**. In some cases, we want the output to be the same, no matter where the input pattern occurs; this is called **shift invariance**, and can be obtained by using a **pooling layer**, which computes the maximum or average value in each local patch of the input. (Note that pooling layers have no free (learnable) parameters.) Other forms of invariance can also be captured by neural networks (see e.g., [CW16; FWW21]).
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 626




![[convolution_operation.png]]



![[convolution_image.png]]


### Padding and Strided Convolutions






### Multi-dimensional Convolutions


![[multidim_convolution_layer.png]]


### Pooling


- [[Pooling for Deep Learning]]


## Explanation

### Motivations

>[!quote]
>One **motivation** for the introduction of convolutional networks is that for *image data*, which is the modality for which CNNs were designed, a standard fully connected architecture would **require vast numbers of parameters** due to the *high-dimensional nature of images*. To see this, consider a colour image with $103 \times 103$ pixels, each with three values corresponding to red, green, and blue intensities. If the first hidden layer of the network has, say, $1,000$ hidden units, then we already have $3 \times 109$ weights in the first layer. Furthermore, such a network would have to learn any **invariances** and **equivariances** by example, which would require huge data sets. By designing an architecture that incorporates our *inductive bias* about the *structure of images*, we can reduce the data set requirements dramatically and also improve generalization with respect to **symmetries in the image space**.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 290

- [[Equivariance of Estimator]]
- [[Invariance under Linear Transformation]]
- [[Inductive Bias in Machine Learning]]

>[!important]
>Convolution leverages **three important ideas** that can help improve a machine learning system: 
>
>- **Sparse Interactions** (also referred to as **sparse connectivity** or **sparse weights**): Instead of allowing every output unit interacts with every input unit, *Convolutional networks*, typically have *sparse interactions*. 
>	- This is accomplished by making the **kernel** *smaller* than the *input*. 
>	- This means that we store *fewer parameters*, which both reduces the *memory requirements* of the model and improves its statistical efficiency. 
>	- It also means that computing the output requires *fewer operations*. These improvements in efficiency are usually quite large. 
>	- If we limit the *number of connections* each output may have to $k$, then the *sparsely connected* approach requires only $k \times n$ parameters and $$O(m \times n) \to O(k \times n)$$ runtime.
>- **Parameter sharing**:  refers to using the *same parameter* for more than one function in a model. 
>	- In a *traditional neural net*, each element of the weight matrix is used *exactly once* when computing the output of a layer. As a synonym for parameter sharing, one can say that a network has **tied weights**, because the value of the weight applied to *one input* is *tied* to the value of a *weight* applied elsewhere.
>	- In a *convolutional neural net*, each member of the **kernel** is used at *every position* of the input. 
>	- The parameter sharing used by the convolution operation means that rather than learning a *separate set of parameters* for *every location*, we **learn only one set**. 
>	- This does not affect the runtime of forward propagation—it is still $O(k \times n)$ —but it does further **reduce the storage requirements** of the model to $k$ parameters.
>- **Equivariant representations**. 
>	- To say a function is equivariant means that if the *input changes*, the *output changes in the same way*. 
>	- Specifically, a function $f(x)$ is *equivariant* to a function $g$ if $$f(g(x)) = g(f(x)).$$
>	- The **convolution** is *equivalent* to **translation (shift) operation.**
>	- Convolution is *not naturally equivariant* to some other transformations, such as **changes in the scale** or **rotation of an image**. 
>
>-- [[Deep Learning by Goodfellow]] pp 325





-----------
##  Recommended Notes and References


- [[Convolutional Neural Network]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 625
- [[Deep Learning by Goodfellow]] pp 321
- [[Deep Learning Foundations and Concepts by Bishop]] pp 290
- [[Foundations of Computer Vision by Torralba]]  pp 335 - 342