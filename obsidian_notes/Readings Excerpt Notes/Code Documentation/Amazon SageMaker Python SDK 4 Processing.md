---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
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

# SageMaker Processing

You can use **Amazon SageMaker Processing** with “Processors” to perform data processing tasks such as *data pre- and post-processing*, *feature engineering*, *data validation*, and *model evaluation*

- [Amazon SageMaker Processing](https://sagemaker.readthedocs.io/en/stable/amazon_sagemaker_processing.html)
    - [Background](https://sagemaker.readthedocs.io/en/stable/amazon_sagemaker_processing.html#background)
    - [Setup](https://sagemaker.readthedocs.io/en/stable/amazon_sagemaker_processing.html#setup)
    - [Data Pre-Processing and Model Evaluation with scikit-learn](https://sagemaker.readthedocs.io/en/stable/amazon_sagemaker_processing.html#data-pre-processing-and-model-evaluation-with-scikit-learn)
    - [Data Processing with Spark](https://sagemaker.readthedocs.io/en/stable/amazon_sagemaker_processing.html#data-processing-with-spark)
    - [Learn More](https://sagemaker.readthedocs.io/en/stable/amazon_sagemaker_processing.html#learn-more)

## Background

>[!quote]
>Amazon SageMaker lets developers and data scientists train and deploy machine learning models. With **Amazon SageMaker Processing**, you can run processing jobs for data processing steps in your machine learning pipeline. *Processing jobs* accept data from *Amazon S3* as *input* and store data into *Amazon S3* as *output*.
>![[amazon_sagemaker_processing_image1.png]]

## Setup

The fastest way to get started with Amazon SageMaker Processing is by running a **Jupyter notebook**.

## Data Pre-Processing and Model Evaluation with scikit-learn

> [!example]
> You can run a scikit-learn script to do data processing on SageMaker using the [`sagemaker.sklearn.processing.SKLearnProcessor`](https://sagemaker.readthedocs.io/en/stable/frameworks/sklearn/sagemaker.sklearn.html#sagemaker.sklearn.processing.SKLearnProcessor "sagemaker.sklearn.processing.SKLearnProcessor") class.
> 
> You first create a `SKLearnProcessor`
> ```python
> from sagemaker.sklearn.processing import SKLearnProcessor
> 
> sklearn_processor = SKLearnProcessor(
>     framework_version="0.20.0",
>     role="[Your SageMaker-compatible IAM role]",
>     instance_type="ml.m5.xlarge",
>     instance_count=1,
> )
> ```
> Then you can run a scikit-learn script `preprocessing.py` in a processing job.
> 
> ```python
> from sagemaker.processing import ProcessingInput, ProcessingOutput
> 
> sklearn_processor.run(
>     code="preprocessing.py",
>     inputs=[
>         ProcessingInput(source="s3://your-bucket/path/to/your/data", destination="/opt/ml/processing/input"),
>     ],
>     outputs=[
>         ProcessingOutput(output_name="train_data", source="/opt/ml/processing/train"),
>         ProcessingOutput(output_name="test_data", source="/opt/ml/processing/test"),
>     ],
>     arguments=["--train-test-split-ratio", "0.2"],
> )
> 
> preprocessing_job_description = sklearn_processor.jobs[-1].describe()
> ```
> In this example, our script 
> - *takes one input from S3* and one *command-line argument*, 
> - *processes the data*, then 
> - *splits the data into two datasets for output*. 
> - When the job is finished, we can *retrieve the output from S3*.


## Bring Your Own Processing Container

>[!info]
> - You can provide Amazon SageMaker Processing with a **Docker image** that has your own *code and dependencies* to run your data processing, feature engineering, and model evaluation workloads.
> 
> - Example on *Dockerfile* in [[SageMaker SDK Training Script Dockerfile]]
> - Example code on build Docker Image and pull to ECR [[SageMaker SDK Training Script Push Dockerfile to ECR]]
> - For an example of a *processing script*, see [Get started with SageMaker Processing](https://github.com/aws/amazon-sagemaker-examples/blob/main/sagemaker_processing/basic_sagemaker_data_processing/basic_sagemaker_processing.ipynb).
> -- [link](https://docs.aws.amazon.com/sagemaker/latest/dg/build-your-own-processing-container.html) 

### How Amazon SageMaker Processing Runs Your Processing Container Image



### How Amazon SageMaker Processing Configures Input and Output For Your Processing Container

- When you create a processing job using the `CreateProcessingJob` operation, you can specify **multiple `ProcessingInput` and `ProcessingOutput`. values**.

>[!important]
> - You use the **`ProcessingInput` parameter** to specify an Amazon Simple Storage Service (Amazon S3) URI to download data from, and a path in your processing container to download the data to.
> - The **`ProcessingOutput` parameter** configures a path in your processing container from which to upload data, and where in Amazon S3 to upload that data to. 
> - For both `ProcessingInput` and `ProcessingOutput`, the **path in the processing container** must begin with **`/opt/ml/processing/` **.


### Run Your Processing Container Using the SageMaker Python SDK

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
- [Amazon SageMaker Processing Examples](https://sagemaker-examples.readthedocs.io/en/latest/sagemaker_processing/index.html)
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

