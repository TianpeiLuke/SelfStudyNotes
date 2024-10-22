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




![[convolution_filter.png]]

### Translation Invariance






![[convolution_operation.png]]



![[convolution_image.png]]


### Padding and Strided Convolutions






### Multi-dimensional Convolutions


![[multidim_convolution_layer.png]]


### Pooling


- [[Pooling for Deep Learning]]


## Explanation

>[!quote]
>One **motivation** for the introduction of convolutional networks is that for *image data*, which is the modality for which CNNs were designed, a standard fully connected architecture would **require vast numbers of parameters** due to the *high-dimensional nature of images*. To see this, consider a colour image with $103 \times 103$ pixels, each with three values corresponding to red, green, and blue intensities. If the first hidden layer of the network has, say, $1,000$ hidden units, then we already have $3 \times 109$ weights in the first layer. Furthermore, such a network would have to learn any **invariances** and **equivariances** by example, which would require huge data sets. By designing an architecture that incorporates our *inductive bias* about the *structure of images*, we can reduce the data set requirements dramatically and also improve generalization with respect to **symmetries in the image space**.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 290

- [[Equivariance of Estimator]]
- [[Invariance under Linear Transformation]]
- [[Inductive Bias in Machine Learning]]



-----------
##  Recommended Notes and References


- [[Convolutional Neural Network]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 625
- [[Deep Learning by Goodfellow]] pp 321
- [[Deep Learning Foundations and Concepts by Bishop]] pp 290
- Torralba, A., Isola, P., & Freeman, W. T. (2024). _Foundations of Computer Vision_. The MIT Press. pp 335 - 342