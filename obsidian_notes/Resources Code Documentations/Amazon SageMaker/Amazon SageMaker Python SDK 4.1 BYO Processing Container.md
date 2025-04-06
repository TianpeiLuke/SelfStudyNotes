---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
  - bring_your_own
  - container
  - model/processing
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-31
name: Amazon SageMaker Python SDK Doc
version: 
year: 2024
---

# Bring Your Own Processing Container

>[!info]
> - You can provide Amazon SageMaker Processing with a **Docker image** that has your own *code and dependencies* to run your data processing, feature engineering, and model evaluation workloads.
> 
> - Example on *Dockerfile* in [[Dockerfile for Model Training]]
> - Example code on build Docker Image and pull to ECR [[Amazon ECR or Elastic Container Registry Create and Push Image]]
> - For an example of a *processing script*, see [Get started with SageMaker Processing](https://github.com/aws/amazon-sagemaker-examples/blob/main/sagemaker_processing/basic_sagemaker_data_processing/basic_sagemaker_processing.ipynb).
> -- [link](https://docs.aws.amazon.com/sagemaker/latest/dg/build-your-own-processing-container.html) 

## How Amazon SageMaker Processing Runs Your Processing Container Image



## How Amazon SageMaker Processing Configures Input and Output For Your Processing Container

- When you create a processing job using the `CreateProcessingJob` operation, you can specify **multiple `ProcessingInput` and `ProcessingOutput`. values**.

>[!important]
> - You use the **`ProcessingInput` parameter** to specify an Amazon Simple Storage Service (Amazon S3) URI to download data from, and a path in your processing container to download the data to.
> - The **`ProcessingOutput` parameter** configures a path in your processing container from which to upload data, and where in Amazon S3 to upload that data to. 
> - For both `ProcessingInput` and `ProcessingOutput`, the **path in the processing container** must begin with **`/opt/ml/processing/` **.


## Run Your Processing Container Using the SageMaker Python SDK

- You can use the SageMaker Python SDK to run **your own processing image** by using the **`Processor` class**. The following example shows how to run your own processing container with one *input from Amazon Simple Storage Service (Amazon S3)* and one *output to Amazon S3*.

```python
from sagemaker.processing import Processor, ProcessingInput, ProcessingOutput

processor = Processor(image_uri='<your_ecr_image_uri>',
                     role=role,
                     instance_count=1,
                     instance_type="ml.m5.xlarge")

processor.run(inputs=[ProcessingInput(
                        source='<s3_uri or local path>',
                        destination='/opt/ml/processing/input_data')],
                    outputs=[ProcessingOutput(
                        source='/opt/ml/processing/processed_data',
                        destination='<s3_uri>')],
                    )
```

- See similar discussion in [[Amazon SageMaker Example Building Your Own Container 0 Overview]]



----------
##  Citations

- Amazon SageMaker Python SDK Documentation [link](https://sagemaker.readthedocs.io/en/stable/index.html)
- [Using the SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/overview.html)
- **Processor** class documentation: [reference](https://sagemaker.readthedocs.io/en/stable/amazon_sagemaker_processing.html#processing-class-documentation)
	- [`sagemaker.processing.Processor`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.Processor "sagemaker.processing.Processor")
	- [`sagemaker.processing.ScriptProcessor`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ScriptProcessor "sagemaker.processing.ScriptProcessor")
	- [`sagemaker.sklearn.processing.SKLearnProcessor`](https://sagemaker.readthedocs.io/en/stable/frameworks/sklearn/sagemaker.sklearn.html#sagemaker.sklearn.processing.SKLearnProcessor "sagemaker.sklearn.processing.SKLearnProcessor")
	- [`sagemaker.spark.processing.PySparkProcessor`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.spark.processing.PySparkProcessor "sagemaker.spark.processing.PySparkProcessor")
	- [`sagemaker.spark.processing.SparkJarProcessor`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.spark.processing.SparkJarProcessor "sagemaker.spark.processing.SparkJarProcessor")
	- [`sagemaker.processing.ProcessingInput`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingInput "sagemaker.processing.ProcessingInput")
	- [`sagemaker.processing.ProcessingOutput`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingOutput "sagemaker.processing.ProcessingOutput")
	- [`sagemaker.processing.ProcessingJob`](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html#sagemaker.processing.ProcessingJob "sagemaker.processing.ProcessingJob")

- **Processing** documentation: [reference](https://sagemaker.readthedocs.io/en/stable/api/training/processing.html)
- AWS Process Data [link](https://docs.aws.amazon.com/sagemaker/latest/dg/processing-job.html)
- `CreateProcessJob` API [link](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_CreateProcessingJob.html)
- **Bring Your Own** Processing **Container** [link](https://docs.aws.amazon.com/sagemaker/latest/dg/build-your-own-processing-container.html)
- *code source*: [SageMaker Process code example](https://github.com/aws/amazon-sagemaker-examples/tree/main/sagemaker_processing)
- *code package link*: 

