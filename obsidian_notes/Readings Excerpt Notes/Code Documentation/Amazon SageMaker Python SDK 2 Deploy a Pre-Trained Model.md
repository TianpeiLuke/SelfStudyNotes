---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
  - model/deploy_production
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-27
name: Amazon SageMaker Python SDK Doc
version: 
year: 2024
---

## Deploy a Pre-Trained Model Directly to a SageMaker Endpoint

- You can deploy a built-in algorithm or pre-trained model to a *SageMaker endpoint* in just a few lines of code using the *SageMaker Python SDK*.

- First, find the *model ID* for the model of your choice in the [Built-in Algorithms with pre-trained Model Table](https://sagemaker.readthedocs.io/en/stable/doc_utils/pretrainedmodels.html).

### Low-code deployment with the JumpStartModel class

- Using the *model ID*, define your model as a **JumpStart model**. [^1] Use the `deploy` method to automatically deploy your model for inference.

>[!example]
> ```python
> from sagemaker.jumpstart.model import JumpStartModel
> 
> model_id = "huggingface-text2text-flan-t5-xl"
> my_model = JumpStartModel(model_id=model_id)
> predictor = my_model.deploy()
> ```

- You can then run *inference* with the deployed model using the `predict` method.

>[!example]
> ```python
>question = "What is Southern California often abbreviated as?"
>response = predictor.predict(question)
>print(response)
> ```

- You can optionally include specific *model versions* or *instance types* when deploying a pretrained model using the `JumpStartModel` class. All JumpStart models have a default instance type. 

- See all supported instance types for a given **JumpStart** model with the `instance_types.retrieve()` method.

>[!example] 
>Retrieve the default deployment instance type using the following code:
> ```python
>from sagemaker import instance_types
> 
> instance_type = instance_types.retrieve_default(
>     model_id=model_id,
>     model_version=model_version,
>     scope="inference")
> print(instance_type)
> ```

- To check *valid data input and output formats* for inference, you can use the `retrieve_options()` method from the `Serializers` and `Deserializers` classes.

>[!example] 
> ```python
>print(sagemaker.serializers.retrieve_options(model_id=model_id, model_version=model_version))
>print(sagemaker.deserializers.retrieve_options(model_id=model_id, model_version=model_version))
> ```

- Similarly, you can use the `retrieve_options()` method to check the supported *content* and *accept types* for a model.

>[!example] 
> ```python
>print(sagemaker.content_types.retrieve_options(model_id=model_id, model_version=model_version))
>print(sagemaker.accept_types.retrieve_options(model_id=model_id, model_version=model_version))
> ```

### Deploy a pre-trained model using the SageMaker Model class

- In this section, you learn how to take a pre-trained model and deploy it *directly* to a **SageMaker Endpoint** and understand what happens behind the scenes if you deployed your model as a `JumpStartModel`. The following assumes familiarity with [SageMaker models](https://sagemaker.readthedocs.io/en/stable/api/inference/model.html) and their deploy functions.

	- To begin, select a `model_id` and `version` from the pre-trained models table, as well as a *model scope* of either “inference” or “training”. Use the *utility functions* to retrieve the **URI** of each of the three components you need to continue.
	  
	- Next, pass the *URIs* and *other key parameters* as part of a new **SageMaker Model class**. The `entry_point` is a *JumpStart script* named `inference.py`. SageMaker handles the implementation of this script. You must use this value for model inference to be successful. For more information about the **Model class** and its parameters, see [Model](https://sagemaker.readthedocs.io/en/stable/api/inference/model.html).
	  
	- Save the *output* from deploying the model to a variable named `predictor`. The **predictor** is used to make queries on the *SageMaker endpoint*. Currently, the generic `model.deploy` call requires the `predictor_cls` parameter to define the **predictor class**. Pass in the default **SageMaker Predictor class** for this parameter. Deployment may take about 5 minutes. [^2]

```python
from sagemaker import image_uris, model_uris, script_uris

model_id, model_version = "tensorflow-tc-bert-en-cased-L-12-H-768-A-12-2", "1.0.0"
instance_type, instance_count = "ml.m5.xlarge", 1

# Retrieve the URIs of the JumpStart resources
base_model_uri = model_uris.retrieve(
    model_id=model_id, model_version=model_version, model_scope="inference"
)
script_uri = script_uris.retrieve(
    model_id=model_id, model_version=model_version, script_scope="inference"
)
image_uri = image_uris.retrieve(
    region=None,
    framework=None,
    image_scope="inference",
    model_id=model_id,
    model_version=model_version,
    instance_type=instance_type,
)
```

```python
from sagemaker.model import Model
from sagemaker.predictor import Predictor
from sagemaker.session import Session

# Create the SageMaker model instance
model = Model(
    image_uri=image_uri,
    model_data=base_model_uri,
    source_dir=script_uri,
    entry_point="inference.py",
    role=Session().get_caller_identity_arn(),
    predictor_cls=Predictor,
    enable_network_isolation=True,
)
```

```python
predictor = model.deploy(
    initial_instance_count=instance_count,
    instance_type=instance_type,
)
```




----------
##  Citations

- Amazon SageMaker Python SDK Documentation [link](https://sagemaker.readthedocs.io/en/stable/index.html)
- [Using the SageMaker Python SDK](https://sagemaker.readthedocs.io/en/stable/overview.html)
- [Amazon SageMaker Model Deploy Examples](https://sagemaker-examples.readthedocs.io/en/latest/inference/index.html)
- `Estimators` class API [link](https://sagemaker.readthedocs.io/en/stable/api/training/estimators.html)
- A full example is available in the [Amazon SageMaker examples repository](https://github.com/awslabs/amazon-sagemaker-examples/tree/master/advanced_functionality/mxnet_mnist_byom).
- Deploy Pre-built Model [link](https://sagemaker.readthedocs.io/en/stable/overview.html#use-built-in-algorithms-with-pre-trained-models-in-sagemaker-python-sdk)
- [SageMaker models](https://sagemaker.readthedocs.io/en/stable/api/inference/model.html)
- SageMaker [Model class](https://sagemaker.readthedocs.io/en/stable/api/inference/model.html).
- *code source*: [https://github.com/aws/sagemaker-python-sdk](https://github.com/aws/sagemaker-python-sdk)
- *code package link*: 


 [^1]: For more information about the `JumpStartModel` class and its parameters, see [JumpStartModel](https://sagemaker.readthedocs.io/en/stable/api/inference/model.html#sagemaker.jumpstart.model.JumpStartModel).

[^2]: Because the model and script URIs are distributed by SageMaker JumpStart, the endpoint, endpoint config and model resources will be prefixed with `sagemaker-jumpstart`. Refer to the model `Tags` to inspect the model artifacts involved in the model creation.

