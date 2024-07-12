---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
  - container
  - bring_your_own
aliases: 
keywords: 
topics:
  - BYO container
language: python
date of note: 2024-03-28
name: Building Your Own Container
version: 
year: 2022
---

# Overview

>[!quote]
>With Amazon SageMaker, you can package your own algorithms that can than be trained and deployed in the **SageMaker environment**. This notebook will guide you through an example that shows you how to build a Docker container for SageMaker and use it for training and inference. 
>
>By packaging an algorithm in a container, you can bring almost any code to the Amazon SageMaker environment, regardless of programming language, environment, framework, or dependencies.
>-- [link](https://sagemaker-examples.readthedocs.io/en/latest/advanced_functionality/scikit_bring_your_own/scikit_bring_your_own.html)

## When should I build my own algorithm container?

>[!important]
> - You may not need to create a container to bring your own code to Amazon SageMaker. When you are using a **framework** (such as Apache MXNet or TensorFlow. See [[Amazon SageMaker Python SDK 3 Frameworks]]) that has direct support in SageMaker, you can simply *supply the Python code* that implements your algorithm using the **SDK entry points** for that framework. This set of frameworks is continually expanding, so we recommend that you check the current list if your algorithm is written in a common machine learning environment.

- Even if there is direct SDK support for your environment or framework, you may find it more effective to *build your own container*. If the code that implements your algorithm is quite *complex* on its own or you need *special additions* to the framework, building your own container may be the right choice.

- If there isn’t direct SDK support for your environment, don’t worry. You’ll see in this walk-through that building your own container is quite straightforward.

## Permissions

- Running this notebook requires permissions in addition to the normal `SageMakerFullAccess` permissions.

## The example

>[!example]
>Here, we’ll show how to package a simple Python example which showcases the [decision tree](http://scikit-learn.org/stable/modules/tree.html) algorithm from the widely used [scikit-learn](http://scikit-learn.org/stable/) machine learning package. The example is purposefully fairly trivial since the point is to **show the surrounding structure** that you’ll want to add to your own code so you can train and host it in Amazon SageMaker.
>


# Part 1: Packaging and Uploading your Algorithm for use with Amazon SageMaker

[[Amazon SageMaker Example Building Your Own Container 1 Docker]]



-----------
##  Recommended Notes

- [[Amazon SageMaker Python SDK 3 Frameworks]]




----------
##  Citations

-  [source link](https://sagemaker-examples.readthedocs.io/en/latest/advanced_functionality/scikit_bring_your_own/scikit_bring_your_own.html) for the doc
- *code package link*: [github repo](https://github.com/aws/amazon-sagemaker-examples/blob/main/advanced_functionality/scikit_bring_your_own/scikit_bring_your_own.ipynb)




