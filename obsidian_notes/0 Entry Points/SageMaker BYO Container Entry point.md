---
tags:
  - entry_point
  - code
  - code_snippet
  - aws/sagemaker
  - model/training
keywords: 
topics: 
language: python
date of note: 2024-03-26
---

## Code Snippet Summary

>[!important] 
>Steps to **Bring Your Own (BYO)** Container
> 1. Write the *training script* `train` and *prediction script* `predictor.py`. 
> 	- [[SageMaker BYO Container - Pytorch Lightning Training]]
> 	- [[SageMaker BYO Container - Pytorch Lightning Hosting and Prediction]]
> 1. Write the *Dockerfile*. 
> 	- [[SageMaker SDK Training Script Dockerfile]]
> 2. **Build** *Docker Image* using Dockerfile and **Push** to *Amazon ECR*. 
> 	- [[SageMaker SDK Training Script Push Dockerfile to ECR]] 
> 3. **Test** algorithm in local machine or Amazon SageMaker instance 
> 	- [[SageMaker SDK Test Container in SageMaker]]
> 4. Start **Training Process** in **SageMaker** using Docker Image in ECR 
> 	- [[SageMaker SDK Training via Training API]]
> 5. **Deploy** model to **Endpoint** in **SageMaker**
> 	- [[SageMaker SDK Deploy Model to Endpoint]]





-----------
##  Recommended Notes

- Amazon SageMaker Examples. [Building your own algorithm container](https://sagemaker-examples.readthedocs.io/en/latest/advanced_functionality/scikit_bring_your_own/scikit_bring_your_own.html)
- Amazon SageMaker Developer Guide. [Deploy models for inference](https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html)
	- [Model Development](https://docs.aws.amazon.com/sagemaker/latest/dg/how-it-works-deployment.html)
	- [Real-time Inference](https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints.html)
		- [Automatically Scale Amazon SageMaker Models](https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-auto-scaling.html)
	- [Use Batch Transform](https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform.html)
	- [Use Docker Containers to build Models](https://docs.aws.amazon.com/sagemaker/latest/dg/docker-containers.html)