---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
  - model/training
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-26
name: Amazon SageMaker Python SDK Doc
version: 
year: 2024
---
# Introduction

>[!info]
> To train a model by using the SageMaker Python SDK, you:
> 
> 1. Prepare a training script
>     
> 2. Create an estimator
>     
> 3. Call the `fit` method of the estimator
>     
> 
> After you train a model, you can save it, and then serve the model as an endpoint to get real-time inferences or get inferences for an entire dataset by using batch transform.
> -- [link](https://sagemaker.readthedocs.io/en/stable/overview.html#train-a-model-with-the-sagemaker-python-sdk)

## Prepare a Training Script

- **Environment Variables** for SageMaker include
  
	- `SM_MODEL_DIR`: A string that represents the path where the training job **writes the model artifacts to**. After training, artifacts in this directory are *uploaded to S3* for model hosting.
    
	- `SM_NUM_GPUS`: An integer representing the *number of GPUs* available to the host.
    
	- `SM_CHANNEL_XXXX`: A string that represents the path to the directory that contains **the input data** for the *specified channel*. For example, if you specify two input channels in the MXNet estimator’s `fit` call, named *‘train’* and *‘test’,* the environment variables `SM_CHANNEL_TRAIN` and `SM_CHANNEL_TEST` are set.
    
	- `SM_HPS`: A json dump of the *hyperparameters* preserving json types (boolean, integer, etc.)
	  
	- For the exhaustive list of available environment variables, see the [SageMaker Containers documentation](https://github.com/aws/sagemaker-containers#list-of-provided-environment-variables-by-sagemaker-containers). Environment variables can be retrieved using `os.environ['SM_XXX']`
	  
- Training script is a python script that can be used as the main script for training process. It is similar to normal *python script*. 

>[!important] 
>The tasks for a typical training script:
> - **loads** data from input channel;
> - **configure** training with hyperparameters;
> - **train** a model
> - **save** a model to `model_dir` so that it can be deployed to endpoint

- Hyperparameters are treated as *argument* to the script. 
	- We can retrieve hyperparameters with an `argparse.ArgumentParser` instance.
	  
	- Note that SageMaker doesn’t support `argparse` actions. If you want to use, for example, boolean hyperparameters, you need to specify `type` as `bool` in your script and provide an explicit `True` or `False` value for this hyperparameter when you create your estimator.

## Using Estimators

### Use Pre-built Container

The following example uses a pre-built `MXNet` container

```python
from sagemaker.mxnet import MXNet

# Configure an MXNet Estimator (no training happens yet)
mxnet_estimator = MXNet('train.py',
                        role='SageMakerRole',
                        instance_type='ml.p2.xlarge',
                        instance_count=1,
                        framework_version='1.2.1')

# Starts a SageMaker training job and waits until completion.
mxnet_estimator.fit('s3://my_bucket/my_training_data/')

# Deploys the model that was generated by fit() to a SageMaker endpoint
mxnet_predictor = mxnet_estimator.deploy(initial_instance_count=1, instance_type='ml.p2.xlarge')

# Serializes data and makes a prediction request to the SageMaker endpoint
response = mxnet_predictor.predict(data)

# Tears down the SageMaker endpoint and endpoint configuration
mxnet_predictor.delete_endpoint()

# Deletes the SageMaker model
mxnet_predictor.delete_model()
```

Note that the example above will eventually delete both the SageMaker endpoint and endpoint configuration through `delete_endpoint()`.

### Training Metrics

- The **SageMaker Python SDK** allows you to specify a *name* and a *regular expression* for *metrics* you want to track for training. A regular expression (regex) matches what is in the training algorithm logs, like a search function. Here is an example of how to define metrics:

```python
# Configure an BYO Estimator with metric definitions (no training happens yet)
byo_estimator = Estimator(image_uri=image_uri,
                          role='SageMakerRole', instance_count=1,
                          instance_type='ml.c4.xlarge',
                          sagemaker_session=sagemaker_session,
                          metric_definitions=[{'Name': 'test:msd', 'Regex': '#quality_metric: host=\S+, test msd <loss>=(\S+)'},
                                              {'Name': 'test:ssd', 'Regex': '#quality_metric: host=\S+, test ssd <loss>=(\S+)'}])
```

### BYO Docker Containers with SageMaker Estimators

- To use a Docker image that you created and use the SageMaker SDK for training, the easiest way is to use the dedicated `Estimator` class. You can create an instance of the `Estimator` class with desired Docker image and use it as described in previous sections

## Using Models Trained Outside of Amazon SageMaker

- You can use models that you train outside of Amazon SageMaker, and model packages that you create or subscribe to in the AWS Marketplace to get inferences.

### BYO Model

>[!info]
> - You can create an *endpoint* from an existing model that you trained outside of Amazon Sagemaker. That is, you can bring your own model:
> 
> 	- First, package the files for the trained model into a `.tar.gz` file, and *upload the archive to S3*.
> 	  
> 	- Next, *create a `Model` object* that corresponds to the framework that you are using: [MXNetModel](https://sagemaker.readthedocs.io/en/stable/sagemaker.mxnet.html#mxnet-model) or [TensorFlowModel](https://sagemaker.readthedocs.io/en/stable/sagemaker.tensorflow.html#tensorflow-model).
> 	  
> 	- After that, *invoke the `deploy()` method* on the `Model`
> 	- This returns a `predictor` the same way an `Estimator` does when `deploy()` is called. You can now get inferences just like with any other model deployed on Amazon SageMaker.

>[!example]  
>  ```python
> from sagemaker.mxnet.model import MXNetModel
> 
> sagemaker_model = MXNetModel(model_data='s3://path/to/model.tar.gz',
>                              role='arn:aws:iam::accid:sagemaker-role',
>                              entry_point='entry_point.py')
> # deploy to endpoint
> predictor = sagemaker_model.deploy(initial_instance_count=1,
>                              instance_type='ml.m4.xlarge')
> ```



----------
##  Citations


- [[Fine-Tuning for Sequence or Sequence-Pair Classification via BERT]]
- Amazon SageMaker Python SDK Documentation [link](https://sagemaker.readthedocs.io/en/stable/index.html)
- [Using the SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/overview.html)
- [Amazon SageMaker Distributed Training Examples](https://sagemaker-examples.readthedocs.io/en/latest/training/distributed_training/index.html)
- [How to run a distributed training job with the SageMaker distributed data parallelism library](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-modify-sdp.html)
- `Estimators` class API [link](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html)
- A full example is available in the [Amazon SageMaker examples repository](https://github.com/awslabs/amazon-sagemaker-examples/tree/master/advanced_functionality/mxnet_mnist_byom).
- *code source*: [https://github.com/aws/sagemaker-python-sdk](https://github.com/aws/sagemaker-python-sdk)
- *code package link*: 



