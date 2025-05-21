---
tags:
  - entry_point
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-25
name: Amazon SageMaker Python SDK Doc
version: 
year: 2024
---
# Introduction

>[!quote]
> **Amazon SageMaker Python SDK** is an open source library for training and deploying machine-learned models on Amazon SageMaker.
> 
> With the SDK, you can train and deploy models using popular deep learning frameworks, algorithms provided by Amazon, or your own algorithms built into SageMaker-compatible Docker images.
> 
> Here you’ll find an overview and API documentation for SageMaker Python SDK. The project homepage is in Github: [https://github.com/aws/sagemaker-python-sdk](https://github.com/aws/sagemaker-python-sdk), where you can find the SDK source and installation instructions for the library.
> 
> -- [link](https://sagemaker.readthedocs.io/en/stable/index.html)


>[!quote]
> SageMaker Python SDK provides several high-level abstractions for working with Amazon SageMaker. These are:
> 
> - **Estimators**: Encapsulate training on SageMaker.
>     
> - **Models**: Encapsulate built ML models.
>     
> - **Predictors**: Provide real-time inference and transformation using Python data-types against a SageMaker endpoint.
>     
> - **Session**: Provides a collection of methods for working with SageMaker resources.
>     
> - **Transformers**: Encapsulate batch transform jobs for inference on SageMaker
>     
> - **Processors**: Encapsulate running processing jobs for data processing on SageMaker
>     
> 
> `Estimator` and `Model` implementations for MXNet, TensorFlow, Chainer, PyTorch, scikit-learn, Amazon SageMaker built-in algorithms, Reinforcement Learning, are included. There’s also an `Estimator` that runs SageMaker compatible custom Docker containers, enabling you to run your own ML algorithms by using the SageMaker Python SDK.
> -- [link](https://sagemaker.readthedocs.io/en/stable/index.html)

# Overview

> [!quote]
> Contents
> 
> - [Using the SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/overview.html#using-the-sagemaker-python-sdk)
>     
>     - [Train a Model with the SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/overview.html#train-a-model-with-the-sagemaker-python-sdk)
>         
>     - [Using Models Trained Outside of Amazon SageMaker](https://sagemaker.readthedocs.io/en/stable/overview.html#using-models-trained-outside-of-amazon-sagemaker)
>         
>     - [Use Built-in Algorithms with Pre-trained Models in SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/overview.html#use-built-in-algorithms-with-pre-trained-models-in-sagemaker-python-sdk)
>         
>     - [SageMaker Automatic Model Tuning](https://sagemaker.readthedocs.io/en/stable/overview.html#sagemaker-automatic-model-tuning)
>         
>     - [SageMaker Asynchronous Inference](https://sagemaker.readthedocs.io/en/stable/overview.html#sagemaker-asynchronous-inference)
>         
>     - [SageMaker Serverless Inference](https://sagemaker.readthedocs.io/en/stable/overview.html#sagemaker-serverless-inference)
>         
>     - [SageMaker Batch Transform](https://sagemaker.readthedocs.io/en/stable/overview.html#sagemaker-batch-transform)
>         
>     - [Local Mode](https://sagemaker.readthedocs.io/en/stable/overview.html#local-mode)
>         
>     - [Secure Training and Inference with VPC](https://sagemaker.readthedocs.io/en/stable/overview.html#secure-training-and-inference-with-vpc)
>         
>     - [Secure Training with Network Isolation (Internet-Free) Mode](https://sagemaker.readthedocs.io/en/stable/overview.html#secure-training-with-network-isolation-internet-free-mode)
>         
>     - [Inference Pipelines](https://sagemaker.readthedocs.io/en/stable/overview.html#inference-pipelines)
>         
>     - [SageMaker Workflow](https://sagemaker.readthedocs.io/en/stable/overview.html#sagemaker-workflow)
>         
>     - [SageMaker Model Building Pipeline](https://sagemaker.readthedocs.io/en/stable/overview.html#sagemaker-model-building-pipeline)
>         
>     - [SageMaker Model Monitoring](https://sagemaker.readthedocs.io/en/stable/overview.html#sagemaker-model-monitoring)
>         
>     - [SageMaker Debugger](https://sagemaker.readthedocs.io/en/stable/overview.html#sagemaker-debugger)
>         
>     - [SageMaker Processing](https://sagemaker.readthedocs.io/en/stable/overview.html#sagemaker-processing)
>         
>     - [Configuring and using defaults with the SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/overview.html#configuring-and-using-defaults-with-the-sagemaker-python-sdk)
>         
>     - [Run Machine Learning code on SageMaker using remote function](https://sagemaker.readthedocs.io/en/stable/overview.html#run-machine-learning-code-on-sagemaker-using-remote-function)
>         
>     - [FAQ](https://sagemaker.readthedocs.io/en/stable/overview.html#faq)
> 
> 


# Entry Points

- [[Amazon SageMaker Python SDK 1 Training Model with SDK]]
- [[Amazon SageMaker Python SDK 2 Deploy a Pre-Trained Model]]
- [[Amazon SageMaker Python SDK 3 Frameworks]]
	- [[Amazon SageMaker Python SDK 3.1.1 Pytorch Train]]
	- [[Amazon SageMaker Python SDK 3.1.2 Pytorch Deploy and Hosting]]
	- [[Amazon SageMaker Python SDK 3.1.3 BYO Model and Attach]]
	- [[Amazon SageMaker Python SDK 3.1.4 Pytorch Lightning]]
	- [[Amazon SageMaker distributed data parallelism library]]
- [[Amazon SageMaker Python SDK 4 Processing]]
	- [[Amazon SageMaker Python SDK 4.1 BYO Processing Container]]
- [[Amazon SageMaker Python SDK 5 Workflow and Step Function]]

# Application NLP Pipeline

## Processing

- [[Processors ver 2.0]]
- [[Processors Categorical Labeler]]
- [[Processors Multiclass One-hot Encoder]]
- [[Processors Tokenizer]]
- [[Processors CS Chat]]

- [[BSMDataset]]
- [[Data Loader]]

## Models

- [[Tabular Embedding with Pydantic]]
- [[BERT Base Embedding Model with Pydantic]]
- [[Multi-modal BERT for FSDP Model Parallelism]]
- [[Multi-modal BERT via Fusion Gate]]
- [[Multi-modal BERT via Mixture of Experts]]
- [[Multi-modal BERT via Cross-Attention]]
- [[Export to ONNX and Inference]]
- [[Trainer for FSDP Model Parallelism]]

- [[RnR Model Compute Metrics]]
- [[RnR Model Performance Plots]]

## Training and Inference Main Script

- [[Train Script under FSDP]]
- [[Inference Script for RnR BSM]]
- [[Requirements]]

## Pipeline

- [[Pytorch Estimator Training for RnR BSM]]
- [[Pytorch Estimator Inference for RnR BSM]]
- [[Batch Transform using Endpoint from SageMaker]]

- [[An End-to-End Training Deployment Pipeline on AWS]]
- [[Hyperparameter for Training Step]]
- [[Model Config for Training Step]]
- [[Builder Training Step]]
- [[Builder Model Step]]



----------
##  Citations

- Amazon SageMaker Python SDK Documentation [link](https://sagemaker.readthedocs.io/en/stable/index.html)
- [Using the SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/overview.html)
- [SageMaker PyTorch Training Toolkit](https://github.com/aws/sagemaker-pytorch-training-toolkit)
- [SageMaker PyTorch Inference Toolkit](https://github.com/aws/sagemaker-pytorch-inference-toolkit)
- [Images for PyTorch](https://github.com/aws/deep-learning-containers/tree/master/pytorch)
- [AWS Step Functions Python SDK website](https://aws-step-functions-data-science-sdk.readthedocs.io/en/stable/)
- [SageMaker distributed data parallelism library](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-intro.html)
- *code source*: [https://github.com/aws/sagemaker-python-sdk](https://github.com/aws/sagemaker-python-sdk)
- *code package link*: 




