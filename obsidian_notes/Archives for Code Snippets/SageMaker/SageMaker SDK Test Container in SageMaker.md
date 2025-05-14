---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - model/training
  - python/aws_python_sdk
keywords: 
topics: 
language: python
date of note: 2024-03-28
---

## Code Snippet Summary

>[!important] 
>The tasks for a typical training script:
> - **loads** data from input channel;
> - **configure** training with hyperparameters;
> - **train** a model
> - **save** a model to `model_dir` so that it can be deployed to endpoint

## Code






-----------
##  Recommended Notes

- [[SageMaker BYO Container Entry point]]
- Test Algorithm locally [link](https://sagemaker-examples.readthedocs.io/en/latest/advanced_functionality/scikit_bring_your_own/scikit_bring_your_own.html#Testing-your-algorithm-on-your-local-machine-or-on-an-Amazon-SageMaker-notebook-instance)